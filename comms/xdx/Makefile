# Created by: Matt Dawson <matt@mattsnetwork.co.uk>
# $FreeBSD$

PORTNAME=	xdx
PORTVERSION=	2.4
PORTREVISION=	5
CATEGORIES=	comms hamradio
MASTER_SITES=	http://www.chronos.org.uk/download/ \
		${MASTER_SITE_LOCAL}
MASTER_SITE_SUBDIR=	db

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Amateur Radio DX cluster monitor

USE_GNOME=	gtk20
GNU_CONFIGURE=	yes
USES=		gmake pkgconfig

MAN1=		xdx.1
LICENSE=	GPLv2

NO_STAGE=	yes
post-patch:
	@${FIND} ${WRKSRC} -name Makefile.in | ${XARGS} ${REINPLACE_CMD} -e \
		's|-D.*_DISABLE_DEPRECATED||g'

.include <bsd.port.mk>
