# Created by: Martin Wilke <miwi@FreeBSD.org>
# $FreeBSD$

PORTNAME=	Rose-DBx-Object-MoreHelpers
PORTVERSION=	0.09
CATEGORIES=	databases perl5
MASTER_SITES=	CPAN
MASTER_SITE_SUBDIR=	Rose/KARMAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	miwi@FreeBSD.org
COMMENT=	Perl 5 module to deploy a DBIx::Class schema

RUN_DEPENDS=	p5-Rose-DB-Object>=0.7730,1:${PORTSDIR}/databases/p5-Rose-DB-Object \
		p5-Data-Dump>=1.06:${PORTSDIR}/devel/p5-Data-Dump

USES=		perl5
USE_PERL5=	configure

MAN3=		Rose::DBx::Object::MoreHelpers.3

NO_STAGE=	yes
.include <bsd.port.mk>
