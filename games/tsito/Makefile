# Created by: Kuang-che Wu <kcwu@csie.org>
# $FreeBSD$

PORTNAME=	tsito
PORTVERSION=	0.8.4
CATEGORIES=	games
MASTER_SITES=	SF/xiangqi-engine/xiangqi-engine/${PORTNAME}-${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	A Chinese chess (Xiangqi) program

HAS_CONFIGURE=	yes
CONFIGURE_ENV=	LIBS="-lcompat"
CONFIGURE_ARGS=	--prefix="${PREFIX}"

MAN1=		tsito.1

NO_STAGE=	yes
.include <bsd.port.mk>
