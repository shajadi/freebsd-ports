# Created by: ijliao
# $FreeBSD$

PORTNAME=	jmusic
PORTVERSION=	1.6.4
CATEGORIES=	audio java
MASTER_SITES=	SF/${PORTNAME}/jMusic_Stable/${PORTVERSION} \
		SF/${PORTNAME}/jMusic_Instruments/${PORTVERSION:S/.4//}/:instruments \
		SF/${PORTNAME}/jMusic_Docs/${PORTVERSION}/:docs
DISTFILES=	jMusic${PORTVERSION}.jar \
		jMusic_1.6_inst.zip:instruments \
		jMusic_doc_${PORTVERSION}.zip:docs
DIST_SUBDIR=	${PORTNAME}
EXTRACT_ONLY=	jMusic_1.6_inst.zip \
		jMusic_doc_${PORTVERSION}.zip

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Composition in Java

USE_JAVA=	yes
NO_STAGE=	yes
JAVA_VERSION=	1.6+
NO_BUILD=	yes
NO_WRKSUBDIR=	yes

PORTDOCS=	*

.include <bsd.port.options.mk>

do-install:
	${MKDIR} ${JAVAJARDIR}/${PORTNAME}
	@${INSTALL_DATA} ${DISTDIR}/${DIST_SUBDIR}/jMusic${PORTVERSION}.jar \
		${JAVAJARDIR}/${PORTNAME}/${PORTNAME}.jar
	@(cd ${WRKSRC} && ${COPYTREE_SHARE} inst ${JAVAJARDIR}/${PORTNAME})

post-install:
.if ${PORT_OPTIONS:MDOCS}
	${MKDIR} ${DOCSDIR}
	@(cd ${WRKSRC} && ${COPYTREE_SHARE} doc ${DOCSDIR})
.endif

.include <bsd.port.mk>
