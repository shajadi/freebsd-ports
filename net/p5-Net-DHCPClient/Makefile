# Created by: Sergey Matveychuk <sem@FreeBSD.org>
# $FreeBSD$

PORTNAME=	Net-DHCPClient
PORTVERSION=	1.0
CATEGORIES=	net perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	sem@FreeBSD.org
COMMENT=	A Perl implementation of a DHCP client API

RUN_DEPENDS+=	p5-Net-RawIP>=0:${PORTSDIR}/net/p5-Net-RawIP
USES=		perl5
USE_PERL5=	configure

WRKSRC=		${WRKDIR}/${PORTNAME}

MAN3=		Net::DHCPClient.3

NO_STAGE=	yes
.include <bsd.port.mk>
