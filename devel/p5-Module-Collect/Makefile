# $FreeBSD$

PORTNAME=	Module-Collect
PORTVERSION=	0.06
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	kuriyama@FreeBSD.org
COMMENT=	Perl extension to collect module files from some directories

RUN_DEPENDS=	\
	p5-File-Find-Rule>0:${PORTSDIR}/devel/p5-File-Find-Rule
BUILD_DEPENDS:=	${RUN_DEPENDS}

USES=		perl5
USE_PERL5=	configure

MAN3=		Module::Collect.3 \
		Module::README.3 \
		Module::Collect::Package.3

NO_STAGE=	yes
.include <bsd.port.mk>
