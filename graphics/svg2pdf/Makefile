# Created by: Joe Marcus Clarke <marcus@FreeBSD.org>
# $FreeBSD$
#   $MCom: ports/graphics/svg2pdf/Makefile,v 1.2 2005/08/08 02:09:09 marcus Exp $

PORTNAME=	svg2pdf
PORTVERSION=	0.1.3
PORTREVISION=	5
CATEGORIES=	graphics
MASTER_SITES=	http://cairographics.org/snapshots/

MAINTAINER=	gnome@FreeBSD.org
COMMENT=	Render an SVG image to a PDF file (using cairo)

LIB_DEPENDS=	svg-cairo.1:${PORTSDIR}/graphics/libsvg-cairo

GNU_CONFIGURE=	yes
USES=		pkgconfig

MAN1=		svg2pdf.1
PLIST_FILES=	bin/svg2pdf

NO_STAGE=	yes
.include <bsd.port.mk>
