# Created by: Nick Sayer
# $FreeBSD$

PORTNAME=	mgapdesk
PORTVERSION=	1.0.7
PORTREVISION=	5
CATEGORIES=	x11
MASTER_SITES=	ftp://ftp.matrox.com/pub/mga/archive/linux/2001/powerdesk_1_00_7/
DISTNAME=	${PORTNAME}-1_00-7beta_src
EXTRACT_SUFX=	.tgz

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Matrox Powerdesk for *nix

IGNORE=		needs an old XFree86/X.org header file to build

USE_GNOME=	gtk12
USES=		gmake
USE_AUTOTOOLS=	autoconf213

WRKSRC=		${WRKDIR}/${PORTNAME}

NO_STAGE=	yes
.include <bsd.port.pre.mk>

.if (${ARCH} == "alpha")
LDFLAGS+=	-lio
.endif

.if ${ARCH} == "sparc64" || ${ARCH} == "ia64"
BROKEN=		Does not compile on sparc64 or ia64
.endif

post-extract:
		@${RM} -f ${WRKSRC}/config.cache
		@${CHMOD} 750 ${WRKSRC}/missing

.include <bsd.port.post.mk>
