# Created by: John Hixson <john@ixsystems.com>
# $FreeBSD$

PORTNAME=	django-json-rpc
PORTVERSION=	0.6.2
PORTREVISION=	1
CATEGORIES=	www python
MASTER_SITES=	http://wiki.pcbsd.org/ports/
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	john@ixsystems.com
COMMENT=	A simple JSON-RPC implementation for Django

RUN_DEPENDS=	${PYTHON_SITELIBDIR}/django/bin/django-admin.py:${PORTSDIR}/www/py-django

LICENSE=	MIT

USE_BZIP2=	yes
USE_PYTHON=	yes
USE_PYDISTUTILS=	easy_install

NO_STAGE=	yes
.include <bsd.port.mk>
