# Created by: Anes Mukhametov <anes@anes.su>
# $FreeBSD$

PORTNAME=	Test-Able-Runner
PORTVERSION=	1.001
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	anes@anes.su
COMMENT=	Use Test::Able without a bunch of boilerplate

LICENSE=	ART10 GPLv1
LICENSE_COMB=	dual

BUILD_DEPENDS=	p5-Module-Pluggable>=3.6:${PORTSDIR}/devel/p5-Module-Pluggable \
		p5-Moose>=0.94:${PORTSDIR}/devel/p5-Moose \
		p5-Test-Able>=0.09:${PORTSDIR}/devel/p5-Test-Able
RUN_DEPENDS:=	${BUILD_DEPENDS}

NO_STAGE=	yes
USE_PERL5=	configure
USES=		perl5

MAN3=		Test::Able::Runner.3 \
		Test::Able::Runner::Role::Meta::Class.3

.include <bsd.port.mk>
