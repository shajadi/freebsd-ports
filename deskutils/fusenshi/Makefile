# Created by: Masanori OZAWA (ozawa@ongs.co.jp)
# $FreeBSD$

PORTNAME=	fusenshi
PORTVERSION=	0.9.0
PORTREVISION=	10
CATEGORIES=	deskutils
MASTER_SITES=	http://www.ongs.co.jp/projects/fusenshi/
EXTRACT_SUFX=	.tgz

MAINTAINER=	ozawa@ongs.co.jp
COMMENT=	A Post-it(R) like application with network support

LIB_DEPENDS=	gtkmm-2.4:${PORTSDIR}/x11-toolkits/gtkmm24 \
		gtksourceview-1.0:${PORTSDIR}/x11-toolkits/gtksourceview

USES=		pkgconfig
USE_GNOME=	libxml2
MAKE_JOBS_UNSAFE=	yes

.ifdef WITHOUT_SSL
MAKE_ARGS+=	WITHOUT_SSL=yes
.else
LIB_DEPENDS+=	gnutls:${PORTSDIR}/security/gnutls
.endif

NO_STAGE=	yes
post-install:
	@${STRIP_CMD} ${PREFIX}/bin/fusenshi

.include <bsd.port.mk>
