# Created by: Alexander Nedotsukov <bland@FreeBSD.org>
# $FreeBSD$

PORTNAME=	sisctrl
PORTVERSION=	0.0.20051202
PORTREVISION=	7
CATEGORIES=	x11
MASTER_SITES=	http://www.winischhofer.net/sis/

MAINTAINER=	bland@FreeBSD.org
COMMENT=	Display Control Panel for XFree86/X.org SiS driver

USES=		gmake pkgconfig
USE_XORG=	x11 ice xxf86vm xinerama xv xrandr xext sm
USE_GNOME=	gtk20
GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	 --with-xv-path=${LOCALBASE}/lib
CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

PLIST_FILES=	bin/sisctrl
MAN1=		sisctrl.1x

NO_STAGE=	yes
.include <bsd.port.mk>
