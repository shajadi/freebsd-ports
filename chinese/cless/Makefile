# Created by: David O'Brien (obrien@cs.ucdavis.edu)
# $FreeBSD$

PORTNAME=	cless
PORTVERSION=	290
CATEGORIES=	chinese
MASTER_SITES=	ftp://ftp.cuhk.hk/pub/chinese/ifcss/software/unix/c-utils/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	A better pager utility (and it speaks Chinese)

GNU_CONFIGURE=	yes
CFLAGS+=	-DHANZI # LDFLAGS=-s datadir=/usr/local/lib/less
CPP=		#
MAN1=		cless.1 clesskey.1

NO_STAGE=	yes
post-install:
.if !defined(NOPORTDOCS)
	${MKDIR} ${PREFIX}/share/doc/cless
	${INSTALL_DATA} ${WRKSRC}/README.CLESS ${PREFIX}/share/doc/cless
.endif

.include <bsd.port.mk>
