# Created by: Oleg Mamontov <oleg@mamontov.net>
# $FreeBSD$

PORTNAME=	XML-FeedPP
PORTVERSION=	0.43
CATEGORIES=	textproc perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	oleg@mamontov.net
COMMENT=	Get an RSS file and parse it

LICENSE=	ART10 GPLv1
LICENSE_COMB=	dual

BUILD_DEPENDS=	p5-XML-TreePP>=0.39:${PORTSDIR}/textproc/p5-XML-TreePP
RUN_DEPENDS:=	${BUILD_DEPENDS}

USES=		perl5
USE_PERL5=	configure

MAN3=		XML::FeedPP.3

NO_STAGE=	yes
.include <bsd.port.mk>
