# Created by: pat
# $FreeBSD$

PORTNAME=	wmmaiload
PORTVERSION=	2.2.1
PORTREVISION=	3
CATEGORIES=	mail windowmaker
MASTER_SITES=	http://tnemeth.free.fr/projets/programmes/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Incoming mail monitor dockapp with a similar look to wmcpuload

USES=		gmake pkgconfig
USE_XORG=	xpm
USE_OPENSSL=	yes
HAS_CONFIGURE=	yes
CONFIGURE_ARGS=	--prefix=${PREFIX}
MAKE_ARGS=	CC="${CC}" \
		CFLAGS="${CFLAGS} -D_GNU_SOURCE ${PTHREAD_CFLAGS}" \
		CPPFLAGS="-I${LOCALBASE}/include" \
		LDFLAGS="-L${LOCALBASE}/lib" \
		LIB_SSL="-lssl -lcrypto" \
		LIB_THREADS="${PTHREAD_LIBS}" \
		DEBUG_CFLAGS="-I${OPENSSLINC}" \
		DEBUG_LDFLAGS="-L${OPENSSLLIB}"

MAN1=		${PORTNAME}.1 ${PORTNAME}-config.1
PLIST_FILES=	bin/wmmaiload bin/wmmaiload-config

.if defined(WITH_GTK2)
USE_GNOME+=	gtk20
MAKE_ARGS+=	GTK_CFLAGS="pkg-config --cflags gtk+-2.0" \
		GTK_LIBS="pkg-config --libs gtk+-2.0"
.else
USE_GNOME+=	gtk12
MAKE_ARGS+=	GTK_CFLAGS="pkg-config --cflags gtk+" \
		GTK_LIBS="pkg-config --libs gtk+"
.endif

NO_STAGE=	yes
post-patch:
.for i in wmmaiload/Init.make
	@${REINPLACE_CMD} -e 's|-L/usr/X11R6/lib||g' ${WRKSRC}/${i}
.endfor
.for i in wmmaiload/checkthread.c
	@${REINPLACE_CMD} -e 's|isnumber(|isnum(|g' ${WRKSRC}/${i}
.endfor
.for i in wmmaiload/main.h
	@${REINPLACE_CMD} -e '/time\.h>/d' ${WRKSRC}/${i}
.endfor
.for i in wmmaiload-config/Init.make
	@${REINPLACE_CMD} -e 's|gtk-config --cflags|$${GTK_CFLAGS}|g ; \
		 s|gtk-config --libs|$${GTK_LIBS}|g' ${WRKSRC}/${i}
.endfor
.for i in wmmaiload-config/dialogs.c wmmaiload-config/mainwindow.c \
	wmmaiload-config/popedit.c
	@${REINPLACE_CMD} -e 's|_widget_draw_default|_widget_queue_draw|g ; \
		 s|remove;|rm;|g ; \
		 s|remove,|rm,|g ; \
		 s|remove =|rm =|g ; \
		 s|PACKAGE"-config"|PACKAGE|g' ${WRKSRC}/${i}
.endfor

do-install:
.for i in wmmaiload wmmaiload-config
	${INSTALL_PROGRAM} ${WRKSRC}/${i}/${i} ${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/doc/${i}.1 ${MANPREFIX}/man/man1
.endfor

.include <bsd.port.pre.mk>

.if ${ARCH} == "ia64" || ${ARCH} == "powerpc" || ${ARCH} == "sparc64"
BROKEN=		Does not compile on ia64, powerpc, or sparc64
.endif

.include <bsd.port.post.mk>
