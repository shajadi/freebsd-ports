# Created by: Anton Berezin <tobez@FreeBSD.org>
# $FreeBSD$

PORTNAME=	Data-GUID
PORTVERSION=	0.047
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
MASTER_SITE_SUBDIR=	CPAN:RJBS
PKGNAMEPREFIX=	p5-

MAINTAINER=	tobez@FreeBSD.org
COMMENT=	Generate globally unique identifiers

BUILD_DEPENDS=	p5-Sub-Install>=0.03:${PORTSDIR}/devel/p5-Sub-Install \
		p5-Sub-Exporter>=0.90:${PORTSDIR}/devel/p5-Sub-Exporter \
		p5-Data-UUID>=1.148:${PORTSDIR}/devel/p5-Data-UUID
RUN_DEPENDS:=	${BUILD_DEPENDS}
TEST_DEPENDS=	p5-Test-Simple>=0.88:${PORTSDIR}/devel/p5-Test-Simple

USES=		perl5
USE_PERL5=	configure

MAN3=	Data::GUID.3

NO_STAGE=	yes
.include <bsd.port.mk>
