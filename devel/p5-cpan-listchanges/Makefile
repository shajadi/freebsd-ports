# $FreeBSD$

PORTNAME=	cpan-listchanges
PORTVERSION=	0.06
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
MASTER_SITE_SUBDIR=	CPAN:MIYAGAWA
PKGNAMEPREFIX=	p5-

MAINTAINER=	kuriyama@FreeBSD.org
COMMENT=	Perl extension to list changes for CPAN modules

RUN_DEPENDS=	\
	p5-Algorithm-Diff>0:${PORTSDIR}/devel/p5-Algorithm-Diff \
	p5-CPAN-DistnameInfo>0:${PORTSDIR}/devel/p5-CPAN-DistnameInfo \
	p5-libwww>0:${PORTSDIR}/www/p5-libwww \
	p5-Module-Metadata>0:${PORTSDIR}/devel/p5-Module-Metadata \
	p5-Try-Tiny>0:${PORTSDIR}/lang/p5-Try-Tiny \
	p5-YAML>0:${PORTSDIR}/textproc/p5-YAML
BUILD_DEPENDS:=	${RUN_DEPENDS}

USES=		perl5
USE_PERL5=	modbuild

MAN1=	cpan-listchanges.1
MAN3=	App::cpanlistchanges.3

NO_STAGE=	yes
.include <bsd.port.mk>
