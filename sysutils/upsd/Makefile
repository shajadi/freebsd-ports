# Created by: alexis
# $FreeBSD$

PORTNAME=	upsd
PORTVERSION=	2.0.1.6
PORTREVISION=	1
CATEGORIES=	sysutils
MASTER_SITES=	http://www.mavetju.org/download/adopted/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	APC Smart UPS Monitoring Daemon

WRKSRC=		${WRKDIR}/upsd-2.0

PLIST_FILES=	sbin/upsd etc/upsd.conf etc/rc.d/upsd.sh

NO_STAGE=	yes
pre-build:
	@${MV} ${WRKSRC}/config.h ${WRKSRC}/conf.h.orig
	@${SED} -e "s!@prefix@!${PREFIX}!g" ${WRKSRC}/conf.h.orig > ${WRKSRC}/conf.h
	@${REINPLACE_CMD} -e 's/NOMAN/NO_MAN/g' ${WRKSRC}/Makefile

post-install:
	@if [ ! -f ${PREFIX}/etc/rc.d/upsd.sh ]; then \
		${ECHO_MSG} "Installing ${PREFIX}/etc/rc.d/upsd.sh startup file."; \
		${INSTALL_SCRIPT} -m 751 ${FILESDIR}/upsd.sh ${PREFIX}/etc/rc.d/upsd.sh; \
	fi
	if [ ! -f ${PREFIX}/etc/upsd.conf ] ; then \
		${INSTALL} -c -o ${BINOWN} -g ${BINGRP} -m 644 \
			${FILESDIR}/upsd.conf ${PREFIX}/etc/upsd.conf; \
	fi

.include <bsd.port.mk>
