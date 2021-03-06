# Created by: Boris Popov <bp@FreeBSD.org>
# $FreeBSD$

PORTNAME=	mars_nwe
PORTVERSION=	0.99.b20
PORTREVISION=	1
CATEGORIES=	net
MASTER_SITES=	ftp://www.compu-art.de/mars_nwe/ \
		ftp://ftp.gwdg.de/pub/linux/misc/ncpfs/mars_nwe/ \
		ftp://ftp.butya.kz/pub/mars_nwe/
DISTNAME=	mars_nwe-0.99.pl20
EXTRACT_SUFX=	.tgz

MAINTAINER=	araujo@FreeBSD.org
COMMENT=	Netware server emulator for Un*x systems

WRKSRC=		${WRKDIR}/mars_nwe

PLIST=	${WRKDIR}/PLIST.DYN

NO_STAGE=	yes
.include <bsd.port.pre.mk>

.if ${OSVERSION} > 900007
BROKEN=		fails to build with new utmpx
.endif

do-install:
	@(cd ${WRKSRC} && ./mk.li install)
	@${INSTALL_DATA} ${WRKSRC}/examples/nw.ini ${PREFIX}/etc/nwserv.conf.example
	@${ECHO} "Please read details in ${WORKDIR}/mars_nwe/doc directory."

pre-install:
	@${CP} ${PKGDIR}/pkg-plist ${WRKDIR}/PLIST.DYN
.if !defined(NOPORSDOCS)
	@${CAT} ${PKGDIR}/pkg-plist.DOC >> ${WRKDIR}/PLIST.DYN
.endif

post-install:
	@${SED} -e "/%%PREFIX%%/s##${PREFIX}#g" \
		${FILESDIR}/nwserv.sh \
		>${PREFIX}/etc/rc.d/nwserv.sh
	@${CHMOD} 0755 ${PREFIX}/etc/rc.d/nwserv.sh
.if !defined(NOPORTDOCS)
	${MKDIR} ${DOCSDIR}/
	${RM} -f ${WRKSRC}/doc/*.orig
	${INSTALL_DATA} ${WRKSRC}/doc/* ${DOCSDIR}/
.endif
	@${ECHO_MSG} "Look in ${DOCSDIR} for documentation."

.include <bsd.port.post.mk>
