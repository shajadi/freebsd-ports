# Created by: fenner
# $FreeBSD$

PORTNAME=	xplot
PORTVERSION=	0.90.7.1
PORTREVISION=	3
CATEGORIES=	math graphics net
MASTER_SITES=	http://www.xplot.org/xplot/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	X11 plotting package

USES=		perl5
USE_XORG=	x11
USE_PERL5=	run
GNU_CONFIGURE=	yes

MAN1=		tcpdump2xplot.1 xplot.1
PORTDOCS=	README README.tcp_plots
PLIST_FILES=	bin/tcpdump2xplot bin/tcpdump2xplot.pl bin/xplot

NO_STAGE=	yes
post-patch:
	@${REINPLACE_CMD} -e \
		'/INSTALL/s|2xplot$$|2xplot.pl|' ${WRKSRC}/Makefile.in

post-install:
	${LN} -sf tcpdump2xplot.pl ${PREFIX}/bin/tcpdump2xplot
.if !defined(NOPORTDOCS)
	@${MKDIR} ${DOCSDIR}
.for doc in ${PORTDOCS}
	${INSTALL_DATA} ${WRKSRC}/${doc} ${DOCSDIR}
.endfor
.endif

.include <bsd.port.mk>
