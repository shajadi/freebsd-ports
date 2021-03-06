# Created by: Cyril Guibourg
# $FreeBSD$

PORTNAME=	milter-greylist
PORTVERSION=	4.3.9
CATEGORIES=	mail
MASTER_SITES=	ftp://ftp.espci.fr/pub/milter-greylist/ \
		http://fossies.org/unix/privat/
PKGNAMESUFFIX=	-devel
EXTRACT_SUFX=	.tgz

MAINTAINER=	m.tsatsenko@gmail.com
COMMENT=	Easy-to-use greylist milter for sendmail and postfix (development)

LICENSE=	BSD

CONFLICTS=	milter-greylist-4.2.*
PKGMESSAGE=	${WRKDIR}/pkg-message

MAKE_JOBS_UNSAFE=	yes

OPTIONS_DEFINE=	LIBSPF2 GEOIP CURL LDAP POSTFIX
LIBSPF2_DESC=	Include SPF support
POSTFIX_DESC=	Use Postfix instead of Sendmail

NO_STAGE=	yes
.include <bsd.port.pre.mk>

##
# Use the following quirks to choose which sendmail to use (ports or system):
#
#   WITH_SENDMAIL_BASE=yes
# or
#   WITH_SENDMAIL_PORT=yes
#
# If unspecified, check for an up-to-date system version but give an
# installed port preference over it.
##

MAN5=		greylist.conf.5
MAN8=		milter-greylist.8

##
# If you have a reentrant resolver (starting with RELENG_5_2) you can use SPF
##
.if ${PORT_OPTIONS:MLIBSPF2}
BUILD_DEPENDS+=	libspf2>=1.2.5:${PORTSDIR}/mail/libspf2
CONFIGURE_ARGS+=	--with-libspf2=${LOCALBASE}
.endif
.if ${PORT_OPTIONS:MGEOIP}
BUILD_DEPENDS+=	GeoIP>=1.4.4:${PORTSDIR}/net/GeoIP
CONFIGURE_ARGS+=	--with-libGeoIP=${LOCALBASE}
.endif
.if ${PORT_OPTIONS:MCURL}
BUILD_DEPENDS+=	curl>=7.18:${PORTSDIR}/ftp/curl
CONFIGURE_ARGS+=	--with-libcurl=${LOCALBASE}
.endif
.if ${PORT_OPTIONS:MLDAP}
USE_OPENLDAP=yes
CONFIGURE_ARGS+=	--with-openldap
.endif
.if ${PORT_OPTIONS:MPOSTFIX}
CONFIGURE_ARGS+=	--enable-postfix
.else
LDFLAGS+=	${SENDMAIL_LDFLAGS}
LIBS+=		${SENDMAIL_LDADD}
.endif
RUN_DEPENDS+=	${BUILD_DEPENDS}

CFLAGS+=	${PTHREAD_CFLAGS}
LIBS+=		${PTHREAD_LIBS}

GNU_CONFIGURE=	yes
CONFIGURE_ARGS+=	--with-user=mailnull --with-libmilter=${MILTERBASE} \
			--enable-dnsrbl --with-thread-safe-resolver
CONFIGURE_ENV+=	LIBS="${LIBS} "

ALL_TARGET=	milter-greylist
SUB_FILES+=	pkg-message

USE_RC_SUBR=	milter-greylist

do-install:
	@${MKDIR} ${PREFIX}/etc/mail
	@${INSTALL_MAN} ${WRKSRC}/greylist.conf.5 ${PREFIX}/man/man5
	@${INSTALL_MAN} ${WRKSRC}/milter-greylist.8 ${PREFIX}/man/man8
	@${INSTALL_PROGRAM} ${WRKSRC}/milter-greylist ${PREFIX}/libexec
	@${INSTALL_DATA} ${WRKSRC}/greylist.conf \
			${PREFIX}/etc/mail/greylist.conf.sample

post-install:
	@${MKDIR} /var/milter-greylist
	@${CHOWN} -R mailnull /var/milter-greylist
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
	@${INSTALL_DATA} ${WRKSRC}/README ${DOCSDIR}
.endif
.if ${PORT_OPTIONS:MEXAMPLES}
	@${MKDIR} ${EXAMPLESDIR}
	@${INSTALL_DATA} ${WRKSRC}/greylist.conf ${EXAMPLESDIR}
.endif
	@${TEST} -f /var/db/milter-greylist/greylist.db && ( \
		${ECHO} "************************************************************"; \
		${ECHO} "************************************************************"; \
		${ECHO} "**                                                        **"; \
		${ECHO} "**                        WARNING                         **"; \
		${ECHO} "**                                                        **"; \
		${ECHO} "** The default dump file location has changed.            **"; \
		${ECHO} "** Please move greylist.db from /var/db/milter-greylist/  **"; \
		${ECHO} "** to /var/milter-greylist/ and update your greylist.conf **"; \
		${ECHO} "** accordingly.                                           **"; \
		${ECHO} "**                                                        **"; \
		${ECHO} "************************************************************"; \
		${ECHO} "************************************************************"; \
	) || ${TRUE}
	@${CAT} ${PKGMESSAGE}

.include "${PORTSDIR}/mail/sendmail/bsd.milter.mk"

.include <bsd.port.post.mk>
