# Created by: Jing-Tang Keith Jang (keith@FreeBSD.org)
# $FreeBSD$

PORTNAME=	latex-cjk
PORTVERSION=	4.8.2
PORTREVISION=	6
CATEGORIES=	print chinese japanese korean
MASTER_SITES=	http://cjk.ffii.org/ \
		ftp://freebsd.csie.ntu.edu.tw/users/rafan/
DISTNAME=	cjk-${PORTVERSION}
DISTFILES=	${DISTNAME}.tar.gz

MAINTAINER=	rafan@FreeBSD.org
COMMENT=	A LaTeX2e macro package which enables the use of CJK scripts

RUN_DEPENDS=	zh-arphicttf>=0:${PORTSDIR}/chinese/arphicttf \
		ttf2pk:${PORTSDIR}/print/freetype-tools
BUILD_DEPENDS:=	${RUN_DEPENDS} \
		${LOCALBASE}/share/ttf2pt1/maps/cugb.map:${PORTSDIR}/chinese/ttf2pt1 \
		ttf2pt1:${PORTSDIR}/print/ttf2pt1
LIB_DEPENDS=	ttf:${PORTSDIR}/print/freetype

USE_GMAKE=	yes
USE_TEX=	tetex latex

MAN1=		bg5conv.1 cef5conv.1 cefconv.1 cefsconv.1 extconv.1 \
		hbf2gf.1 sjisconv.1

SUB_FILES=	pkg-deinstall pkg-install pkg-message
SUB_LIST=	TEXMFDIR=${TEXMFDIR_REL}
PLIST_SUB=	TEXMFDIR=${TEXMFDIR_REL}

INSTALL_DIR=	${INSTALL} -d -m 0755 -o root -g wheel

WRKFONTDIR=	${WRKDIR}/fonts

OPTIONS_DEFINE=	CCMAP DVIPDFMX UTF8ARPHIC DOCS NLS
OPTIONS_DEFAULT=	CCMAP DVIPDFMX UTF8ARPHIC
CCMAP_DESC=	CCT CCMap package (for PDFTeX's CID support)
DVIPDFMX_DESC=	Install and configure DVIPDFMx for CJK
UTF8ARPHIC_DESC=	Arphic free fonts in UTF-8 (no Type 1)

NO_STAGE=	yes
.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MCCMAP}
MASTER_SITES+=	http://ftp.intron.ac/pub/FreeBSD/local-distfiles/:cct
DISTFILES+=	cct-20060219-ccmap.tar.gz:cct
PLIST_SUB+=	CCMAP=""
.else
PLIST_SUB+=	CCMAP="@comment "
.endif

.if ${PORT_OPTIONS:MDVIPDFMX}
USE_TEX+=	dvipdfmx
# Configuration is done by "pkg-install"
.endif

.if ${PORT_OPTIONS:MUTF8ARPHIC}
PLIST_SUB+=	UTF8ARPHIC=""
.else
PLIST_SUB+=	UTF8ARPHIC="@comment "
.endif

post-extract:
	@${RM} -f ${WRKSRC}/Makefile

post-patch:
	# be compatible with Debian
	@${CP} -p ${WRKSRC}/texinput/Bg5/c00kai.fd ${WRKSRC}/texinput/Bg5/c00bkai.fd
	@${REINPLACE_CMD} -e 's,c00kai.fd,c00bkai.fd,; s,{kai},{bkai},' ${WRKSRC}/texinput/Bg5/c00bkai.fd
.if ${PORT_OPTIONS:MCCMAP}
	@${REINPLACE_CMD} -e 's,/usr/local,${LOCALBASE},' ${WRKDIR}/ccmap/make.sh
.endif
	@${FIND} -E ${WRKSRC} ${WRKDIR}/ccmap -regex '.*.(orig|bak)' -delete

pre-su-install:
	${SH} ${PKGINSTALL} ${PKGNAME} PRE-INSTALL

post-install:
.if ${PORT_OPTIONS:MDOCS}
	${MKDIR} ${DOCSDIR}
	(cd ${WRKSRC}/doc && ${COPYTREE_SHARE} \* ${DOCSDIR})
