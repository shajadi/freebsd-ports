# Created by: Patrick Powell <papowell@astart.com>
# $FreeBSD$

PORTNAME=	XML-Compile-SOAP-WSA
PORTVERSION=	0.12
CATEGORIES=	net perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	papowell@astart.com
COMMENT=	SOAP message messages with WSA fields

BUILD_DEPENDS=	p5-Net-Server>=0.97:${PORTSDIR}/net/p5-Net-Server \
		p5-libwww>=5.803:${PORTSDIR}/www/p5-libwww \
		p5-Log-Report>=0.22:${PORTSDIR}/devel/p5-Log-Report \
		p5-XML-Compile-SOAP>=2.10:${PORTSDIR}/net/p5-XML-Compile-SOAP \
		p5-XML-Compile>=1.01:${PORTSDIR}/textproc/p5-XML-Compile \
		p5-XML-Compile-Cache>=0.91:${PORTSDIR}/textproc/p5-XML-Compile-Cache
RUN_DEPENDS:=	${BUILD_DEPENDS}

USES=		perl5
USE_PERL5=	configure

MAN3=	XML::Compile::SOAP::WSA.3 \
	XML::Compile::SOAP::WSA::Util.3

NO_STAGE=	yes
.include <bsd.port.mk>
