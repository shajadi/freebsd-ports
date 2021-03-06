# Created by: Andrey Zakhvatov
# $FreeBSD$

PORTNAME=	gltron
PORTVERSION=	0.70
PORTREVISION=	11
CATEGORIES=	games
MASTER_SITES=	SF/${PORTNAME}/${PORTNAME}-source/${PORTVERSION}
EXTRACT_SUFX=	-source.tar.gz

MAINTAINER=	lx@FreeBSD.org
COMMENT=	A 3D worm game for two players for X Window System

LIB_DEPENDS=	png15:${PORTSDIR}/graphics/png

USE_GL=		gl
USE_SDL=	sdl sound
USE_GMAKE=	yes
GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--disable-warn

CPPFLAGS+=	-I${LOCALBASE}/include ${PTHREAD_CFLAGS}
LDFLAGS+=	-L${LOCALBASE}/lib ${PTHREAD_LIBS}

OPTIONS_DEFINE=	SDL_NET
SDL_NET_DESC=	Network Support

DESKTOP_ENTRIES=	"GLtron" \
	"3D lightcycle game" \
	"${DATADIR}/art/default/gltron.png" \
	"gltron" \
	"Game;ArcadeGame;" \
	false

NO_STAGE=	yes
.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MSDL_NET}
USE_SDL+=	net
CONFIGURE_ARGS+=	--enable-network
.endif

post-patch:
	@${REINPLACE_CMD} -e 's|CFLAGS="-D|CFLAGS="$$CFLAGS -D|g ; \
		 s|-O$$enable_optimize||g' ${WRKSRC}/configure
	@${FIND} ${WRKSRC} -name "Makefile.in" | ${XARGS} ${REINPLACE_CMD} -e \
		's|^AM_CFLAGS|INCLUDES|g ; \
		 s|^AM_CXXFLAGS|INCLUDES|g ; \
		 s|-ansi -pedantic||g'

post-install:
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
.for file in ChangeLog README
	${INSTALL_DATA} ${WRKSRC}/${file} ${DOCSDIR}
.endfor
.endif

.include <bsd.port.mk>
