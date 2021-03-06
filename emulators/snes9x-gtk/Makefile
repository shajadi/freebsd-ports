# Created by: okeeblow <root@cooltrainer.org>
# $FreeBSD$

PORTNAME=	snes9x
PORTVERSION=	1.52r79
PORTREVISION=	4
CATEGORIES=	emulators
MASTER_SITES=	http://snes9x-gtk.googlecode.com/files/
PKGNAMESUFFIX=	-gtk
DISTNAME=	snes9x-1.52-src

MAINTAINER=	root@cooltrainer.org
COMMENT=	Super Nintendo Entertainment System(SNES) Emulator

LIB_DEPENDS=	png15:${PORTSDIR}/graphics/png

USE_BZIP2=	yes
USE_XORG=	x11 sm ice xext
USES=		gettext gmake perl5 desktop-file-utils pkgconfig
USE_GNOME=	gtk20 intltool libglade2 libxml2
GNU_CONFIGURE=	yes
USE_SDL=	sdl
CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib
CONFIGURE_ARGS+=	--without-alsa

WRKSRC=		${WRKDIR}/${DISTNAME}/gtk

OPTIONS_DEFINE=	DEBUG OPENGL JMA NETPLAY XV XRANDR
OPTIONS_DEFAULT=	JMA NETPLAY XV XRANDR
OPTIONS_DEFINE_i386=	ASM MMX
OPTIONS_DEFAULT_i386=	ASM
JMA_DESC=	Enable JMA archive decompression support
NETPLAY_DESC=	Enable network support
XV_DESC=	Enable XVideo output on GTK
XRANDR_DESC=	Enable XRandR support on GTK

NO_STAGE=	yes
.include <bsd.port.pre.mk>

.if ${PORT_OPTIONS:MDEBUG}
CONFIGURE_ARGS+=	--with-debug
.else
CONFIGURE_ARGS+=	--without-debug
.endif

.if ${PORT_OPTIONS:MASM}
BUILD_DEPENDS+=	nasm:${PORTSDIR}/devel/nasm
CONFIGURE_ARGS+=	--with-assembler
.else
CONFIGURE_ARGS+=	--without-assembler
.endif

.if ${PORT_OPTIONS:MMMX} && !defined(PACKAGE_BUILDING)
CONFIGURE_ARGS+=	--with-mmx
.else
CONFIGURE_ARGS+=	--without-mmx
.endif

.if ${PORT_OPTIONS:MOPENGL}
CONFIGURE_ARGS+=	--with-opengl
USE_GL=	glu
.else
CONFIGURE_ARGS+=	--without-opengl
.endif

.if ${PORT_OPTIONS:MJMA}
CONFIGURE_ARGS+=	--with-jma-decomp
.else
CONFIGURE_ARGS+=	--without-jma-decomp
.endif

.if ${PORT_OPTIONS:MNETPLAY}
CONFIGURE_ARGS+=	--with-netplay
.else
CONFIGURE_ARGS+=	--without-netplay
.endif

.if ${PORT_OPTIONS:MXV}
CONFIGURE_ARGS+=	--with-xv
USE_XORG+=	xv
.else
CONFIGURE_ARGS+=	--without-xv
.endif

.if ${PORT_OPTIONS:MXRANDR}
CONFIGURE_ARGS+=	--with-xrandr
USE_XORG+=	xrandr
.else
CONFIGURE_ARGS+=	--without-xrandr
.endif

.if exists(/usr/lib/libusbhid.a)
CONFIGURE_ARGS+=	--with-joystick
.else
CONFIGURE_ARGS+=	--without-joystick
.endif

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/${PORTNAME}${PKGNAMESUFFIX} ${PREFIX}/bin/${PORTNAME}${PKGNAMESUFFIX}
	${INSTALL_DATA} ${WRKSRC}/data/snes9x.svg ${PREFIX}/share/pixmaps
	${INSTALL_DATA} ${WRKSRC}/data/snes9x.desktop ${PREFIX}/share/applications

post-install:
	-@update-desktop-database

.include <bsd.port.post.mk>
