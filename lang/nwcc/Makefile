# Created by: David O'Brien (obrien@NUXI.org)
# $FreeBSD$

PORTNAME=	nwcc
PORTVERSION=	0.7.5
PORTREVISION?=	0
CATEGORIES=	lang
MASTER_SITES=	SF/${PORTNAME}/${PORTNAME}/${PORTNAME}%20${PORTVERSION}
DISTNAME=	${PORTNAME}_${PORTVERSION}

MAINTAINER=	obrien@FreeBSD.org
COMMENT=	Nils Weller's C compiler for Unix systems

ONLY_FOR_ARCHS=	i386 amd64

HAS_CONFIGURE=	yes
CONFIGURE_ARGS=	--installprefix=${PREFIX}
ALL_TARGET=

NO_STAGE=	yes
post-build:
	cd ${WRKSRC} ; ${MAKE} test

.include <bsd.port.mk>
