# Created by: Alexander Kriventsov <avk@vl.ru>
# $FreeBSD$

PORTNAME=	Crypt-Simple
PORTVERSION=	0.06
PORTREVISION=	2
CATEGORIES=	security perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	avk@vl.ru
COMMENT=	Perl encrypt stuff simply

RUN_DEPENDS=	p5-Crypt-Blowfish>=0:${PORTSDIR}/security/p5-Crypt-Blowfish \
		p5-MIME-Base64>=0:${PORTSDIR}/converters/p5-MIME-Base64 \
		p5-FreezeThaw>=0:${PORTSDIR}/devel/p5-FreezeThaw
BUILD_DEPENDS=	p5-Crypt-Blowfish>=0:${PORTSDIR}/security/p5-Crypt-Blowfish \
		p5-MIME-Base64>=0:${PORTSDIR}/converters/p5-MIME-Base64 \
		p5-FreezeThaw>=0:${PORTSDIR}/devel/p5-FreezeThaw

USES=		perl5
USE_PERL5=	configure

MAN3=	Crypt::Simple.3

NO_STAGE=	yes
.include <bsd.port.mk>
