# Created by: Steven Kreuzer <skreuzer@FreeBSD.org>
# $FreeBSD$

PORTNAME=	AnyEvent-Graphite
PORTVERSION=	0.08
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	skreuzer@FreeBSD.org
COMMENT=	A non-blocking Graphite client

RUN_DEPENDS=	p5-AnyEvent>=4.15:${PORTSDIR}/devel/p5-AnyEvent \
		p5-AnyEvent-SNMP>=1.0:${PORTSDIR}/net-mgmt/p5-AnyEvent-SNMP
BUILD_DEPENDS:=	${RUN_DEPENDS}

USES=		perl5
USE_PERL5=	configure

MAN3=		AnyEvent::Graphite.3 \
		AnyEvent::Graphite::SNMPAgent.3

NO_STAGE=	yes
.include <bsd.port.mk>
