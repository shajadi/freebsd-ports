# Created by: thierry@pompo.net
# $FreeBSD$

PORTNAME=	ascii2binary
PORTVERSION=	2.14
CATEGORIES=	converters
MASTER_SITES=	http://billposer.org/Software/Downloads/

MAINTAINER=	thierry@FreeBSD.org
COMMENT=	Convert between textual representations of numbers and binary

USE_BZIP2=	yes
USES=		gettext

LICENSE=	GPLv3

GNU_CONFIGURE=	yes
CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib
WRKSRC=		${WRKDIR}/${PORTNAME}-${PORTVERSION}

PLIST_FILES=	bin/ascii2binary bin/binary2ascii

MAN1=		ascii2binary.1 binary2ascii.1

NO_STAGE=	yes
pre-configure:
	${REINPLACE_CMD} -e "s|/usr/local|${LOCALBASE}|" ${WRKSRC}/Makefile.in

.include <bsd.port.mk>
