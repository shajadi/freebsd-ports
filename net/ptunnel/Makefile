# Created by: Yen-Ming Lee <leeym@FreeBSD.org>
# $FreeBSD$

PORTNAME=	ptunnel
PORTVERSION=	0.72
CATEGORIES=	net
MASTER_SITES=	http://www.cs.uit.no/~daniels/PingTunnel/
DISTNAME=	PingTunnel-${PORTVERSION}

MAINTAINER=	leeym@FreeBSD.org
COMMENT=	Tunneling TCP connections over ICMP echo request and reply

WRKSRC=		${WRKDIR}/PingTunnel
USE_GMAKE=	yes

PLIST_FILES=	bin/ptunnel
MAN8=		ptunnel.8

NO_STAGE=	yes
post-patch:
	@${REINPLACE_CMD} -e '/^CC/d;s/-lpthread/${PTHREAD_LIBS}/' ${WRKSRC}/${MAKEFILE}
	@${REINPLACE_CMD} -e 's/stdint.h/inttypes.h/' ${WRKSRC}/ptunnel.h

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/ptunnel ${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/ptunnel.8 ${MAN8PREFIX}/man/man8

.include <bsd.port.mk>
