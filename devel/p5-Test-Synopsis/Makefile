# Created by: Takuya Tsuchida <tsucchi@cpan.org>
# $FreeBSD$

PORTNAME=	Test-Synopsis
PORTVERSION=	0.06
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	tsucchi@cpan.org
COMMENT=	Test your SYNOPSIS code in CPAN module

BUILD_DEPENDS=	p5-Filter>=1.35:${PORTSDIR}/devel/p5-Filter \
		p5-Test-Simple>=0.88:${PORTSDIR}/devel/p5-Test-Simple
RUN_DEPENDS=	p5-Filter>=1.35:${PORTSDIR}/devel/p5-Filter \
		p5-Test-Simple>=0.88:${PORTSDIR}/devel/p5-Test-Simple

USES=		perl5
USE_PERL5=	configure
MAN3=		Test::Synopsis.3

NO_STAGE=	yes
.include <bsd.port.mk>
