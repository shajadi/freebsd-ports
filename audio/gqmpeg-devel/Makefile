# Created by: Vanilla Pooh Shu <vanilla@FreeBSD.org>
# $FreeBSD$

PORTNAME=	gqmpeg
PORTVERSION=	0.91.1
PORTREVISION=	12
CATEGORIES=	audio
MASTER_SITES=	SF

MAINTAINER=	oliver@FreeBSD.org
COMMENT=	Another gtk-based MP3 frontend

LIB_DEPENDS=	png15:${PORTSDIR}/graphics/png

.if defined(WITH_MPG321)
RUN_DEPENDS+=	mpg321:${PORTSDIR}/audio/mpg321
.else
RUN_DEPENDS+=	mpg123:${PORTSDIR}/audio/mpg123
.endif

.if !defined(WITHOUT_MOD)
RUN_DEPENDS+=	xmp:${PORTSDIR}/audio/xmp
.endif

.if !defined(WITHOUT_OGG)
RUN_DEPENDS+=	ogg123:${PORTSDIR}/audio/vorbis-tools
.endif

USES=		gmake pkgconfig
NO_STAGE=	yes
LATEST_LINK=	gqmpeg-devel
USE_XORG=	xext xrender xinerama xi xrandr xcursor xcomposite xdamage x11 \
		xfixes xproto
USE_GNOME=	gtk20
GNU_CONFIGURE=  yes

CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

CONFLICTS=	gqmpeg-0.2*

MAN1=		gqmpeg.1

.include <bsd.port.pre.mk>

.if !defined(WITH_MPG321)
pre-everything::
	@${ECHO_MSG}
	@${ECHO_MSG} "If you want to use mpg321 instead of mpg123,"
	@${ECHO_MSG} "hit Ctrl-C right now and execute \"make WITH_MPG321=yes\""
	@${ECHO_MSG}
.endif

.if defined(WITH_MPG321)
post-patch:
	@${REINPLACE_CMD} -E -e \
		's/^(#define MPG123_BINARY "mpg)123"/\1321"/' \
		${WRKSRC}/src/io_mpg123.c
.endif

.include <bsd.port.post.mk>
