# Created by: Gergely Nagy <8@free.bsd.hu>
# $FreeBSD$

PORTNAME=	ratpoison
PORTVERSION=	1.4.5
PORTREVISION=	1
CATEGORIES=	x11-wm
MASTER_SITES=	${MASTER_SITE_SAVANNAH} \
		http://mirror.4bit.ws/
MASTER_SITE_SUBDIR=	ratpoison

MAINTAINER=	dhn@FreeBSD.org
COMMENT=	Simple window manager with no fat library dependencies

USE_XORG=	xext xinerama xtst
GNU_CONFIGURE=	yes

OPTIONS_DEFINE=	GDM_SUPPORT DOCS
GDM_SUPPORT_DESC=	Install session data files for GDM

SUB_FILES=	ratpoison.desktop

NO_STAGE=	yes
.include <bsd.port.options.mk>

post-patch:
	${REINPLACE_CMD} -e 's|bash|sh|g' ${WRKSRC}/contrib/allwindows.sh

.if ${PORT_OPTIONS:MGDM_SUPPORT}
PLIST_SUB+=	WITH_GDM=""

post-install:
	${MKDIR} ${PREFIX}/etc/dm/Sessions
	${INSTALL_DATA} ${WRKDIR}/ratpoison.desktop ${PREFIX}/etc/dm/Sessions/
.else
PLIST_SUB+=	WITH_GDM="@comment "
.endif

.if ${PORT_OPTIONS:MDOCS}
MAN1=		ratpoison.1
INFO=		ratpoison
.else
INSTALL_TARGET=	SUBDIRS=src install-exec
.endif

.include <bsd.port.mk>
