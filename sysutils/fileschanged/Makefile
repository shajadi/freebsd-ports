# Created by: Konstantin Reznichenko <kot@premierbank.dp.ua>
# $FreeBSD$

PORTNAME=	fileschanged
PORTVERSION=	0.6.5
PORTREVISION=	1
CATEGORIES=	sysutils
MASTER_SITES=	SF

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Utility that reports when files have been altered

BUILD_DEPENDS=	${LOCALBASE}/include/argp.h:${PORTSDIR}/devel/argp-standalone \
		help2man:${PORTSDIR}/misc/help2man

GNU_CONFIGURE=	yes
NO_STAGE=	yes
USE_GMAKE=	yes
USE_FAM=	yes
CONFIGURE_ENV+=	LIBS="-largp"
CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib
CONFIGURE_ARGS=	--datadir=${PREFIX}/share/doc --disable-nls

INFO=		fileschanged
MAN1=		fileschanged.1
PORTDOCS=	AUTHORS ChangeLog INSTALL NEWS README
PLIST_FILES=	bin/fileschanged

.if !defined(NOPORTDOCS)
post-install:
	${MKDIR} ${DOCSDIR}
.for DOCFILE in ${PORTDOCS}
	${INSTALL_DATA} ${WRKSRC}/${DOCFILE} ${DOCSDIR}
.endfor
.endif

.include <bsd.port.mk>
