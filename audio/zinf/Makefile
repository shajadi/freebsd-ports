# Created by: Roman Shterenzon <roman@xpert.com>
# $FreeBSD$

PORTNAME=	zinf
PORTVERSION=	2.2.5
PORTREVISION=	18
CATEGORIES=	audio ipv6
MASTER_SITES=	SF

MAINTAINER=	ports@FreeBSD.org
COMMENT=	GTK-based MP3 player

LIB_DEPENDS=	id3-3.8.3:${PORTSDIR}/audio/id3lib \
		gdbm.4:${PORTSDIR}/databases/gdbm

USES=		pathfix gettext gmake perl5
NO_STAGE=	yes
USE_GNOME=	gtk20 lthack
WANT_GNOME=	yes
GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--enable-ipv6 \
		--disable-arts

CPPFLAGS+=	-I${LOCALBASE}/include ${PTHREAD_CFLAGS}
LDFLAGS+=	-L${LOCALBASE}/lib ${PTHREAD_LIBS}

.include <bsd.port.pre.mk>

.if ${ARCH} == "i386"
BUILD_DEPENDS+=	nasm:${PORTSDIR}/devel/nasm
CPPFLAGS+=	"-D_M_IX86"
.else
CONFIGURE_ARGS+=	--disable-x86opts
.endif

.if ${ARCH} == "alpha"
CPPFLAGS+=	"-D_M_ALPHA"
.endif

.if ${HAVE_GNOME:Mesound}!="" || defined(WITH_ALL_PLUGINS)
USE_GNOME+=	esound
PLIST_SUB+=	ESOUND=""
.else
CONFIGURE_ARGS+=	--disable-esd
PLIST_SUB+=	ESOUND="@comment "
.endif

.if !defined(WITHOUT_VORBIS) || defined(WITH_ALL_PLUGINS)
LIB_DEPENDS+=	vorbis.4:${PORTSDIR}/audio/libvorbis
PLIST_SUB+=	VORBIS=""
.else
CONFIGURE_ARGS+=	--disable-vorbis
PLIST_SUB+=	VORBIS="@comment "
.endif

pre-everything::
	@${ECHO_MSG}
	@${ECHO_MSG} "You may use the following build options:"
	@${ECHO_MSG}
	@${ECHO_MSG} "WITHOUT_GNOME=esound	do NOT build with esd support"
	@${ECHO_MSG} "WITHOUT_VORBIS=yes	do NOT build with Ogg/Vorbis codec plugin"
	@${ECHO_MSG}
	@${ECHO_MSG} "WITH_ALL_PLUGINS=yes	build with all plugins"
	@${ECHO_MSG}

post-patch:
	@${REINPLACE_CMD} -e 's|echo aout|echo elf|' ${WRKSRC}/configure
	@${REINPLACE_CMD} -e 's|Player::||' ${WRKSRC}/base/include/player.h

post-install:
	@${MKDIR} ${PREFIX}/etc/sdr/plugins
	${INSTALL_DATA} ${FILESDIR}/sdr2.plugin.S100.audio.rtp.mpa.zinf \
		${PREFIX}/etc/sdr/plugins
	${CHOWN} -R ${SHAREOWN}:${SHAREGRP} ${DATADIR}

.include <bsd.port.post.mk>
