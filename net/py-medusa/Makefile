# Created by: Hye-Shik Chang <perky@fallin.lv>
# $FreeBSD$

PORTNAME=	medusa
PORTVERSION=	0.5.4
PORTREVISION=	1
CATEGORIES=	net devel python
MASTER_SITES=	CHEESESHOP/source/m/${PORTNAME}
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}
DIST_SUBDIR=	python

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Asynchronous socket-based server framework for Python

OPTIONS_DEFINE=	DOCS EXAMPLES

USE_PYTHON=	yes
USE_PYDISTUTILS=	yes

DOCSDIR=	${PREFIX}/share/doc/py-${PORTNAME}
EXAMPLESDIR=	${PREFIX}/share/examples/py-${PORTNAME}

PORTDOCS=	*
PORTEXAMPLES=	*

NO_STAGE=	yes
.include <bsd.port.options.mk>

post-install:
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
.for doc in CHANGES.txt INSTALL.txt LICENSE.txt README.txt TODO.txt
	${INSTALL_DATA} ${WRKSRC}/${doc} ${DOCSDIR}
.endfor
	@(cd ${WRKSRC} && ${COPYTREE_SHARE} docs ${DOCSDIR})
.endif
.if ${PORT_OPTIONS:MEXAMPLES}
	@${MKDIR} ${EXAMPLESDIR}
.for exdir in demo test thread
	@(cd ${WRKSRC} && ${COPYTREE_SHARE} ${exdir} ${EXAMPLESDIR})
.endfor
.endif

.include <bsd.port.mk>
