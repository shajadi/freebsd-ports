# $FreeBSD$

PORTNAME=	Data-Visitor-Encode
PORTVERSION=	0.10007
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	kuriyama@FreeBSD.org
COMMENT=	Perl extension to encode/decode values in a structure

RUN_DEPENDS=	\
	p5-Data-Visitor>=0.18:${PORTSDIR}/devel/p5-Data-Visitor
BUILD_DEPENDS:=	${RUN_DEPENDS}
TEST_DEPENDS=	p5-Test-Exception>0:${PORTSDIR}/devel/p5-Test-Exception

USES=		perl5
USE_PERL5=	configure

MAN3=		Data::Visitor::Encode.3

NO_STAGE=	yes
.include <bsd.port.mk>
