# Created by: Greg Larkin <glarkin@FreeBSD.org>
# $FreeBSD$

PORTNAME=	gittrac
CATEGORIES=	devel

COMMENT=	Web-Based Bug And Patch-Set Tracking System For Git

RUN_DEPENDS=	git>=0:${PORTSDIR}/devel/git

MASTERDIR=	${.CURDIR}/../cvstrac
MAKE_ARGS=	APPNAME=gittrac
PKGMESSAGE=	${.CURDIR}/pkg-message

NO_STAGE=	yes
.include "${MASTERDIR}/Makefile"
