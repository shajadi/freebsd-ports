# Created by: Kris Kennaway <kkennawa@physics.adelaide.edu.au>
# $FreeBSD$

PORTNAME=	linux-realplayer
DISTVERSION=	10.0.9.809-20070726
PORTREVISION=	4
CATEGORIES=	multimedia audio linux
MASTER_SITES=	http://client-software.real.com/free/unix/:player \
		http://mirror.therek.net/freebsd/distfiles/mplayer/:codecs \
		SF/mplayer-tru/mplayer-codecs/20040704:codecs \
		ftp://fr2.rpmfind.net/linux/sourceforge/m/mp/mplayer-tru/mplayer-codecs/20040704/:codecs \

DISTFILES=	RealPlayer10GOLD.rpm:player \
		mplayer-codecs-linux-real-20040626-1.i386.rpm:codecs

MAINTAINER=	multimedia@FreeBSD.org
COMMENT=	Linux RealPlayer 10 from RealNetworks

WRKSRC=		${WRKDIR}/usr/local/RealPlayer
ONLY_FOR_ARCHS=	i386 amd64
USE_LINUX=	yes
USE_LINUX_APPS=	gtk2 xorglibs
RESTRICTED=	Redistribution not allowed
NO_BUILD=	yes
WANT_GNOME=	yes

RADIR=		${PREFIX}/lib/RealPlayer
PLUGINSDIR=	${PREFIX}/lib/linux-mozilla/plugins
RABINDIR=	${PREFIX}/bin

NO_STAGE=	yes
.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MNLS}
PLIST_SUB+=	NLS="" LINUXBASE="${LINUXBASE}"
.else
PLIST_SUB+=	NLS="@comment "
.endif

.include <bsd.port.pre.mk>

.if exists(${LOCALBASE}/share/icons)
WITH_ICONS=	yes
PLIST_SUB+=	ICONS=""
.else
PLIST_SUB+=	ICONS="@comment "
.endif

.if ${HAVE_GNOME:Mgnomehier}!=""
WITH_GNOME=	yes
PLIST_SUB+=	GNOME=""
.else
PLIST_SUB+=	GNOME="@comment "
.endif

.if defined(WITH_ICONS) || defined(WITH_GNOME)
PLIST_SUB+=	X11=""
.else
PLIST_SUB+=	X11="@comment "
.endif

do-extract:
	@${MKDIR} ${WRKDIR}
	@for f in ${_DISTFILES}; do\
		cd ${WRKDIR}; ${TAR} -xf ${DISTDIR}/$$f ; \
	done

post-patch:
	@${SED} 's|/usr/local|${PREFIX}|' \
		< ${FILESDIR}/realplay > ${WRKSRC}/realplay

do-install:
	@${MKDIR} ${RADIR}
	${INSTALL_DATA} ${WRKSRC}/LICENSE ${WRKSRC}/README ${RADIR}
	${INSTALL_PROGRAM} ${WRKSRC}/realplay.bin ${RADIR}
	${BRANDELF} -t Linux ${RADIR}/realplay.bin
.for dir in codecs common lib plugins share/default share/realplay
	@${MKDIR} ${RADIR}/${dir}
	${INSTALL_DATA} ${WRKSRC}/${dir}/* ${RADIR}/${dir}
.endfor

# Extra codecs from the RealPlayer-9 -- no longer shipped by Real,
# but still in use by major content providers, such as Amazon:
.for c in dnet ddnt
	${INSTALL_DATA} ${WRKDIR}/usr/lib/codecs/$c.so.6.0	\
		${RADIR}/codecs/
	${LN} -sf $c.so.6.0 ${RADIR}/codecs/$c.so
.endfor

.if ${PORT_OPTIONS:MNLS}
	@${MKDIR} ${RADIR}/share/locale
	${CP} -Rp ${WRKSRC}/share/locale/* ${RADIR}/share/locale
	${CHOWN} -R ${SHAREOWN}:${SHAREGRP} ${RADIR}/share/locale
.for c in de es fr hi it ja ko pl pt_BR zh_CN zh_TW
	${LN} -sf ${RADIR}/share/locale/${c}/player.mo \
		${LINUXBASE}/usr/share/locale/${c}/LC_MESSAGES/realplay.mo
.endfor
.endif

	@${MKDIR} ${PLUGINSDIR}
	${INSTALL_DATA} ${WRKSRC}/mozilla/* ${PLUGINSDIR}

	@${MKDIR} ${PREFIX}/bin
	${INSTALL_SCRIPT} ${WRKSRC}/realplay ${PREFIX}/bin

.if defined(WITH_ICONS)
. for size in 16x16 32x32 48x48 192x192
	@${MKDIR} ${LOCALBASE}/share/icons/hicolor/${size}/apps
	${INSTALL_DATA} ${WRKSRC}/share/icons/realplay_${size}.png \
		${LOCALBASE}/share/icons/hicolor/${size}/apps
. endfor
. for size in 48x48 192x192
	@${MKDIR} ${LOCALBASE}/share/icons/hicolor/${size}/mimetypes
	${INSTALL_DATA} ${WRKSRC}/share/icons/mime-*_${size}.png \
		${LOCALBASE}/share/icons/hicolor/${size}/mimetypes
. endfor
.endif

.if defined(WITH_GNOME)
	@${MKDIR} ${LOCALBASE}/share/pixmaps
	${INSTALL_DATA} ${WRKSRC}/share/realplay.png \
		${LOCALBASE}/share/pixmaps

	@${MKDIR} ${LOCALBASE}/share/applications
	${INSTALL_DATA} ${WRKSRC}/share/realplay.desktop \
		${LOCALBASE}/share/applications

	@${MKDIR} ${LOCALBASE}/share/application-registry
	${INSTALL_DATA} ${WRKSRC}/share/realplay.applications \
		${LOCALBASE}/share/application-registry

	@${MKDIR} ${LOCALBASE}/share/mime-info
	${INSTALL_DATA} ${WRKSRC}/share/realplay.keys ${WRKSRC}/share/realplay.mime \
		${LOCALBASE}/share/mime-info
.endif

.include <bsd.port.post.mk>
