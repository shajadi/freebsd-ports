# Created by: Robert Noland <rnoland@FreeBSD.org>
# $FreeBSD$

PORTNAME=	simple-ccsm
PORTVERSION=	0.8.4
PORTREVISION=	4
CATEGORIES=	x11-wm
MASTER_SITES=	http://releases.compiz.org/${PORTVERSION}/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	A Python/GTK based settings manager for CompizConfig

RUN_DEPENDS=	${LOCALBASE}/libdata/pkgconfig/compizconfig-python.pc:${PORTSDIR}/x11-wm/compizconfig-python

USE_BZIP2=	yes
USES=		gettext gmake pkgconfig
USE_GNOME=	pygtk2
USE_PYTHON=	-2.7

INSTALLS_EGGINFO=	yes

INSTALLS_ICONS=	yes

NO_STAGE=	yes
.include <bsd.port.mk>
