# Created by: Lars Thegler <lth@FreeBSD.org>
# $FreeBSD$

PORTNAME=	Net-IMAP-Simple-SSL
PORTVERSION=	1.3
CATEGORIES=	mail perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	lth@FreeBSD.org
COMMENT=	SSL support for Net::IMAP::Simple

BUILD_DEPENDS=	p5-IO-Socket-SSL>=0:${PORTSDIR}/security/p5-IO-Socket-SSL \
		p5-Net-IMAP-Simple>=0:${PORTSDIR}/mail/p5-Net-IMAP-Simple
RUN_DEPENDS:=	${BUILD_DEPENDS}

USES=		perl5
USE_PERL5=	configure

MAN3=	Net::IMAP::Simple::SSL.3

NO_STAGE=	yes
.include <bsd.port.mk>
