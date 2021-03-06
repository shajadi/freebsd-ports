# Created by: Radim Kolar
# $FreeBSD$

PORTNAME=	zgv
PORTVERSION=	5.9
PORTREVISION=	5
CATEGORIES=	graphics
MASTER_SITES=	${MASTER_SITE_SUNSITE}
MASTER_SITE_SUBDIR=	apps/graphics/viewers/svga

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Graphics viewer for SVGAlib

LIB_DEPENDS=	tiff.4:${PORTSDIR}/graphics/tiff \
		vga.1:${PORTSDIR}/graphics/svgalib \
		jpeg.11:${PORTSDIR}/graphics/jpeg \
		png15:${PORTSDIR}/graphics/png

ONLY_FOR_ARCHS=	i386
USE_GMAKE=	yes
ALL_TARGET=	zgv info
MAKE_ENV=	ZGV_LIBS="${LDFLAGS}"
BINMODE=	4755

PLIST_FILES=	bin/zgv etc/zgvrc.sample
.if !defined(NO_INSTALL_MANPAGES)
MAN1=		zgv.1
.endif
.if !defined(NOPORTDOCS)
INFO=		zgv
PORTDOCS=	NEWS README SECURITY TODO INSTALL
.endif

NO_STAGE=	yes
post-patch:
	${RM} ${WRKSRC}/doc/zgv
	@${REINPLACE_CMD} -e 's|ZGV_LIBS=|ZGV_LIBS+=|' ${WRKSRC}/src/Makefile

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/src/zgv ${PREFIX}/bin
	${INSTALL_DATA} ${WRKSRC}/doc/sample.zgvrc ${PREFIX}/etc/zgvrc.sample
.if !defined(NOPORTDOCS)
	${INSTALL_DATA} ${WRKSRC}/doc/zgv ${PREFIX}/${INFO_PATH}/zgv.info
	${MKDIR} ${DOCSDIR}
.for i in ${PORTDOCS}
	${INSTALL_DATA} ${WRKSRC}/${i} ${DOCSDIR}
.endfor
.endif
.if !defined(NO_INSTALL_MANPAGES)
	${INSTALL_MAN} ${WRKSRC}/doc/zgv.1 ${MAN1PREFIX}/man/man1
.endif

.include <bsd.port.mk>
