# Created by: Hye-Shik Chang
# $FreeBSD$

PORTNAME=	cvs2svn
PORTVERSION=	2.4.0
PORTREVISION=	4
CATEGORIES=	devel
MASTER_SITES=	http://cvs2svn.tigris.org/files/documents/1462/49237/ \
		LOCAL/ohauer

PATCHFILES=	${PORTNAME}-${PORTVERSION}-r${PATCHREV}.diff.bz2
PATCH_SITES=	${MASTER_SITE_LOCAL}
PATCH_SITE_SUBDIR=	ohauer

MAINTAINER=	ohauer@FreeBSD.org
COMMENT=	CVS to Subversion Repository Converter

BUILD_DEPENDS=	${PYTHON_PKGNAMEPREFIX}gdbm>0:${PORTSDIR}/databases/py-gdbm
RUN_DEPENDS:=	${BUILD_DEPENDS}

# 2.4.0 -> svn r5392
PATCHREV=	5433

USE_PYTHON=		-2.7
USE_PYDISTUTILS=	yes
PYDISTUTILS_AUTOPLIST=	yes

OPTIONS_MULTI=		SCM
OPTIONS_MULTI_SCM=	SUBVERSION GIT BAZAAR
OPTIONS_DEFAULT=	SUBVERSION

SUBVERSION_DESC=	Build with subversion support
GIT_DESC=		Build with git support
BAZAAR_DESC=		Build with Bazaar support

SUBVERSION_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}subversion>=0:${PORTSDIR}/devel/py-subversion
GIT_RUN_DEPENDS=	${LOCALBASE}/bin/git:${PORTSDIR}/devel/git
BAZAAR_RUN_DEPENDS=	${LOCALBASE}/bin/bzr:${PORTSDIR}/devel/bzr

.include <bsd.port.options.mk>

.if ${OSVERSION} > 1000000
RUN_DEPENDS+=	cvs:${PORTSDIR}/devel/cvs
.endif

# documents from ${WRKSRC}/doc
DOCS1=		design-notes.txt making-releases.txt \
		revision-reader.txt symbol-notes.txt

# documents from ${WRKSRC}/www
DOCS2=		cvs2bzr.html cvs2git.html cvs2svn.html \
		faq.html features.html index.html issue_tracker.html \
		project_license.html project_tools.html

PORTDOCS:=	${DOCS1} ${DOCS2}

PORTEXAMPLES=	cvs2bzr-example.options cvs2git-example.options \
		cvs2hg-example.options cvs2svn-example.options

MANPAGES=	cvs2svn.1.gz \
		cvs2git.1.gz \
		cvs2bzr.1.gz

PLIST_FILES+=	${MANPAGES:S|^|man/man1/|}

post-patch:
# be consistent with PORTVERSION
	@${REINPLACE_CMD} -e 's|2.5.0-dev|2.4.0|' \
		${WRKSRC}/PKG-INFO \
		${WRKSRC}/cvs2svn_lib/version.py

# The only thing different in this target vs. the one found in bsd.port.mk
# is that the extract command exit code is ignored.  tar exits with status
# 1 because the distfile contains a symlink that points nowhere.
do-extract:
	@${RM} -rf ${WRKDIR}
	@${MKDIR} ${WRKDIR}
	@-for f in ${EXTRACT_ONLY}; do \
		if ! (cd ${WRKDIR} && ${EXTRACT_CMD} ${EXTRACT_BEFORE_ARGS} ${_DISTDIR}/$$f ${EXTRACT_AFTER_ARGS});\
		then \
			exit 1; \
		fi; \
	done

post-build:
	${MAKE} man -C ${WRKSRC}

post-install:
	@${INSTALL_MAN} ${MANPAGES:R:S|^|${WRKSRC}/|} ${STAGEDIR}${PREFIX}/man/man1/
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	@${INSTALL_DATA} ${DOCS1:S|^|${WRKSRC}/doc/|} ${STAGEDIR}${DOCSDIR}/
	@${INSTALL_DATA} ${DOCS2:S|^|${WRKSRC}/www/|} ${STAGEDIR}${DOCSDIR}/
	@${MKDIR} ${STAGEDIR}${EXAMPLESDIR}
	@${INSTALL_DATA} ${PORTEXAMPLES:S|^|${WRKSRC}/|} ${STAGEDIR}${EXAMPLESDIR}/

.include <bsd.port.mk>
