# Created by: Jose Alonso Cardenas Marquez <acardenas@bsd.org.pe>
# $FreeBSD$

PORTNAME=	py2play
PORTVERSION=	0.1.10
CATEGORIES=	net-p2p python
MASTER_SITES=	http://download.gna.org/slune/
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}
DISTNAME=	Py2Play-${PORTVERSION}

MAINTAINER=	acm@FreeBSD.org
COMMENT=	Peer-to-peer network game engine

DIST_SUBDIR=	python
USE_PYTHON=	yes
USE_PYDISTUTILS=	yes
PYDISTUTILS_PKGNAME=	Py2Play
EXAMPLESDIR=	${PREFIX}/share/examples/py-py2play

NO_STAGE=	yes
post-install:
.ifndef NOPORTEXAMPLES
	@${MKDIR} ${EXAMPLESDIR}
	${INSTALL_DATA} ${WRKSRC}/startdemo ${EXAMPLESDIR}
.endif
.if !defined(NOPORTDOCS)
	@${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/README ${DOCSDIR}
.endif

.include <bsd.port.mk>
