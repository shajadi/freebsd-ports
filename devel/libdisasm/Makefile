# Created by: Lutz Boehne <lboehne@damogran.de>
# $FreeBSD$

PORTNAME=	libdisasm
PORTVERSION=	0.23
CATEGORIES=	devel
MASTER_SITES=	SF/bastard/${PORTNAME}/${PORTVERSION}

MAINTAINER=	bf@FreeBSD.org
COMMENT=	The Bastard Disassembly Environment x86 disassembler library and CLI

GNU_CONFIGURE=	yes
USE_GMAKE=	yes
USE_LDCONFIG=	yes
ONLY_FOR_ARCHS=	i386 amd64

.ifndef(NOPORTDOCS)
PORTDOCS=	libdisasm.txt
.endif

MAN1=	x86dis.1
MAN3=	x86_disasm.3 x86_format_insn.3 x86_init.3
MAN7=	libdisasm.7

NO_STAGE=	yes
post-install:
.ifndef(NOPORTDOCS)
	${MKDIR} ${DOCSDIR}
.for i in ${PORTDOCS}
	${INSTALL_DATA} ${WRKSRC}/doc/${i} ${DOCSDIR}
.endfor
.endif

.include <bsd.port.mk>
