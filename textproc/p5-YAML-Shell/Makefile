# Created by: Steve Wills <swills@FreeBSD.org>
# $FreeBSD$

PORTNAME=	YAML-Shell
PORTVERSION=	0.60
CATEGORIES=	textproc perl5
MASTER_SITES=	CPAN
MASTER_SITE_SUBDIR=	CPAN:INGY
PKGNAMEPREFIX=	p5-

MAINTAINER=	swills@FreeBSD.org
COMMENT=	The YAML Test Shell

BUILD_DEPENDS=	p5-YAML>=0.67:${PORTSDIR}/textproc/p5-YAML
RUN_DEPENDS=	p5-YAML>=0.67:${PORTSDIR}/textproc/p5-YAML

USES=		perl5
USE_PERL5=	configure

MAN1=		ysh.1
MAN3=		YAML::Shell.3

NO_STAGE=	yes
.include <bsd.port.mk>
