# Created by: shane@freebsdhackers.net
# $FreeBSD$

PORTNAME=	destroy
PORTVERSION=	20050329
CATEGORIES=	security
MASTER_SITES=	http://www.freebsdhackers.net/destroy/ \
		http://destroy.rider.us/ \
		http://www.impurity.org/mirrors/destroy/

MAINTAINER=	shane@freebsdhackers.net
COMMENT=	Program to securely destroy files on the hard disk

USE_GMAKE=	yes

MAN1=		destroy.1
PLIST_FILES=	bin/destroy

NO_STAGE=	yes
do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/destroy ${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/destroy.1 ${MAN1PREFIX}/man/man1

.include <bsd.port.mk>
