# Created by: Dmitry Shulgachik <legh@legh.ru>
# $FreeBSD$

PORTNAME=	jx
PORTVERSION=	1.23
CATEGORIES=	sysutils
MASTER_SITES=	http://legh.ru/wp-content/uploads/jx/

MAINTAINER=	legh@legh.ru
COMMENT=	Wrapper to jexec with more feature in interpreting jail id

USES=		perl5
NO_BUILD=	yes
USE_PERL5=	run

PLIST_FILES=	bin/${PORTNAME}

MAN1=		jx.1
MANCOMPRESSED=	yes

OPTIONS_DEFINE=	CONFIG
CONFIG_DESC=	Enable custom config (recuire Config::General)

NO_STAGE=	yes
.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MCONFIG}
RUN_DEPENDS=	p5-Config-General>=0:${PORTSDIR}/devel/p5-Config-General
PLIST_FILES+=	etc/${PORTNAME}.cfg.sample
.endif

post-patch:
.if ${PORT_OPTIONS:MCONFIG}
	${REINPLACE_CMD} -e 's/use constant use_config => 0;/use constant use_config => 1;/' ${WRKSRC}/${PORTNAME}.pl
.endif

do-install:
	${INSTALL_SCRIPT} ${WRKSRC}/${PORTNAME}.pl ${PREFIX}/bin/${PORTNAME}
	${INSTALL_MAN} ${WRKSRC}/${PORTNAME}.1.gz ${PREFIX}/man/man1/${PORTNAME}.1.gz
.if ${PORT_OPTIONS:MCONFIG}
	${INSTALL_DATA} ${WRKSRC}/${PORTNAME}.cfg.sample ${PREFIX}/etc/${PORTNAME}.cfg.sample
.endif

.include <bsd.port.mk>
