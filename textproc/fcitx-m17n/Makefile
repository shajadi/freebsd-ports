# Created by: Zhihao Yuan <lichray@gmail.com>
# $FreeBSD$

PORTNAME=	fcitx-m17n
PORTVERSION=	0.1.4
CATEGORIES=	textproc
MASTER_SITES=	GOOGLE_CODE
PROJECTHOST=	fcitx
DIST_SUBDIR=	fcitx

MAINTAINER=	lichray@gmail.com
COMMENT=	Multilingualization support for Fcitx

LIB_DEPENDS=	fcitx-config:${PORTSDIR}/chinese/fcitx \
		m17n:${PORTSDIR}/devel/m17n-lib

USE_XZ=		yes
USES=		cmake gettext pkgconfig
USE_GNOME=	intltool

NO_STAGE=	yes
.include <bsd.port.mk>
