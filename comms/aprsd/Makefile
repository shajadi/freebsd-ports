# Created by: db
# $FreeBSD$

PORTNAME=	aprsd
PORTVERSION=	2.2.515
CATEGORIES=	comms hamradio
MASTER_SITES=	SF/${PORTNAME}/${PORTNAME}/2.2.5-15
DISTNAME=	aprsd-2.2.5-15

MAINTAINER=	db@FreeBSD.org
COMMENT=	Server daemon providing Internet access to APRS packet data

GNU_CONFIGURE=	yes
SUB_FILES=	pkg-message

NO_STAGE=	yes
.include <bsd.port.pre.mk>

post-patch:
	@${REINPLACE_CMD} -e 's|%%CONFPATH%%|${PREFIX}/etc/aprsd/|' \
 	    -e 's|%%LOGPATH%%|/var/log/aprsd/|' \
		    ${WRKSRC}/src/aprsd.cpp
	@${REINPLACE_CMD} -e 's|%%LOGPATH%%|/var/log/aprsd/|' \
	    ${WRKSRC}/src/utils.cpp

post-configure:
	@${REINPLACE_CMD} -e 's|-lpthread|${PTHREAD_LIBS}|' \
	    ${WRKSRC}/Makefile

pre-install:
	@${MKDIR} ${PREFIX}/etc/aprsd
	@${MKDIR} "/var/log/aprsd"
	@${SETENV} "PKG_PREFIX=${PREFIX}" ${SH} ${PKGINSTALL} ${PKGNAME} PRE-INSTALL

post-install:
	@cd ${WRKSRC}/admin
.for	f in INIT.TNC RESTORE.TNC aprsd.conf welcome.txt user.deny
	@${INSTALL_DATA} ${WRKSRC}/admin/$f ${PREFIX}/etc/aprsd/$f.samp
.endfor
	${MKDIR} ${EXAMPLESDIR}
.for	f in chkaprsd udp_example
	@${INSTALL_DATA} ${WRKSRC}/admin/$f ${EXAMPLESDIR}
.endfor
	@${INSTALL_SCRIPT}	${FILESDIR}/aprsd ${LOCALBASE}/etc/rc.d
.if !defined(NOPORTDOCS)
	@${MKDIR} ${DOCSDIR}
	@${CP} ${WRKSRC}/doc/*.html ${DOCSDIR}
	@${ECHO}
	@${ECHO} docs are in ${PREFIX}/share/doc/aprsd
	@${ECHO}
.endif
	@${CAT} ${PKGMESSAGE}

.include <bsd.port.post.mk>
