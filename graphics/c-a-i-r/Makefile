# Created by: buganini@gmail.com
# $FreeBSD$

PORTNAME=	c-a-i-r
PORTVERSION=	2.19
CATEGORIES=	graphics
MASTER_SITES=	SF/${PORTNAME}/${PORTNAME}/CAIR%20v${PORTVERSION}
DISTNAME=	CAIR_v${PORTVERSION}

MAINTAINER=	buganini@gmail.com
COMMENT=	Content Aware Image Resizer is an implementation of seam carving

USE_ZIP=	yes
USES=		gmake
MAKE_ARGS+=	CC="${CXX}"

WRKSRC=		${WRKDIR}

PLIST_FILES=	bin/cair

NO_STAGE=	yes
do-install:
	${INSTALL_SCRIPT} ${WRKSRC}/cair ${PREFIX}/bin

.include <bsd.port.mk>
