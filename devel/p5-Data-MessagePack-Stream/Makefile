# $FreeBSD$

PORTNAME=	Data-MessagePack-Stream
PORTVERSION=	0.07
PORTREVISION=	1
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	kuriyama@FreeBSD.org
COMMENT=	Perl extension for yet another messagepack streaming deserializer

BUILD_DEPENDS=	p5-Data-MessagePack>0:${PORTSDIR}/devel/p5-Data-MessagePack

USES=		perl5
USE_PERL5=	configure
MAKE_JOBS_UNSAFE=	yes

MAN3=	Data::MessagePack::Stream.3

NO_STAGE=	yes
.include <bsd.port.mk>
