# Created by: ijliao
# $FreeBSD$

PORTNAME=	sloth
PORTVERSION=	1.1.0
CATEGORIES=	sysutils
MASTER_SITES=	http://www.sourcefiles.org/Utilities/Miscellaneous/ \
		http://T32.TecNik93.com/FreeBSD/others_ports/${PORTNAME}${PKGNAMESUFFIX}/sources/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Slow down a process

GNU_CONFIGURE=	yes

MAN1=		sloth.1
PLIST_FILES=	bin/sloth

NO_STAGE=	yes
post-patch:
	@${REINPLACE_CMD} -e "s,wait.h,sys/wait.h,g" ${WRKSRC}/configure

.include <bsd.port.mk>
