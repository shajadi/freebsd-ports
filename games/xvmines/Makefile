# Created by: Andrey Zakhvatov
# $FreeBSD$

PORTNAME=	xvmines
PORTVERSION=	1.0
PORTREVISION=	2
CATEGORIES=	games
MASTER_SITES=	XCONTRIB/../R5contrib
EXTRACT_SUFX=	.tar.Z

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Simple minesweeper game for X Window System

LIB_DEPENDS=	xview:${PORTSDIR}/x11-toolkits/xview

OPTIONS_DEFINE=	DOCS

USES=		imake
USE_XORG=	x11

MANCOMPRESSED=	no
MAN6=		xvmines.6
PORTDOCS=	Copyright
PLIST_FILES=	bin/xvmines

NO_STAGE=	yes
.include <bsd.port.options.mk>

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/xvmines ${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/xvmines.man ${MAN6PREFIX}/man/man6/xvmines.6
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/Copyright ${DOCSDIR}
.endif

.include <bsd.port.mk>
