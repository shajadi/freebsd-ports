# Created by: Hendrik Scholz <hscholz@raisdorf.net>
# $FreeBSD$

PORTNAME=	buici-clock
PORTVERSION=	0.4.9.2
CATEGORIES=	x11-clocks
MASTER_SITES=	DEBIAN
DISTNAME=	${PORTNAME}_${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Xlib implementation of an attractive, configurable clock

LICENSE=	GPLv2 # (or later)

LIB_DEPENDS=	cairo.2:${PORTSDIR}/graphics/cairo

WRKSRC=		${WRKDIR}/${PORTNAME}-${PORTVERSION}

USE_XORG=	x11 xext
USES=		bison pkgconfig
USE_GMAKE=	yes
GNU_CONFIGURE=	yes
MAKE_JOBS_UNSAFE=yes

MAN1=		buici-clock.1
PLIST_FILES=	bin/buici-clock

NO_STAGE=	yes
post-patch:
	@${REINPLACE_CMD} -e \
		's|echo -e|echo| ; \
		 s|-g | |' ${WRKSRC}/Makefile.in
	@${REINPLACE_CMD} -e \
		's|_=|+=| ; \
		 s|-g | |' ${WRKSRC}/xo/Makefile.in

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/buici-clock ${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/buici-clock.1 ${MANPREFIX}/man/man1

.include <bsd.port.mk>
