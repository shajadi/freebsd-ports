# Created by: Yi-Jheng Lin <yzlin@cs.nctu.edu.tw>
# $FreeBSD$

PORTNAME=	safe-rm
PORTVERSION=	0.10
CATEGORIES=	sysutils
MASTER_SITES=	http://launchpad.net/safe-rm/trunk/0.10/+download/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Wrapper around the rm command to prevent accidental deletions

LICENSE=	GPLv3

USES=		perl5
USE_PERL5=	run
NO_BUILD=	yes

FETCH_ARGS=	-pRr

PORTDOCS=	COPYING Changes README
PLIST_FILES=	bin/safe-rm

NO_STAGE=	yes
.include <bsd.port.options.mk>

do-install:
	${INSTALL_SCRIPT} ${WRKSRC}/safe-rm ${PREFIX}/bin

post-install:
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
	${INSTALL_MAN} ${PORTDOCS:S,^,${WRKSRC}/,} ${DOCSDIR}
.endif

.include <bsd.port.mk>
