# Created by: Ion-Mihai "IOnut" Tetcu <itetcu@FreeBSD.org>
# $FreeBSD$

PORTNAME=	unsafe_image_rules
PORTVERSION=	0.8
PORTREVISION=	1
DISTNAME=	${PORTNAME:S/-/_/}.${PORTVERSION}-1.4
DIST_SUBDIR=	squirrelmail

MAINTAINER=	itetcu@FreeBSD.org
COMMENT=	Determines what unsafe (web) images will be shown

USE_SM_COMPAT=	yes
USES=		perl5
USE_PERL5=	run

SQUIRREL_PLUGIN_NAME=	${PORTNAME:S/-/_/}

NO_STAGE=	yes
.include "${.CURDIR}/../squirrelmail/bsd.squirrelmail.mk"

.include <bsd.port.mk>
