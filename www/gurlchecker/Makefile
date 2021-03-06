# Created by: Koop Mast <einekoai@chello.nl>
# $FreeBSD$

PORTNAME=	gurlchecker
PORTVERSION=	0.10.1
PORTREVISION=	20
CATEGORIES=	www gnome
MASTER_SITES=	http://labs.libre-entreprise.org/frs/download.php/%SUBDIR%/
MASTER_SITE_SUBDIR=	547

MAINTAINER=	clsung@FreeBSD.org
COMMENT=	Gnome program to check a page/website for broken links

LIB_DEPENDS=	gnet-2.0.0:${PORTSDIR}/net/gnet2

OPTIONS_DEFINE=	CROCO TIDY CLAMAV GNUTLS
CROCO_DESC=Library for CSS2 validation
TIDY_DESC=Library for HTML w3c validation
CLAMAV_DESC=Library for virii scan
GNUTLS_DESC=Library for HTTPS check

OPTIONS_DEFAULT=	CLAMAV GNUTLS

USE_GNOME=	gnomeprefix intlhack libgnomeui
USES=	pathfix gmake pkgconfig
GNU_CONFIGURE=	yes
CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

NO_STAGE=	yes
.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MNLS}
USES+=		gettext
PLIST_SUB+=	NLS=""
.else
PLIST_SUB+=	NLS="@comment "
.endif

.if ${PORT_OPTIONS:MCROCO}
LIB_DEPENDS+=	croco-0.6.3:${PORTSDIR}/textproc/libcroco
.else
CONFIGURE_ARGS+=	--disable-croco
.endif

.if ${PORT_OPTIONS:MTIDY}
LIB_DEPENDS+=	tidy-0.99.0:${PORTSDIR}/www/tidy-lib
.else
CONFIGURE_ARGS+=	--disable-tidy
.endif

.if ${PORT_OPTIONS:MCLAMAV}
LIB_DEPENDS+=	clamav.7:${PORTSDIR}/security/clamav
.else
CONFIGURE_ARGS+=	--disable-clamav
.endif

.if ${PORT_OPTIONS:MGNUTLS}
LIB_DEPENDS+=	gnutls.26:${PORTSDIR}/security/gnutls
.else
CONFIGURE_ARGS+=	--disable-gnutls
.endif

post-patch:
	@${REINPLACE_CMD} -e \
		'/maxratio/s|^.*||' ${WRKSRC}/src/ucclam.c
	@${REINPLACE_CMD} -e \
		'/^SUBDIRS/s|doc ui man|ui|g' ${WRKSRC}/Makefile.in
	@${REINPLACE_CMD} -e \
		's|-lresolv||g' ${WRKSRC}/src/Makefile.in
.if ! ${PORT_OPTIONS:MNLS}
	@${REINPLACE_CMD} -e \
		'/^SUBDIRS/s|po ui|ui|g' ${WRKSRC}/Makefile.in
.endif

.include <bsd.port.mk>
