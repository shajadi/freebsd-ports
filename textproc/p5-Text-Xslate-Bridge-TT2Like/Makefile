# $FreeBSD$

PORTNAME=	Text-Xslate-Bridge-TT2Like
PORTVERSION=	0.00010
CATEGORIES=	textproc perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	kuriyama@FreeBSD.org
COMMENT=	Perl extension of TT2 Variable Method Clone for Text::Xslate

RUN_DEPENDS=	\
	p5-Text-Xslate>=1.3000:${PORTSDIR}/textproc/p5-Text-Xslate
BUILD_DEPENDS=	${RUN_DEPENDS}

USES=		perl5
USE_PERL5=	configure

MAN3=	Text::Xslate::Bridge::TT2Like.3

NO_STAGE=	yes
.include <bsd.port.mk>
