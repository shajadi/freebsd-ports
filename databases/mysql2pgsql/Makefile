# Created by: Pete Fritchman <petef@databits.net>
# $FreeBSD$

PORTNAME=	mysql2pgsql
PORTVERSION=	1.2
PORTEPOCH=	1
CATEGORIES=	databases
MASTER_SITES=	http://pgfoundry.org/frs/download.php/1535/
DISTNAME=	${PORTNAME}
EXTRACT_SUFX=	.perl

MAINTAINER=	klossalex@gmail.com
COMMENT=	Convert a MySQL dump to a PostgreSQL dump

PLIST_FILES=	bin/mysql2pgsql
USES=		perl5
NO_BUILD=	yes

NO_STAGE=	yes
do-extract:
	${MKDIR} ${WRKDIR}
	${CP} -p ${DISTDIR}/mysql2pgsql.perl ${WRKDIR}

do-install:
	${INSTALL_SCRIPT} ${WRKDIR}/mysql2pgsql.perl ${PREFIX}/bin/mysql2pgsql

.include <bsd.port.mk>
