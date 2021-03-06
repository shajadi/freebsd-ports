# Created by: Maxim Ignatenko
# $FreeBSD$

PORTNAME=	vsftpd-ext
PORTVERSION=	${UPSTREAMVERSION}.${EXTVERSION}
PORTREVISION=	1
CATEGORIES=	ftp ipv6
MASTER_SITES=	http://vsftpd.devnet.ru/files/${UPSTREAMVERSION}/ext.${EXTVERSION}/
PKGNAMESUFFIX?=	${SSL_SUFFIX}${PKGNAMESUFFIX2}
DISTNAME=	vsFTPd-${UPSTREAMVERSION}-ext${EXTVERSION}
EXTRACT_SUFX=	.tgz

MAINTAINER=	gelraen.ua@gmail.com
COMMENT=	FTP daemon that aims to be "very secure". Extended build

CONFLICTS=	vsftpd-2* vsftpd${SSL_SUFFIX}${PKGNAMESUFFIX2}-2*

UPSTREAMVERSION=	2.3.5
EXTVERSION=	1

WRKSRC=	${WRKDIR}/vsFTPd-${UPSTREAMVERSION}-ext.${EXTVERSION}
ALL_TARGET=	vsftpd
MAN5=		vsftpd.conf.5
MAN8=		vsftpd.8
DOCFILES=	AUDIT BENCHMARKS BUGS Changelog FAQ INSTALL LICENSE \
		README README.security README.ssl REFS REWARD \
		SIZE SPEED TODO TUNING

OPTIONS_DEFINE=	RC_SCRIPT SSL DOCS
OPTIONS_DEFAULTL=	RC_SCRIPT
RC_SCRIPT_DESC=	install RC_SCRIPT

NO_STAGE=	yes
.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MRC_SCRIPT}
USE_RC_SUBR=	vsftpd
.endif

.if ${PORT_OPTIONS:MSSL}
USE_OPENSSL=	yes
SSL_SUFFIX=	-ssl
CFLAGS+=	-I${OPENSSLINC}
LDFLAGS+=	-L${OPENSSLLIB}
.endif

do-configure:
	${REINPLACE_CMD} -e "s|/etc/vsftpd|${PREFIX}/etc|" \
		${WRKSRC}/builddefs.h
	${REINPLACE_CMD} \
		-e '/^CC/s/=/?=/' \
		-e '/^CFLAGS/{s/=/+=/;s/-O[0-9]//;}' \
		-e '/^LIBS/s|=.*|= `./vsf_findlibs.sh`|' \
		-e '/^LINK/s/=.*/=/' \
		${WRKSRC}/Makefile
	${REINPLACE_CMD} -e '/-lutil/d' ${WRKSRC}/vsf_findlibs.sh
	${REINPLACE_CMD} -e \
		"s|#undef VSF_BUILD_TCPWRAPPERS|#define VSF_BUILD_TCPWRAPPERS 1|" \
		${WRKSRC}/builddefs.h
	@${ECHO_CMD} "secure_chroot_dir=${PREFIX}/share/vsftpd/empty" >> \
		${WRKSRC}/vsftpd.conf
	@${ECHO_CMD} >>${WRKSRC}/vsftpd.conf ""
	@${ECHO_CMD} >>${WRKSRC}/vsftpd.conf \
		"# If using vsftpd in standalone mode, uncomment the next two lines:"
	@${ECHO_CMD} >>${WRKSRC}/vsftpd.conf "# listen=YES"
	@${ECHO_CMD} >>${WRKSRC}/vsftpd.conf "# background=YES"
	${REINPLACE_CMD} -e "s|/etc/v|${PREFIX}/etc/v|" \
		-e 's|delay_failed_logins|delay_failed_login|' \
		-e 's|delay_successful_logins|delay_successful_login|' \
		${WRKSRC}/vsftpd.8 ${WRKSRC}/vsftpd.conf.5 ${WRKSRC}/tunables.c
.if ${PORT_OPTIONS:MSSL}
	${REINPLACE_CMD} -e \
		"s|#undef VSF_BUILD_SSL|#define VSF_BUILD_SSL 1|" \
		${WRKSRC}/builddefs.h
.endif

pre-install:
	${SETENV} PKG_PREFIX=${PREFIX} ${SH} ${PKGINSTALL} ${PKGNAME} PRE-INSTALL

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/vsftpd ${PREFIX}/libexec/
	${INSTALL_DATA} ${WRKSRC}/vsftpd.conf ${PREFIX}/etc/vsftpd.conf.dist
	${INSTALL} -d ${PREFIX}/share/vsftpd/empty
	@if [ ! -e ${PREFIX}/etc/vsftpd.conf ]; then \
		${INSTALL_DATA} ${WRKSRC}/vsftpd.conf ${PREFIX}/etc/ ; \
	fi
	${MKDIR} ${PREFIX}/share/vsftpd/empty
	@for i in ${MAN8} ; do \
		${INSTALL_MAN} -m 644 ${WRKSRC}/$${i} ${MANPREFIX}/man/man8/ ; \
		done
	@for i in ${MAN5} ; do \
		${INSTALL_MAN} -m 644 ${WRKSRC}/$${i} ${MANPREFIX}/man/man5/ ; \
		done
	${MKDIR} /var/ftp
.if ${PORT_OPTIONS:MDOCS}
	${MKDIR} ${DOCSDIR}
.for i in ${DOCFILES}
	${INSTALL_DATA} -m 644 ${WRKSRC}/${i} ${DOCSDIR}
.endfor
.for i in EXAMPLE SECURITY
	${MKDIR} ${DOCSDIR}/${i}
	${CP} -p -R -L ${WRKSRC}/${i}/./ ${DOCSDIR}/${i}/
	${CHMOD} -R -L a+rX,go-w ${DOCSDIR}/${i}/
.endfor
.endif

.include <bsd.port.mk>
