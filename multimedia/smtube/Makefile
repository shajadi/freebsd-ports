# Created by: Pawel Pekala <pawel@FreeBSD.org>
# $FreeBSD$

PORTNAME=	smtube
PORTVERSION=	1.8
CATEGORIES=	multimedia
MASTER_SITES=	SF/smplayer/SMTube/${PORTVERSION}/

MAINTAINER=	pawel@FreeBSD.org
COMMENT=	SMPlayer YouTube browser

RUN_DEPENDS=	${LOCALBASE}/bin/smplayer:${PORTSDIR}/multimedia/smplayer

USE_BZIP2=	yes
USES=		gmake
ALL_TARGET=	#empty
USE_QT4=	linguist_build moc_build qmake_build rcc_build uic_build
QMAKEFLAGS+=	QMAKE_CXXFLAGS_RELEASE=""
INSTALLS_ICONS=	yes

PORTDOCS=	*

OPTIONS_DEFINE=	DOCS

post-patch:
	@${REINPLACE_CMD} -e 's|qmake|${QMAKE} ${QMAKEFLAGS}|' \
		-e 's|lrelease|${QT_PREFIX}/bin/lrelease-qt4|g' \
		-e 's|PREFIX=/usr/local|PREFIX=${PREFIX}|g' \
		-e 's|$$(PREFIX)/share/smtube|${DATADIR}|g' \
		-e 's|$$(PREFIX)/share/doc/smtube|${DOCSDIR}|' \
		-e 's| make| ${GMAKE}|' \
		${WRKSRC}/Makefile

.include <bsd.port.mk>
