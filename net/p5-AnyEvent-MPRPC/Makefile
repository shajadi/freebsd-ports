# $FreeBSD$

PORTNAME=	AnyEvent-MPRPC
PORTVERSION=	0.20
CATEGORIES=	net perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	kuriyama@FreeBSD.org
COMMENT=	Perl extension for simple TCP-based MPRPC client/server

RUN_DEPENDS=	\
	p5-Any-Moose>=0.13:${PORTSDIR}/devel/p5-Any-Moose \
	p5-AnyEvent>=5.261:${PORTSDIR}/devel/p5-AnyEvent \
	p5-Data-MessagePack>=0.34:${PORTSDIR}/devel/p5-Data-MessagePack \
	p5-Data-MessagePack-Stream>=0.05:${PORTSDIR}/devel/p5-Data-MessagePack-Stream \
	p5-AnyEvent-MessagePack>=0.19:${PORTSDIR}/devel/p5-AnyEvent-MessagePack
BUILD_DEPENDS:=	${RUN_DEPENDS}
TEST_DEPENDS=	p5-Test-TCP>=0:${PORTSDIR}/devel/p5-Test-TCP

USES=		perl5
USE_PERL5=	configure

MAN3=	AnyEvent::MPRPC.3 \
	AnyEvent::MPRPC::Client.3 \
	AnyEvent::MPRPC::CondVar.3 \
	AnyEvent::MPRPC::Server.3

NO_STAGE=	yes
.include <bsd.port.mk>
