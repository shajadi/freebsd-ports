# Created by: Yukihiro Nakai <nakai@FreeBSD.org>
# $FreeBSD$

PORTNAME=	epplets
PORTVERSION=	0.14
CATEGORIES=	x11-wm
MASTER_SITES=	SF/enlightenment/${PORTNAME}/${PORTVERSION}

MAINTAINER=	gahr@FreeBSD.org
COMMENT=	A collection of Enlightenment dock applications

BUILD_DEPENDS=	e16:${PORTSDIR}/x11-wm/e16
LIB_DEPENDS=	cdaudio.1:${PORTSDIR}/audio/libcdaudio
RUN_DEPENDS=	e16:${PORTSDIR}/x11-wm/e16 \
		import:${PORTSDIR}/graphics/ImageMagick

USE_XORG=	xext
USE_GNOME=	esound
USE_GL=		glut
USES=		gmake pkgconfig
USE_LDCONFIG=	yes
CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib
GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--disable-auto-respawn

NO_STAGE=	yes
post-patch:
	@${REINPLACE_CMD} -e 's|<machine/soundcard\.h>|<sys/soundcard.h>|g' \
		${WRKSRC}/epplets/Emix.c
	@${REINPLACE_CMD} -e 's|<malloc\.h>|<stdlib.h>|g' \
		${WRKSRC}/epplets/mbox.c

.include <bsd.port.mk>
