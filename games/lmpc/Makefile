# Created by: Alexey Dokuchaev <danfe@FreeBSD.org>
# $FreeBSD$

PORTNAME=	lmpc
PORTVERSION=	3.4.4
CATEGORIES=	games
MASTER_SITES=	SF/${PORTNAME}/${PORTNAME}/${PORTNAME}-${PORTVERSION} \
		http://demospecs.half-empty.de/lmpc-alpha/:doc
DISTFILES=	${DISTNAME}${EXTRACT_SUFX} ${FETCHED_DOCS:S/$/:doc/}
EXTRACT_ONLY=	${DISTNAME}${EXTRACT_SUFX}

MAINTAINER=	danfe@FreeBSD.org
COMMENT=	Tool to manipulate some FPS games demo recordings

LICENSE=	GPLv2

USES=		gmake perl5
MAKE_JOBS_UNSAFE=	yes
GNU_CONFIGURE=	yes
USE_PERL5=	build

PORTSCOUT=	limit:.*[0-9]$$		# letter-suffixed files are binaries

SCRIPTS=	dema dm2cat procdm2.pl
PROGRAMS=	dbs demcut lmpc
FETCHED_DOCS=	${PORTNAME}.html ${PORTNAME}.pdf ${PORTNAME}.sgml
PORTDOCS=	*
PLIST_FILES=	${SCRIPTS:S,^,bin/,} ${PROGRAMS:S,^,bin/,}

OPTIONS_DEFINE=	DOCS

NO_STAGE=	yes
.include <bsd.port.options.mk>

.if ${ARCH} != "i386"
IGNORE=		does not work on ${ARCH}: assumes sizeof(long) == 4
.endif

post-patch:
	@${REINPLACE_CMD} -e 's,bin doc src spec,bin src,' \
		${WRKSRC}/Makefile.in

do-install:
	${INSTALL_SCRIPT} ${SCRIPTS:S,^,${WRKSRC}/bin/,} ${PREFIX}/bin
	${INSTALL_PROGRAM} ${PROGRAMS:S,^,${WRKSRC}/src/,} ${PREFIX}/bin
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/README ${DOCSDIR}
	${INSTALL_DATA} ${FETCHED_DOCS:S,^,${DISTDIR}/,} ${DOCSDIR}
.endif

.include <bsd.port.mk>
