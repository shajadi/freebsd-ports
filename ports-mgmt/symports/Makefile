# $FreeBSD$

PORTNAME=	symports
PORTVERSION=	1.1
CATEGORIES=	ports-mgmt
MASTER_SITES=	http://isis.poly.edu/~eitan/files/
DISTNAME=	auto-symlink-virtual-${PORTVERSION}

MAINTAINER=	eadler@FreeBSD.org
COMMENT=	Automatically generate symlinks for virtual categories

LICENSE=	BSD

USE_BZIP2=	yes
NO_BUILD=	yes

PLIST_FILES=	bin/${PORTNAME} man/man1/symports.1.gz

do-install:
	${INSTALL_SCRIPT} ${WRKDIR}/auto-symlink-virtual.sh ${STAGEDIR}${PREFIX}/bin/${PORTNAME}
	${INSTALL_MAN} ${WRKDIR}/symports.1 ${STAGEDIR}${MAN1PREFIX}/man/man1/symports.1

.include <bsd.port.mk>
