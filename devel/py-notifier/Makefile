# Created by: Li-Wen Hsu <lwhsu@lwhsu.org>
# $FreeBSD$

PORTNAME=	notifier
PORTVERSION=	0.5.8
CATEGORIES=	devel python
MASTER_SITES=	http://www.bitkipper.net/bytes/pynotifier/source/
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}
DISTNAME=	py${PORTNAME}_${PORTVERSION}-1

MAINTAINER=	lwhsu@FreeBSD.org
COMMENT=	A generic notifier/event scheduler abstraction

USE_PYTHON=	yes
USE_PYDISTUTILS=	yes
PYDISTUTILS_PKGNAME=	pynotifier

EXAMPLESDIR=	${PREFIX}/share/examples/py-${PORTNAME}

WRKSRC=		${WRKDIR}/py${PORTNAME}-${PORTVERSION}

.if !defined(NOPORTEXAMPLES)
NO_STAGE=	yes
post-install:
	${MKDIR} ${EXAMPLESDIR}
	${CP} ${WRKSRC}/examples/*.py ${EXAMPLESDIR}
.endif

.include <bsd.port.mk>
