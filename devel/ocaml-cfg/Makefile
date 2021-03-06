# Created by: Stanislav Sedov <ssedov@mbsd.msk.ru>
# $FreeBSD$

PORTNAME=	cfg
PORTVERSION=	2.0.1
CATEGORIES=	devel
MASTER_SITES=	http://cdn.bitbucket.org/mmottl/cfg/downloads/
PKGNAMEPREFIX=	ocaml-

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Library for manipulation of context-free grammars

LICENSE=	LGPL21

BUILD_DEPENDS=	menhir:${PORTSDIR}/devel/menhir

OPTIONS_DEFINE=	DOCS EXAMPLES

USE_OCAML=	yes
USE_OCAML_FINDLIB=yes
USE_OCAMLFIND_PLIST=yes
USE_OCAML_WASH=	yes

HAS_CONFIGURE=	yes
CONFIGURE_ARGS=	--prefix ${PREFIX} --disable-docs --disable-examples
MAKE_JOBS_UNSAFE=yes

DOCSDIR=	${OCAML_DOCSDIR}/${PORTNAME}
EXAMPLESDIR=	${OCAML_EXAMPLESDIR}/${PORTNAME}

PORTDOCS=	*
PORTEXAMPLES=	*

NO_STAGE=	yes
.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MDOCS}
PLIST_DIRSTRY+=	${OCAML_DOCSDIR:S,^${PREFIX}/,,}
.endif

.if ${PORT_OPTIONS:MEXAMPLES}
PLIST_DIRSTRY+=	${OCAML_EXAMPLESDIR:S,^${PREFIX}/,,}
.endif

post-install:
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
.for i in AUTHORS.txt CHANGES.txt README.md
	(cd ${WRKSRC} && ${INSTALL_DATA} ${i} ${DOCSDIR})
.endfor
.endif
.if ${PORT_OPTIONS:MEXAMPLES}
	@${MKDIR} ${EXAMPLESDIR}
	@(cd ${WRKSRC}/examples && ${COPYTREE_SHARE} . ${EXAMPLESDIR})
.endif

.include <bsd.port.mk>
