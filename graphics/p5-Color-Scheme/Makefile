# $FreeBSD$

PORTNAME=	Color-Scheme
PORTVERSION=	1.05
CATEGORIES=	graphics perl5
MASTER_SITES=	CPAN
MASTER_SITE_SUBDIR=	Color
PKGNAMEPREFIX=	p5-

MAINTAINER=	tobez@FreeBSD.org
COMMENT=	Generate pleasant color schemes

BUILD_DEPENDS=	p5-Test-Differences>=0.47:${PORTSDIR}/devel/p5-Test-Differences
RUN_DEPENDS:=	${BUILD_DEPENDS}

USES=		perl5
USE_PERL5=	configure

MAN3=	Color::Scheme.3

NO_STAGE=	yes
.include <bsd.port.mk>
