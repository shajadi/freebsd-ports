# Created by: Li-Wen Hsu <lwhsu@FreeBSD.org>
# $FreeBSD$

PORTNAME=	Vroom
PORTVERSION=	0.29
CATEGORIES=	textproc perl5
MASTER_SITES=	CPAN
MASTER_SITE_SUBDIR=	CPAN:INGY
PKGNAMEPREFIX=	p5-

MAINTAINER=	lwhsu@FreeBSD.org
COMMENT=	Slide Shows in Vim

BUILD_DEPENDS=	p5-File-HomeDir>=0:${PORTSDIR}/devel/p5-File-HomeDir \
		p5-IO-All>=0:${PORTSDIR}/devel/p5-IO-All \
		p5-Template-Toolkit-Simple>=0:${PORTSDIR}/www/p5-Template-Toolkit-Simple \
		p5-Term-Size>=0:${PORTSDIR}/devel/p5-Term-Size \
		p5-YAML-LibYAML>=0:${PORTSDIR}/textproc/p5-YAML-LibYAML
RUN_DEPENDS:=	${BUILD_DEPENDS}

USES=		perl5
USE_PERL5=	configure

MAN3=	Vroom.3

NO_STAGE=	yes

.include <bsd.port.mk>
