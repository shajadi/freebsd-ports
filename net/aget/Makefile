# Created by: Aaron Zauner <az_mail@gmx.at>
# $FreeBSD$

PORTNAME=	aget
PORTVERSION=	0.4.1
CATEGORIES=	net
MASTER_SITES=	http://www.enderunix.org/aget/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	A multithreaded HTTP download accelerator

PLIST_FILES=	bin/aget
MAN1=	aget.1

NO_STAGE=	yes
post-patch:
# fix man prefix and make portlint happy :)
	@${REINPLACE_CMD} -e 's|/usr/share/man/man1/|${MANPREFIX}/man/man1/|g' -e \
		's|/usr/local/bin/|${PREFIX}/bin/|g' ${WRKSRC}/Makefile

.include <bsd.port.mk>
