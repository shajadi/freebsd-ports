# Created by: Li-Wen Hsu <lwhsu@FreeBSD.org>
# $FreeBSD$

PORTNAME=	gnutls
PORTVERSION=	1.2.4
PORTREVISION=	1
CATEGORIES=	security python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}
DISTNAME=	python-gnutls-${PORTVERSION}

MAINTAINER=	lwhsu@FreeBSD.org
COMMENT=	Python wrapper for the GNUTLS library

LIB_DEPENDS=	gnutls.26:${PORTSDIR}/security/gnutls

USE_PYTHON=	yes
USE_PYDISTUTILS=	yes
PYDISTUTILS_PKGNAME=	python_gnutls

EXAMPLESDIR=	${PREFIX}/share/examples/py-${PORTNAME}

NO_STAGE=	yes
post-patch:
	${REINPLACE_CMD} -e "s|include_dirs=.*|include_dirs=\['${LOCALBASE}/include'\],|" ${WRKSRC}/setup.py
	${REINPLACE_CMD} -e "s|library_dirs=.*|library_dirs=\['${LOCALBASE}/lib'\],|" ${WRKSRC}/setup.py
	${REINPLACE_CMD} -e "s|\.26||g" ${WRKSRC}/gnutls/library/functions.py

.if !defined(NOPORTEXAMPLES)
post-install:
	@${MKDIR} ${EXAMPLESDIR}
	${CP} -R ${WRKSRC}/examples/ ${EXAMPLESDIR}
.endif

.include <bsd.port.mk>
