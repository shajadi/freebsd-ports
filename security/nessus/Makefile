# Created by: Anders Nordby <anders@fix.no>
# $FreeBSD$

PORTNAME=	nessus
PORTVERSION=	2.2.9
PORTREVISION=	1
CATEGORIES=	security
MASTER_SITES=	ftp://ftp.nessus.org/pub/nessus/nessus-${PORTVERSION}/src/ \
		ftp://ftp.gwdg.de/pub/linux/misc/nessus/nessus-${PORTVERSION}/src/ \
		http://ftp.gwdg.de/pub/linux/misc/nessus/nessus-${PORTVERSION}/src/ \
		ftp://sunsite.cnlab-switch.ch/mirror/nessus/nessus-${PORTVERSION}/src/ \
		ftp://ftp.ayamura.org/pub/nessus/nessus-${PORTVERSION}/src/
DISTNAME=	nessus-core-${PORTVERSION}

MAINTAINER=	udo.schweigert@siemens.com
COMMENT=	Security scanner: looks for vulnerabilities in a given network

LIB_DEPENDS=	nasl.4:${PORTSDIR}/security/nessus-libnasl

DIST_SUBDIR=	nessus
WRKSRC=		${WRKDIR}/nessus-core
SUB_FILES=	pkg-deinstall
SUB_LIST=	PKGNAME=${PKGNAME}

GNU_CONFIGURE=	yes
USE_RC_SUBR=	nessusd
WANT_GNOME=	yes
.if defined(WITHOUT_NESSUS_GTK) || defined(WITHOUT_GTK)
WITHOUT_GNOME=	yes
.endif

NO_STAGE=	yes
.include <bsd.port.pre.mk>

.if ${HAVE_GNOME:Mgtk20}!=""
USE_GNOME+=	gtk20
PKGNAMESUFFIX+=	-gtk2
.elif ${HAVE_GNOME:Mgtk12}!=""
USE_GNOME+=	gtk12
PKGNAMESUFFIX+=	-gtk
.else
CONFIGURE_ARGS+=--disable-gtk
.endif

MAN1=		nessus.1 nessus-mkrand.1 nessus-mkcert-client.1 nessus-fetch.1
MAN8=		nessusd.8 nessus-adduser.8 nessus-mkcert.8 nessus-rmuser.8

post-install:
	@${SED} -e 's;\$${PREFIX};${PREFIX};' ${FILESDIR}/nessusd.conf \
		> ${PREFIX}/etc/nessus/nessusd.conf.dist
	@${SED} -e 's;\$${PREFIX};${PREFIX};' ${FILESDIR}/nessusd.rules \
		> ${PREFIX}/etc/nessus/nessusd.rules.dist
	@${CHMOD} 644 ${PREFIX}/etc/nessus/nessusd.conf.dist \
		${PREFIX}/etc/nessus/nessusd.rules.dist
	@if [ ! -f ${PREFIX}/etc/nessus/nessusd.conf ]; then \
		${CP} -p ${PREFIX}/etc/nessus/nessusd.conf.dist \
			${PREFIX}/etc/nessus/nessusd.conf; \
	fi
	@if [ ! -f ${PREFIX}/etc/nessus/nessusd.rules ]; then \
		${CP} -p ${PREFIX}/etc/nessus/nessusd.rules.dist \
			${PREFIX}/etc/nessus/nessusd.rules; \
	fi
	@${SETENV} ${SCRIPTS_ENV} ${SH} ${SCRIPTDIR}/move_nessus
.if ! exists(${PREFIX}/var/CA/serverkey.pem)
	@${ECHO} ""
	@${ECHO} "**************************************************************************"
	@${ECHO} "To create and install a new certificate, type \"make cert\""
	@${ECHO} "**************************************************************************"
	@${ECHO} ""
.endif
	@${CAT} ${PKGMESSAGE}

cert:
	@${ECHO} ""
	@${ECHO} "**************************************************************************"
	@${ECHO} "The new certificate will be saved into ${PREFIX}/var/CA/serverkey.pem"
	@${ECHO} "**************************************************************************"
	@${ECHO} ""
	${PREFIX}/sbin/nessus-mkcert

.include <bsd.port.post.mk>
