# Created by: Jim Geovedi <jim@corebsd.or.id>
# $FreeBSD$

PORTNAME=	xmlsec1
PORTVERSION=	1.2.19
CATEGORIES=	security
MASTER_SITES=	http://www.aleksey.com/xmlsec/download/ \
		ftp://ftp.aleksey.com/pub/xmlsec/releases/ \
		ftp://ftp.xmlsoft.org/xmlsec/releases/ \
		ftp://ftp.rpmfind.net/pub/XML/xmlsec/releases/

MAINTAINER=	johans@FreeBSD.org
COMMENT=	XML Security Library

BUILD_DEPENDS:=	${RUN_DEPENDS}

OPTIONS_DEFINE=	GNUTLS NSS
GNUTLS_DESC=	Enable GNUTLS support
NSS_DESC=	Enable Mozilla's NSS support

USE_OPENSSL=	yes
USE_GNOME=	gnomehack lthack libxslt
GNU_CONFIGURE=	yes
USE_LDCONFIG=	yes
USES=		pkgconfig

MAN1=	xmlsec1.1 xmlsec1-config.1
CFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib
MAKE_ENV+=	ABS_BUILDDIR=${WRKSRC} TMPFOLDER=${WRKSRC}
.if !defined(.PARSEDIR)
MAKE_ARGS+=	-EABS_BUILDDIR
.endif
USE_AUTOTOOLS=	libltdl

NO_STAGE=	yes
.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MDOCS}
PORTDOCS=	*
MAKE_ENV+=	DOCS=docs
.endif

.if ${PORT_OPTIONS:MGNUTLS}
CONFIGURE_ARGS+=	--with-gnutls="${LOCALBASE}"
LIB_DEPENDS+=		gnutls:${PORTSDIR}/security/gnutls
PLIST_SUB+=		GNUTLS=""
.else
CONFIGURE_ARGS+=	--without-gnutls
PLIST_SUB+=		GNUTLS="@comment "
.endif

.if ${PORT_OPTIONS:MNSS}
CONFIGURE_ARGS+=	--with-nss="${LOCALBASE}" --with-nspr="${LOCALBASE}"
LIB_DEPENDS+=		nss3:${PORTSDIR}/security/nss
PLIST_SUB+=		NSS=""
.else
CONFIGURE_ARGS+=	--without-nss
PLIST_SUB+=		NSS="@comment "
.endif

CONFIGURE_ARGS+=	--with-openssl="${OPENSSLBASE}"

post-patch:
	@${REINPLACE_CMD} -e 's|src apps man docs|src apps man \$${DOCS}|g' \
	    -e 's|^confexecdir =.*$$|confexecdir = \$$(sysconfdir)|g' \
	    -e 's|/tmp/\*\.log|${WRKSRC}/*.log|g' \
		${WRKSRC}/Makefile.in
	@${REINPLACE_CMD} -e '/objformat=/s|=`[^`]*`|=elf|' \
	    -e '/^XMLSEC_SHLIBSFX="/s|"[^"]*"|".so"|' \
	    -e 's|openssl_exlibs=-ldl|openssl_exlibs=|' \
	    -e 's|-ldl"|"|' \
	    -e 's,with_nspr/include,with_nspr/include/nspr ${PTHREAD_CFLAGS},' \
	    -e 's,with_nss/include,with_nss/include/nss/nss,' \
	    -e 's,with_nss/lib,with_nss/lib/nss,g' \
	    -e 's,\(CPPFLAGS="\$$NSS_CFLAGS\),\1 $$NSPR_CFLAGS,' \
	    -e '/XMLSEC_CRYPTO_LIST=.*openssl/s,$$,\; CPPFLAGS="$$CPPFLAGS $$OPENSSL_CFLAGS",' \
	    -e 's,\(-lplc4\)",\1 ${PTHREAD_LIBS}",' \
	    -e '/ test /s, == , = ,' \
		${WRKSRC}/${CONFIGURE_SCRIPT}
	@${REINPLACE_CMD} \
	    -e 's,total_time.*/ 1000),total_time*1000/CLOCKS_PER_SEC,' \
		${WRKSRC}/apps/xmlsec.c
	@${REINPLACE_CMD} -e 's,\\\\\\,\\,g' ${WRKSRC}/*.pc.in
.if ${PORT_OPTIONS:MGNUTLS}
# Don't rely on broken autodetection
	@${REINPLACE_CMD} -e '/^GNUTLS_FOUND/s/no/yes/' \
	    -e '/^GNUTLS_LIBS=/s,"","-L${LOCALBASE}/lib -lgnutls",' \
		${WRKSRC}/${CONFIGURE_SCRIPT}
.endif
.if ${PORT_OPTIONS:MNSS}
# Makeing the xmlsec1 executable multi-threaded to let load -lnss,
# when needed.
	@${REINPLACE_CMD} -e 's,^\(xmlsec1_LDADD = \)\\$$,\1 -L${LOCALBASE}/lib ${PTHREAD_LIBS}\\,' \
		${WRKSRC}/apps/Makefile.in
.endif

.include <bsd.port.mk>
