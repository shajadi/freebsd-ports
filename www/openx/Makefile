# Created by: Piotr Rybicki <meritus@innervision.pl>
# $FreeBSD$

PORTNAME=	openx
PORTVERSION=	2.8.11
CATEGORIES=	www
MASTER_SITES=	http://download.openx.org/

MAINTAINER=	meritus@innervision.pl
COMMENT=	Free, opensource ad server in PHP

LICENSE=	GPLv2

USE_BZIP2=	yes
NO_BUILD=	yes
SUB_LIST+=	PKGNAME=${PKGNAME}
SUB_FILES+=	pkg-message

NO_STAGE=	yes
.include <bsd.port.pre.mk>

.if !defined(WITHOUT_PHP_DEPENDS)
USE_PHP=	xml pcre zlib mysql pgsql ftp
.endif

do-install:
	@cd ${WRKSRC} && ${COPYTREE_SHARE} . ${WWWDIR}
	@${CHOWN} -R ${WWWOWN}:${WWWGRP} ${WWWDIR}
	@${CHMOD} -R 755 ${WWWDIR}
	@${ECHO_CMD} '@exec ${CHOWN} -R ${WWWOWN}:${WWWGRP} ${WWWDIR}' >> ${TMPPLIST}
	@${ECHO_CMD} '@exec ${CHMOD} -R 755 ${WWWDIR}' >> ${TMPPLIST}

post-install:
	@${CAT} ${PKGMESSAGE}

.include <bsd.port.post.mk>
