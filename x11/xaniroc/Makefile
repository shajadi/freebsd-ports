# Created by: Stefan Zehl <sec@42.org>
# $FreeBSD$

PORTNAME=	xaniroc
PORTVERSION=	1.02
PORTREVISION=	2
CATEGORIES=	x11
MASTER_SITES=	ftp://ftp.42.org/pub/orphan/
DISTNAME=	${PORTNAME}
EXTRACT_SUFX=	.src.tar.Z

MAINTAINER=	sec@42.org
COMMENT=	Animate your root-cursor

USES=		imake
USE_XORG=	ice sm x11 xaw xext xmu xpm xt
MAN1=		xaniroc.1
PLIST_FILES=	bin/xaniroc

NO_STAGE=	yes
post-extract:
	${MV} ${WRKSRC}/manpage.1 ${WRKSRC}/xaniroc.man

.include <bsd.port.mk>
