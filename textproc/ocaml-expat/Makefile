# Created by: Marwan Burelle <marwan.burelle@lri.fr
# $FreeBSD$

PORTNAME=	ocaml-expat
PORTVERSION=	0.9.1
PORTREVISION=	3
CATEGORIES=	textproc
MASTER_SITES=	http://www.xs4all.nl/~mmzeeman/ocaml/

MAINTAINER=	michael.grunewald@laposte.net
COMMENT=	A stub for the expat parser in OCaml

BUILD_DEPENDS=	ocamlc:${PORTSDIR}/lang/ocaml \
		ocamlfind:${PORTSDIR}/devel/ocaml-findlib
RUN_DEPENDS=	ocamlc:${PORTSDIR}/lang/ocaml \
		ocamlfind:${PORTSDIR}/devel/ocaml-findlib
LIB_DEPENDS=	expat.6:${PORTSDIR}/textproc/expat2

USE_GMAKE=	yes
MAKE_ARGS=	EXPAT_LIBDIR=${LOCALBASE}/lib \
		EXPAT_INCDIR=${LOCALBASE}/include \
		CAML_INCDIR=${LOCALBASE}/lib/ocaml

ALL_TARGET=	all allopt

.if !defined(NOPORTDOCS)
ALL_TARGET+=	doc
PORTDOCS=	*
.endif

PKGDEINSTALL=	${PKGINSTALL}

NO_STAGE=	yes
post-install:
	@${FIND} ${PREFIX}/lib/ocaml/site-lib/expat -type f | \
		${SED} "s,^${PREFIX}/,," >> ${TMPPLIST}
	@${ECHO_CMD} "@dirrm lib/ocaml/site-lib/expat" >> ${TMPPLIST}
	@${ECHO_CMD} "@unexec ocamlfind remove expat 2>/dev/null || true" >> ${TMPPLIST}
	PKG_PREFIX=${PREFIX} ${SH} ${PKGINSTALL} ${PKGNAME} POST-INSTALL
.if !defined(NOPORTDOCS)
	@${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/doc/* ${DOCSDIR}
.endif

.include <bsd.port.mk>