.endif
.if ${PORT_OPTIONS:MNLS}
	${MKDIR} ${EXAMPLESDIR}
	(cd ${WRKSRC}/examples && ${COPYTREE_SHARE} \* ${EXAMPLESDIR})
.endif

# Install Arphic fonts for Type 3 or DVIPDFMx
	@${ECHO_CMD} "Generating Arphic fonts' TFM files..."
	${SETENV} LOCALBASE=${LOCALBASE} ${SH} ${SCRIPTDIR}/installtfm.sh \
		arb5sung arb5sung.ttf UBig5
	${SETENV} LOCALBASE=${LOCALBASE} ${SH} ${SCRIPTDIR}/installtfm.sh \
		arb5kai arb5kai.ttf UBig5
	${SETENV} LOCALBASE=${LOCALBASE} ${SH} ${SCRIPTDIR}/installtfm.sh \
		argbsung argbsung.ttf UGB
	${SETENV} LOCALBASE=${LOCALBASE} ${SH} ${SCRIPTDIR}/installtfm.sh \
		argbkai argbkai.ttf UGB

# Install Arphic fonts for Type 1 and PDFTeX
	@${ECHO_CMD} "Generating Type 1 Arphic fonts..."
	${MKDIR} ${WRKFONTDIR}
	${ECHO} -n "" > ${WRKFONTDIR}/CJK-type1.map
	${ECHO} -n "" > ${WRKFONTDIR}/CJK-pdftex.map
	cd ${WRKFONTDIR} && ${SETENV} LOCALBASE=${LOCALBASE} ${SH} \
		${SCRIPTDIR}/installt1enc.sh arb5sung arb5sung.ttf Bg5
	cd ${WRKFONTDIR} && ${SETENV} LOCALBASE=${LOCALBASE} ${SH} \
		${SCRIPTDIR}/installt1enc.sh arb5kai arb5kai.ttf Bg5
	cd ${WRKFONTDIR} && ${SETENV} LOCALBASE=${LOCALBASE} ${SH} \
		${SCRIPTDIR}/installt1enc.sh argbsung argbsung.ttf GB
	cd ${WRKFONTDIR} && ${SETENV} LOCALBASE=${LOCALBASE} ${SH} \
		${SCRIPTDIR}/installt1enc.sh argbkai argbkai.ttf GB

# Install package ccmap
.if ${PORT_OPTIONS:MCCMAP}
	@${ECHO_CMD} "Installing ccmap..."
	${MKTEXLSR}
	cd ${WRKDIR}/ccmap && ${SH} make.sh && ${COPYTREE_SHARE} \* ${CJKDIR}/ccmap
.endif

# Install Arphic fonts in Unicode separation for Type 3 or DVIPDFMx
.if ${PORT_OPTIONS:MUTF8ARPHIC}
	@${ECHO_CMD} "Generating Arphic fonts' TFM files in Unicode..."
	${SETENV} LOCALBASE=${LOCALBASE} ${SH} ${SCRIPTDIR}/installtfm.sh \
		arb5sungu arb5sung.ttf Unicode
	${SETENV} LOCALBASE=${LOCALBASE} ${SH} ${SCRIPTDIR}/installtfm.sh \
		arb5kaiu arb5kai.ttf Unicode
	${SETENV} LOCALBASE=${LOCALBASE} ${SH} ${SCRIPTDIR}/installtfm.sh \
		argbsungu argbsung.ttf Unicode
	${SETENV} LOCALBASE=${LOCALBASE} ${SH} ${SCRIPTDIR}/installtfm.sh \
		argbkaiu argbkai.ttf Unicode
.endif

# Mapping files for updmap(1) and PDFTeX
	${INSTALL_DIR} ${CJKMAPDIR}
	${INSTALL_DATA} ${WRKFONTDIR}/CJK-type1.map ${CJKMAPDIR}
	${INSTALL_DATA} ${WRKFONTDIR}/CJK-pdftex.map ${CJKMAPDIR}

# Final
	${SH} ${PKGINSTALL} ${PKGNAME} POST-INSTALL

	${CAT} ${PKGMESSAGE}

.include "../../print/latex-cjk/Makefile.common"
.include <bsd.port.mk>
