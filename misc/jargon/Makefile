# Created by: moeding
# $FreeBSD$

PORTNAME=	jargon
PORTVERSION=	4.4.7
CATEGORIES=	misc
MASTER_SITES=	http://www.catb.org/~esr/jargon/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	The famous jargon file

NO_BUILD=	yes

DATADIR=	${PREFIX}/share/jargon

NO_STAGE=	yes
post-extract:
	(cd ${WRKSRC}; \
	 ${RM} -rf html/graphics/.xvpics graphics/.xvpics \
		html/letters.html~ html/online-preface.html~)

do-install:
	${MKDIR} ${DATADIR}
	(cd ${WRKSRC}; ${PAX} -rw . ${DATADIR})
	${CHOWN} -R ${SHAREOWN}:${SHAREGRP} ${DATADIR}

.include <bsd.port.mk>
