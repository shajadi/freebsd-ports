# Created by: Ganael Laplanche <ganael.laplanche@martymac.org>
# $FreeBSD$

PORTNAME=	openjazz
PORTVERSION=	20120819
CATEGORIES=	games
MASTER_SITES=	http://alister.eu/jazz/oj/ \
		LOCAL/martymac
DISTNAME=	OpenJazz-src-190812

MAINTAINER=	martymac@FreeBSD.org
COMMENT=	Free re-implementation of the Jazz Jackrabbit(tm) game engine

LICENSE=	GPLv2

NO_WRKSUBDIR=	yes
USE_ZIP=	yes
USE_GMAKE=	yes
ALL_TARGET=	OpenJazz
USE_XORG=	x11 xext xrandr xrender xau xdmcp
USE_SDL=	sdl

USE_DOS2UNIX=	yes
DOS2UNIX_REGEX=	.*\.(h|cpp)

CPPFLAGS+=	-I${LOCALBASE}/include `${SDL_CONFIG} --cflags` \
		-DDATAPATH=\\\"${DATADIR}/\\\" -DHOMEDIR
LDFLAGS+=	-L${LOCALBASE}/lib ${PTHREAD_LIBS} `${SDL_CONFIG} --libs`

SUB_FILES=	pkg-message

NO_STAGE=	yes
do-install:
	@${MKDIR} ${DATADIR}
	@${INSTALL_DATA} ${WRKSRC}/openjazz.000 ${DATADIR}/
	@${INSTALL_SCRIPT} ${WRKDIR}/OpenJazz ${PREFIX}/bin/openjazz
	@${CAT} ${PKGMESSAGE}

.include <bsd.port.mk>
