# Created by: David Naylor <naylor.b.david@gmail.com>
# $FreeBSD$

PORTNAME=	wine-gecko
DISTVERSION=	1.4
CATEGORIES=	emulators
MASTER_SITES=	SF/wine/Wine%20Gecko/${DISTVERSION}
DISTNAME=	wine_gecko-${DISTVERSION}-x86
EXTRACT_SUFX=	.msi
EXTRACT_ONLY=

MAINTAINER=	dbn@FreeBSD.org
COMMENT=	Gecko Layout Engine for Wine (HTML support)

LICENSE=	MPL GPLv2 GPLv3 LGPL21 LGPL3
LICENSE_COMB=	multi

PORTSCOUT=	ignore:1	# for newer versions see emulators/wine-gecko-devel

NO_BUILD=	yes
PLIST_SUB+=	GECKO_VERSION="${DISTVERSION}"
DATADIR=	${PREFIX}/share/wine
PLIST_FILES=	%%DATADIR%%/gecko/wine_gecko-%%GECKO_VERSION%%-x86.msi
PLIST_DIRSTRY=	%%DATADIR%%/gecko %%DATADIR%%

NO_STAGE=	yes
do-install:
	@${MKDIR} ${DATADIR}/gecko
	${INSTALL_DATA} ${DISTDIR}/wine_gecko-${DISTVERSION}-x86.msi \
		${DATADIR}/gecko

.include <bsd.port.mk>
