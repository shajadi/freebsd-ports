# Created by: Edwin Groothuis (edwin@mavetju.org)
# $FreeBSD$

PORTNAME=	pkg_tree
PORTVERSION=	1.1
PORTREVISION=	2
CATEGORIES=	ports-mgmt
MASTER_SITES=	http://www.mavetju.org/download/

MAINTAINER=	edwin@mavetju.org
COMMENT=	Get a 'graphical' tree-overview of installed packages

USES=		perl5

MAN7=		pkg_tree.7
PLIST_FILES=	bin/pkg_tree

NO_STAGE=	yes
post-patch:
	@${REINPLACE_CMD} -e 's|__PREFIX__|${PREFIX}|g ; \
		s|__INSTALL_MAN__|${INSTALL_MAN}|g ; \
		s|__INSTALL_SCRIPT__|${INSTALL_SCRIPT}|g' ${WRKSRC}/Makefile
	@${REINPLACE_CMD} -e 's|#!/usr/bin/perl -w|#!${PERL5} -w|' \
		${WRKSRC}/pkg_tree

.include <bsd.port.mk>
