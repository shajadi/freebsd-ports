# Created by: Serge Gagnon <gagnon__s@videotron.ca>
# $FreeBSD$

PORTNAME=	disktool
PORTVERSION=	2.0
PORTREVISION=	3
CATEGORIES=	sysutils
MASTER_SITES=	http://ftp.auxio.org/pub/mirrors/step.polymtl.ca/pub/Xview/apps/disktool/
DISTNAME=	disktool-2.0c

MAINTAINER=	cy@FreeBSD.org
COMMENT=	XView sysadmin tool for monitoring diskfull situations

LIB_DEPENDS=	xview.3:${PORTSDIR}/x11-toolkits/xview

WRKSRC=		${WRKDIR}/${DISTNAME}

ALL_TARGET=	disktool

MAN1=		disktool.1
PLIST_FILES=	bin/disktool

NO_STAGE=	yes
post-patch:
	@${REINPLACE_CMD} -e 's|%%PREFIX%%|${PREFIX}|g' ${WRKSRC}/Makefile

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/disktool ${PREFIX}/bin/
	${INSTALL_MAN} ${WRKSRC}/disktool.man \
	${PREFIX}/man/man1/disktool.1

.include <bsd.port.mk>
