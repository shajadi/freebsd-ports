# Created by: Motoyuki Kasahara <m-kasahr@sra.co.jp>
# $FreeBSD$

PORTNAME?=	libtool
PORTVERSION=	2.4.2
PORTREVISION=	2
CATEGORIES=	devel
MASTER_SITES=	${MASTER_SITE_GNU}
MASTER_SITE_SUBDIR=	libtool
DISTNAME=	libtool-${PORTVERSION}

MAINTAINER=	autotools@FreeBSD.org
COMMENT?=	Generic shared library support script

LICENSE?=        GPLv2
LICENSE_FILE?=   ${WRKSRC}/COPYING

CONFLICTS=	libtool-fixed-[0-9]*

GNU_CONFIGURE=	yes
CONFIGURE_ARGS?= --disable-ltdl-install
CONFIGURE_ENV=	MAKEINFO="makeinfo --no-split"
INFO?=		libtool
.if ${PORTNAME} != "libltdl"
MAN1=		libtool.1 libtoolize.1
.endif

NO_STAGE=	yes

post-extract:
	@${RM} -f ${WRKSRC}/doc/*.info*

post-patch:
	@${REINPLACE_CMD} -e 's|sed gsed|sed|g' \
		-e 's|CC=cc|CC=${CC}|g' \
		${WRKSRC}/configure ${WRKSRC}/libltdl/configure

post-configure:
	@${FIND} ${WRKSRC} -type f | ${XARGS} ${TOUCH} -f

.include <bsd.port.mk>
