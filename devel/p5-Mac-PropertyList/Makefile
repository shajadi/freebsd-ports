# Created by: Nobutaka Mantani <nobutaka@FreeBSD.org>
# $FreeBSD$

PORTNAME=	Mac-PropertyList
PORTVERSION=	1.38
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	nobutaka@FreeBSD.org
COMMENT=	A Perl extension for parsing Mac OS X property lists

LICENSE_COMB=	dual
LICENSE=	ART10 GPLv1

BUILD_DEPENDS=	p5-XML-Entities>=0:${PORTSDIR}/textproc/p5-XML-Entities
RUN_DEPENDS:=	${BUILD_DEPENDS}

USES=		perl5
USE_PERL5=	configure

MAN3=	Mac::PropertyList.3 \
	Mac::PropertyList::ReadBinary.3 \
	Mac::PropertyList::WriteBinary.3

NO_STAGE=	yes
.include <bsd.port.mk>
