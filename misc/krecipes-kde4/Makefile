# $FreeBSD$

PORTNAME=	krecipes
DISTVERSION=	2.0-beta2
PORTREVISION=	2
CATEGORIES=	misc kde
MASTER_SITES=	SF/${PORTNAME}/${PORTNAME}/${DISTVERSION}

MAINTAINER=	jhale@FreeBSD.org
COMMENT=	KDE4 recipe database

LICENSE=	GPLv2

USES=		cmake gettext
USE_QT4=	moc_build qmake_build rcc_build uic_build
USE_KDE4=	automoc4 kdeprefix kdelibs qimageblitz sharedmime

NO_STAGE=	yes

OPTIONS_MULTI=		DB
OPTIONS_MULTI_DB=	SQLITE MYSQL PGSQL
OPTIONS_DEFAULT=	SQLITE

SQLITE_USE=		SQLITE=yes \
			QT4=sql-sqlite3_run
SQLITE_CMAKE_OFF=	-DWITH_Sqlite:BOOL=OFF

MYSQL_USE=		MYSQL=yes \
			QT4=sql-mysql_run

PGSQL_USE=		PGSQL=yes \
			QT4=sql-pgsql_run

.include <bsd.port.mk>
