# Created by: Sunpoet Po-Chuan Hsieh <sunpoet@FreeBSD.org>
# $FreeBSD$

PORTNAME=	Module-Build-Tiny
PORTVERSION=	0.030
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Tiny replacement for Module::Build

LICENSE=	ART10 GPLv1
LICENSE_COMB=	dual

BUILD_DEPENDS=	p5-ExtUtils-Config>=0.003:${PORTSDIR}/devel/p5-ExtUtils-Config \
		p5-ExtUtils-Helpers>=0.020:${PORTSDIR}/devel/p5-ExtUtils-Helpers \
		p5-ExtUtils-InstallPaths>=0.002:${PORTSDIR}/devel/p5-ExtUtils-InstallPaths \
		p5-Test-Harness>=3.29:${PORTSDIR}/devel/p5-Test-Harness
RUN_DEPENDS:=	${BUILD_DEPENDS}

USE_PERL5=	modbuildtiny
USES=		perl5

.include <bsd.port.pre.mk>

.if ${PERL_LEVEL} < 501400
BUILD_DEPENDS+=	p5-CPAN-Meta>=0:${PORTSDIR}/devel/p5-CPAN-Meta \
		p5-JSON-PP>=2:${PORTSDIR}/converters/p5-JSON-PP
RUN_DEPENDS+=	p5-CPAN-Meta>=0:${PORTSDIR}/devel/p5-CPAN-Meta \
		p5-JSON-PP>=2:${PORTSDIR}/converters/p5-JSON-PP
.endif

.include <bsd.port.post.mk>
