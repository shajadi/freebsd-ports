# Created by: Lukasz Wasikowski <lukasz@wasikowski.net>
# $FreeBSD$

PORTNAME=	mod_macro
PORTVERSION=	1.1.11
CATEGORIES=	www
MASTER_SITES=	http://www.cri.ensmp.fr/~coelho/mod_macro/

MAINTAINER=	lukasz@wasikowski.net
COMMENT=	Apache 2.2.x module for use macros in config files

LICENSE=	mod_macro
LICENSE_NAME=	mod_macro license (apache with postcard request)
LICENSE_FILE=	${WRKSRC}/LICENSE
LICENSE_PERMS=	dist-mirror dist-sell pkg-mirror pkg-sell auto-accept


USE_APACHE=	22
LATEST_LINK=	mod_macro22
AP_FAST_BUILD=	yes
AP_GENPLIST=	yes
PORTDOCS=	${PORTNAME}.html

PORTSCOUT=	limit:^1\.1\.

OPTIONS_DEFINE=	DOCS

NO_STAGE=	yes
.include <bsd.port.options.mk>

post-install:
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}/
	${INSTALL_DATA} ${WRKSRC}/${PORTDOCS} ${DOCSDIR}/
.endif

.include <bsd.port.mk>
