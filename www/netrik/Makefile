# Created by: Alan Eldridge <alane@FreeBSD.org>
# $FreeBSD$

PORTNAME=	netrik
PORTVERSION=	1.16.1
CATEGORIES=	www
MASTER_SITES=	SF/${PORTNAME}/stable/${PORTVERSION}%20%28beta%29

MAINTAINER=	ale@FreeBSD.org
COMMENT=	Text web browser, ambitious, in active development

RUN_DEPENDS=	wget:${PORTSDIR}/ftp/wget

USE_GMAKE=	yes
GNU_CONFIGURE=	yes

PLIST_FILES=	bin/netrik

MAN1=		netrik.1
MAN5=		netrikrc.5

PORTDOCS=	*

NO_STAGE=	yes
post-patch:
	@${REINPLACE_CMD} "s/#include <ncursesw\//#include </" \
		${WRKSRC}/*.c
.if defined(NOPORTDOCS)
	@${REINPLACE_CMD} "s/install-data-am: install-docDATA/install-data-am:/" \
		${WRKSRC}/Makefile.in
	@${REINPLACE_CMD} "s/install-docDATA install-man/install-man/" \
		${WRKSRC}/doc/Makefile.in
.endif

.include <bsd.port.mk>
