# Created by: trasz <trasz@pin.if.uz.zgora.pl>
# $FreeBSD$

PORTNAME=	dtcyber
PORTVERSION=	2.0b1
PORTREVISION=	2
CATEGORIES=	emulators
MASTER_SITES=	http://members.iinet.net.au/~tom-hunter/ \
		${MASTER_SITE_LOCAL}
MASTER_SITE_SUBDIR=	trasz
DISTNAME=	dtcyber20b1

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Desktop CYBER Emulator

USE_ZIP=	yes
USE_XORG=	x11
USE_DOS2UNIX=	yes
NO_WRKSUBDIR=	yes
INSTALL_TARGET=
MAKEFILE=	Makefile.x11
SUB_FILES=	pkg-message
PKGMESSAGE=	${WRKDIR}/pkg-message
PLIST_FILES=	bin/dtcyber %%EXAMPLESDIR%%/cyber.ini %%EXAMPLESDIR%%/cos.tap
PLIST_DIRS=	%%EXAMPLESDIR%%

NO_STAGE=	yes
pre-patch:
	${REINPLACE_CMD} -e 's|-lpthread|${PTHREAD_LIBS}|' ${WRKSRC}/Makefile.x11
	${REINPLACE_CMD} -e 's|CFLAGS  = -O2|CFLAGS+= |' ${WRKSRC}/Makefile.x11
	${REINPLACE_CMD} -e 's|/usr/X11R6|${LOCALBASE}|' ${WRKSRC}/Makefile.x11

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/dtcyber ${PREFIX}/bin
	@${MKDIR} ${EXAMPLESDIR}
	${INSTALL_DATA} ${WRKSRC}/cyber.ini ${EXAMPLESDIR}
	${INSTALL_DATA} ${WRKSRC}/Os/cos.tap ${EXAMPLESDIR}

post-install:
	@${CAT} ${PKGMESSAGE}

.include <bsd.port.mk>
