# Created by: shige
# $FreeBSD$

PORTNAME=	eject
PORTVERSION=	1.5
PORTREVISION=	4
CATEGORIES=	sysutils
MASTER_SITES=	ftp://ports.jp.FreeBSD.org/pub/FreeBSD-jp/OD/ \
		ftp://ftp4.jp.FreeBSD.org/pub/FreeBSD-jp/OD/ \
		ftp://ftp.ics.es.osaka-u.ac.jp/pub/mirrors/FreeBSD-jp/OD/

MAINTAINER=	sylvio@FreeBSD.org
COMMENT=	Utility for ejecting media from CD or optical disk drive

PLIST_FILES=	sbin/eject
PORTDOCS=	README README-J

MAN1=		eject.1
MANCOMPRESSED=	yes

NO_STAGE=	yes
post-patch:
	${REINPLACE_CMD} -e 's,4555,555,' ${WRKSRC}/Makefile

post-install:
.if !defined(NOPORTDOCS)
	${MKDIR} ${DOCSDIR}
.for i in ${PORTDOCS}
	${INSTALL_DATA} ${WRKSRC}/${i} ${DOCSDIR}
.endfor
.endif
	@${CAT} ${PKGMESSAGE}

.include <bsd.port.mk>
