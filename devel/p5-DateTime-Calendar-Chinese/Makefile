# Created by: Masahiro Teramoto <markun@onohara.to>
# $FreeBSD$

PORTNAME=	DateTime-Calendar-Chinese
PORTVERSION=	1.00
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
MASTER_SITE_SUBDIR=	CPAN:DMAKI
PKGNAMEPREFIX=	p5-

MAINTAINER=	markun@onohara.to
COMMENT=	Traditional Chinese Calendar Implementation

LICENSE=	ART10 GPLv1
LICENSE_COMB=	dual

BUILD_DEPENDS=	p5-DateTime-Event-Chinese>=1.00:${PORTSDIR}/devel/p5-DateTime-Event-Chinese
RUN_DEPENDS=	p5-DateTime-Event-Chinese>=1.00:${PORTSDIR}/devel/p5-DateTime-Event-Chinese

USES=		perl5
USE_PERL5=	configure

MAN3=		DateTime::Calendar::Chinese.3

NO_STAGE=	yes
.include <bsd.port.mk>
