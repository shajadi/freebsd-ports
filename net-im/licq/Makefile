# Created by: Brian Feldman & Matt Heckaman
# $FreeBSD$

PORTNAME=	base
PORTVERSION=	${LICQ_VER}
PORTREVISION=	1
CATEGORIES=	net-im
PKGNAMESUFFIX=	${SOCKS_SUFFIX}${PKGNAMESUFFIX2}

MAINTAINER=	dinoex@FreeBSD.org
COMMENT=	A popular ICQ-compatible plugin-based program

LIB_DEPENDS=	boost_regex:${PORTSDIR}/devel/boost-libs

LICENSE=	GPLv2

NO_STAGE=	yes

USES=		cmake iconv
WRKSRC=		${WRKDIR}/${DISTNAME}
LICQ_PORT?=	net-im/licq

# workaround for installed autoconf/automake
LDFLAGS+=	${PTHREAD_LIBS} -L${LOCALBASE}/lib ${ICONV_LIB} -Wl,--export-dynamic
CPPFLAGS+=	-I${LOCALBASE}/include
CFLAGS+=	-I${LOCALBASE}/include
CXXFLAGS+=	-Wl,--export-dynamic

.if !defined(WITHOUT_OPENSSL)
USE_OPENSSL=	yes
CONFIGURE_ARGS+=--with-openssl-inc=${OPENSSLINC}
CONFIGURE_ARGS+=--with-openssl-lib=${OPENSSLLIB}
.endif

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MNLS}
CMAKE_ARGS+=	-DENABLE_NLS:BOOL=OFF
PLIST_SUB+=	NLS="@comment "
.else
USES+=		gettext
PLIST_SUB+=	NLS=""
.endif

pre-configure:
	${REINPLACE_CMD} -e 's=!/bin/bash=!${LOCALBASE}/bin/bash=' \
		${WRKSRC}/bin/sidclean.sh

post-install:
	@${MKDIR} ${PREFIX}/lib/licq
	@${CAT} ${PKGMESSAGE}
	${INSTALL_SCRIPT} ${WRKSRC}/bin/sidclean.sh ${PREFIX}/bin/sidclean.bash

.include <bsd.port.pre.mk>

.include "${PORTSDIR}/${LICQ_PORT}/Makefile.inc"

.include <bsd.port.post.mk>
