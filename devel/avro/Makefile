# Created by: Veniamin Gvozdikov <vg@FreeBSD.org>
# $FreeBSD$

PORTNAME=	avro
PORTVERSION=	1.7.3
CATEGORIES=	devel
MASTER_SITES=	# none
DISTFILES=	# none
EXTRACT_ONLY=	# none

MAINTAINER=	vg@FreeBSD.org
COMMENT=	Data serialization system

NO_BUILD=	yes

OPTIONS_DEFINE=	C CPP PYTHON
C_DESC=		Install ANSI C library
CPP_DESC=	Install C++ library
PYTHON_DESC=	Install Python library

OPTIONS_DEFAULT=C CPP PYTHON

NO_STAGE=	yes
.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MC}
LIB_DEPENDS+=	avro:${PORTSDIR}/devel/avro-c
.endif

.if ${PORT_OPTIONS:MCPP}
LIB_DEPENDS+=	avrocpp:${PORTSDIR}/devel/avro-cpp
.endif

.if ${PORT_OPTIONS:MPYTHON}
BUILD_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}avro:${PORTSDIR}/devel/py-avro
.endif

do-install:	# empty

.include <bsd.port.mk>
