# $FreeBSD$

PORTNAME=	trytond_carrier_percentage
PORTVERSION=	2.4.1
CATEGORIES=	finance python
MASTER_SITES=	http://downloads.tryton.org/${PORTVERSION:R}/

MAINTAINER=	matthias@petermann.it
COMMENT=	Tryton Application Platform (Carrier Percentage Module)

LICENSE=	GPLv3

RUN_DEPENDS=	trytond>=2.4.0:${PORTSDIR}/finance/trytond \
		trytond_carrier>=2.4.1:${PORTSDIR}/finance/trytond_carrier \
		trytond_currency>=2.4.0:${PORTSDIR}/finance/trytond_currency

CONFLICTS=	trytond_carrier_percentage-2.[68].*

USE_PYTHON=	yes
USE_PYDISTUTILS=easy_install

NO_STAGE=	yes
.include <bsd.port.mk>
