# Created by: UMENO Takashi
# $FreeBSD$

PORTNAME=	gcompmgr
PORTVERSION=	0.21
PORTREVISION=	8
CATEGORIES=	x11-wm
MASTER_SITES=	SF/${PORTNAME}/${PORTNAME}/${PORTNAME}-${PORTVERSION}

MAINTAINER=	umeno@rr.iij4u.or.jp
COMMENT=	GNOME interface to xcompmgr

RUN_DEPENDS=	xcompmgr:${PORTSDIR}/x11-wm/xcompmgr
LIB_DEPENDS=	gtkmm-2.4.1:${PORTSDIR}/x11-toolkits/gtkmm24

GNU_CONFIGURE=	yes
USES=		pkgconfig
USE_AUTOTOOLS=	automake:env

DESKTOP_ENTRIES="gcompmgr" \
		"Configure window effects" \
		"" \
		"gcompmgr" \
		"DesktopSettings;Settings;GTK;" \
		true


NO_STAGE=	yes
post-patch:
.for file in depcomp install-sh missing
	@${LN} -sf ${AUTOMAKE_DIR}/${file} ${WRKSRC}
.endfor
	@${REINPLACE_CMD} -e 's|connect(SigC::slot|connect(sigc::mem_fun|g ; \
		s|#include <sigc++\/compatibility\.h>||g' \
			${WRKSRC}/src/*.cc

.include <bsd.port.mk>
