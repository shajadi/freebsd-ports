# $FreeBSD$

PORTNAME=	Plack-Server-ReverseHTTP
PORTVERSION=	0.02
CATEGORIES=	www perl5
MASTER_SITES=	CPAN
MASTER_SITE_SUBDIR=	CPAN:MIYAGAWA
PKGNAMEPREFIX=	p5-

MAINTAINER=	kuriyama@FreeBSD.org
COMMENT=	Perl extension of reversehttp gateway for PSGI application

RUN_DEPENDS=	\
	p5-AnyEvent>0:${PORTSDIR}/devel/p5-AnyEvent \
	p5-AnyEvent-ReverseHTTP>0:${PORTSDIR}/www/p5-AnyEvent-ReverseHTTP \
	p5-Plack>0:${PORTSDIR}/www/p5-Plack
BUILD_DEPENDS:=	${RUN_DEPENDS}

USES=		perl5
USE_PERL5=	configure

MAN3=	Plack::Server::ReverseHTTP.3

NO_STAGE=	yes
.include <bsd.port.mk>
