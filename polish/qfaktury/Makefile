# Created by: Piotr Rybicki (meritus@innervision.pl)
# $FreeBSD$

PORTNAME=	qfaktury
PORTVERSION=	0.6.2
PORTREVISION=	2
CATEGORIES=	polish deskutils
MASTER_SITES=	SF

MAINTAINER=	meritus@innervision.pl
COMMENT=	Polish invoicing desktop program

USE_QT4=	qmake_build uic_build moc_build rcc_build corelib gui xml qt3support

PORTDOCS=	ChangeLog.txt ReadMe.txt ReleaseNotes.txt TODO.txt

NO_STAGE=	yes
post-patch:
	@cd ${WRKSRC} && ${REINPLACE_CMD} -e 's|@PREFIX@|${PREFIX}|g' qfaktury.pro \
	QFaktury.desktop

pre-build:
	@cd ${WRKSRC} && ${QMAKE} -spec ${QMAKESPEC}

post-install:
.if !defined(NOPORTDOCS)
	@${MKDIR} ${DOCSDIR}
.for file in ${PORTDOCS}
	@${INSTALL_DATA} ${WRKSRC}/${file} ${DOCSDIR}
.endfor
.endif

.include <bsd.port.mk>
