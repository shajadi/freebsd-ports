# Created by: milki <milki@rescomp.berkeley.edu>
# $FreeBSD$

PORTNAME=	Bot-Training-MegaHAL
PORTVERSION=	0.02
CATEGORIES=	misc perl5
MASTER_SITES=	CPAN
MASTER_SITE_SUBDIR=	CPAN:AVAR
PKGNAMEPREFIX=	p5-

MAINTAINER=	milki@rescomp.berkeley.edu
COMMENT=	Provide megahal.trn via Bot::Training

LICENSE=	ART10 GPLv1
LICENSE_COMB=	dual

BUILD_DEPENDS=	p5-File-ShareDir-Install>=0:${PORTSDIR}/devel/p5-File-ShareDir-Install
RUN_DEPENDS=	p5-Any-Moose>=0:${PORTSDIR}/devel/p5-Any-Moose \
	p5-Bot-Training>=0:${PORTSDIR}/misc/p5-Bot-Training

USES=		perl5
USE_PERL5=	configure

MAN3=	Bot::Training::MegaHAL.3

NO_STAGE=	yes
.include <bsd.port.mk>
