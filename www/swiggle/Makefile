# Created by: Josef El-Rayes <j.el-rayes@daemon.li>
# $FreeBSD$

PORTNAME=	swiggle
PORTVERSION=	0.4
PORTREVISION=	8
CATEGORIES=	www
MASTER_SITES=	http://homepage.univie.ac.at/l.ertl/swiggle/files/ \
		http://bsd-geek.de/FreeBSD/distfiles/

MAINTAINER=	lme@FreeBSD.org
COMMENT=	Swiggle is a commandline web image gallery generator

LIB_DEPENDS=	jpeg.11:${PORTSDIR}/graphics/jpeg \
		exif.12:${PORTSDIR}/graphics/libexif

NO_STAGE=	yes
post-patch:
	${REINPLACE_CMD} -e 's,/usr/local,${LOCALBASE},g' ${WRKSRC}/Makefile

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/swiggle ${PREFIX}/bin

post-install:
.if !defined(NOPORTDOCS)
	${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/README ${DOCSDIR}
.endif

.include <bsd.port.mk>
