# Created by: Steve Wills <swills@FreeBSD.org>
# $FreeBSD$

PORTNAME=	UUID
PORTVERSION=	0.04
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
MASTER_SITE_SUBDIR=	CPAN:JNH
PKGNAMEPREFIX=	p5-

MAINTAINER=	swills@FreeBSD.org
COMMENT=	Perl extension for using UUID interfaces as defined in e2fsprogs

LIB_DEPENDS=	uuid:${PORTSDIR}/misc/e2fsprogs-libuuid

USES=		perl5
USE_PERL5=	configure
CFLAGS+=	-I${LOCALBASE}/include

MAN3=	UUID.3

NO_STAGE=	yes
.include <bsd.port.mk>
