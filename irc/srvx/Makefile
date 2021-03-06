# Created by: Walter Venable <weaseal@hotmail.com>
# $FreeBSD$

PORTNAME=	srvx
PORTVERSION=	1.3.1
CATEGORIES=	irc net
MASTER_SITES=	SF

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Services for ircu P10 protocol networks

LICENSE=	GPLv2

GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--without-getopt

SUB_FILES=	pkg-message

PLIST_FILES=	bin/srvx etc/srvx.conf.example etc/sockcheck.conf.example
PORTDOCS=	*

OPTIONS_DEFINE=	BAHAMUT DEBUG
OPTIONS_DEFAULT=	BAHAMUT
BAHAMUT_DESC=	Enable Bahamut protocol (P10 is default)

DEBUG_CONFIGURE_ON=	--enable-debug
BAHAMUT_CONFIGURE_ON=	--with-protocol=bahamut

NO_STAGE=	yes
.include <bsd.port.options.mk>

post-patch:
	@${REINPLACE_CMD} -e 's|srvx\.conf|${PREFIX}/etc/srx.conf|' \
		${WRKSRC}/src/main.c

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/src/srvx ${PREFIX}/bin
	${INSTALL_DATA} ${WRKSRC}/*.conf.example ${PREFIX}/etc
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/src/*.help ${DOCSDIR}
.endif
	@${ECHO_MSG}
	@${CAT} ${PKGMESSAGE}
	@${ECHO_MSG}

.include <bsd.port.mk>
