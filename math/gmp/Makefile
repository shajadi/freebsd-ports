# Created by: Ying-Chieh Liao <ijliao@FreeBSD.org>
# $FreeBSD$

PORTNAME=	gmp
PORTVERSION=	5.1.3
CATEGORIES=	math devel
MASTER_SITES=	${MASTER_SITE_GNU}
MASTER_SITE_SUBDIR=	gmp

MAINTAINER=	ale@FreeBSD.org
COMMENT=	A free library for arbitrary precision arithmetic

LICENSE=	LGPL3

OPTIONS_DEFINE=	CPU_OPTS
CPU_OPTS_DESC=	Enable assembly optimizations for your CPU

USE_XZ=		yes
HAS_CONFIGURE=	yes
GNU_CONFIGURE=	no # needed, since the following line would add it
USE_AUTOTOOLS=	libtool
USE_GNOME=	ltverhack
CONFIGURE_ENV=	MAKEINFO="makeinfo --no-split"
CONFIGURE_ARGS=	--prefix=${PREFIX} \
		--infodir=${PREFIX}/info \
		--mandir=${PREFIX}/man \
		--enable-cxx
USE_LDCONFIG=	yes

INFO=		gmp

.include <bsd.port.pre.mk>

.if ! ${PORT_OPTIONS:MCPU_OPTS}
CONFIGURE_ARGS+=--build=${ARCH}-portbld-freebsd${OSREL}
.elif ${ARCH:S/64//} != ${ARCH}
CONFIGURE_ENV+=	ABI="64"
.else
CONFIGURE_ENV+=	ABI="32"
.endif

post-extract:
	@${RM} -f ${WRKSRC}/doc/gmp.info*

post-patch:
	@${REINPLACE_CMD} "s/\(athlon64\-\*\-\*\)/amd64-*-* | \1/;s/\(x86_64)\)/amd64 | \1/" \
		${WRKSRC}/configure

regression-test check: build
	@cd ${WRKSRC} && ${SETENV} ${MAKE_ENV} ${MAKE} check

.include <bsd.port.post.mk>
