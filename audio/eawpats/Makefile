# Created by: Jonathan Lennox <lennox@cs.columbia.edu>
# $FreeBSD$

PORTNAME=	eawpats
PORTVERSION=	12
PORTREVISION=	3
CATEGORIES=	audio
MASTER_SITES=	${MASTER_SITE_GENTOO}
MASTER_SITE_SUBDIR=	distfiles
DISTNAME=	eawpats12_full

MAINTAINER=	lennox@cs.columbia.edu
COMMENT=	Eric A. Welsh's collection of Gravis Ultrasound MIDI patches

RESTRICTED=	Some of the patches are marked no-commercial-use

NO_BUILD=	yes
NO_STAGE=	yes

PATCH_SUBDIRS=	ethnic mazpat/fx gsdrum08 gsdrum25 gsdrum40 gus power sfx wime
DOC_SUBDIRS=	ethnic gsdrum08 gsdrum25 gsdrum40 power wime

WRKSRC=		${WRKDIR}/${PORTNAME}
TIMIDITY_DATADIR=	${PREFIX}/share/timidity

post-patch:
	@${REINPLACE_CMD} -e 's|/home/user/eawpats|${DATADIR}|' ${WRKSRC}/linuxconfig/timidity.cfg

do-install:
	${MKDIR} ${DATADIR}
	${INSTALL_DATA} ${WRKSRC}/*.cfg ${WRKSRC}/*.pat ${WRKSRC}/*.ini ${DATADIR}
.for subdir in ${PATCH_SUBDIRS}
	${MKDIR} ${DATADIR}/${subdir}
	${INSTALL_DATA} ${WRKSRC}/${subdir}/*.pat ${DATADIR}/${subdir}
.endfor
	${MKDIR} ${TIMIDITY_DATADIR}
	${INSTALL_DATA} ${WRKSRC}/linuxconfig/timidity.cfg ${TIMIDITY_DATADIR}/timidity.cfg-eawpats
	[ -f ${TIMIDITY_DATADIR}/timidity.cfg ] || \
		${INSTALL_DATA} ${WRKSRC}/linuxconfig/timidity.cfg ${TIMIDITY_DATADIR}/timidity.cfg
.if !defined(NOPORTDOCS)
	${MKDIR} ${DOCSDIR}
	${INSTALL_MAN} ${WRKSRC}/*.txt ${WRKSRC}/*.hlp ${DOCSDIR}
.for subdir in ${DOC_SUBDIRS}
	${MKDIR} ${DOCSDIR}/${subdir}
	${INSTALL_MAN} ${WRKSRC}/${subdir}/*.txt ${DOCSDIR}/${subdir}
.endfor
.endif

.include <bsd.port.mk>
