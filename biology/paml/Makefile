# Created by: dbader@eece.unm.edu
# $FreeBSD$

PORTNAME=	paml
PORTVERSION=	4.4c
CATEGORIES=	biology
MASTER_SITES=	http://abacus.gene.ucl.ac.uk/software/
DISTNAME=	${PORTNAME}${PORTVERSION}

MAINTAINER=	wen@FreeBSD.org
COMMENT=	Phylogenetic Analysis by Maximum Likelihood (PAML)

USE_GMAKE=	YES
WRKSRC=		${WRKDIR}/${PORTNAME}44/src
MAKE_ARGS=	CC="${CC}" CFLAGS="${CFLAGS}"

BINARIES=	baseml basemlg chi2 codeml evolver pamp yn00
DOC_FILES=	MCMCtreeDoc.pdf pamlDOC.pdf pamlFAQs.pdf pamlHistory.txt

NO_STAGE=	yes
do-install:
.for f in ${BINARIES}
	${INSTALL_PROGRAM} ${WRKSRC}/${f} ${PREFIX}/bin
.endfor
.if !defined(NOPORTDOCS)
	${MKDIR} ${DOCSDIR}
.for f in ${DOC_FILES}
	${INSTALL_DATA} ${WRKDIR}/${PORTNAME}44/doc/${f} ${DOCSDIR}
.endfor
.endif

.include <bsd.port.mk>
