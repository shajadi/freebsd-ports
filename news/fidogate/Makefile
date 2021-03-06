# $FreeBSD$

PORTNAME=	fidogate
PORTVERSION=	4.4.10
CATEGORIES=	news mail
MASTER_SITES=	SF \
		ftp://ftp.fu-berlin.de/unix/news/fidogate/

MAINTAINER=	dinoex@FreeBSD.org
COMMENT=	Fido-Internet Gateway and Tosser

.if !defined(WITHOUT_IFCICO)
RUN_DEPENDS=	${LOCALBASE}/libexec/ifmail/ifcico:${PORTSDIR}/news/ifmail
.endif

MAKE_JOBS_UNSAFE=	yes
NO_STAGE=	yes

USES=		gmake perl5

DOCLIST=	fidogate.texi fidogate.txt gatebau94.txt kludge-rfc.doc \
		msgid.doc qmail.txt texinfo.tex dirs.html index.html \
		template.html fido howto misc rfc gatebau/msgid.sgml \
		gatebau/msgid.tex gatebau/msgid.txt

.include <bsd.port.pre.mk>

pre-configure:
	${TOUCH} ${WRKSRC}/doc/fidogate.info
	${RM} -f ${WRKSRC}/doc/fidogate.info-?
	${RM} -f ${WRKSRC}/doc/fidogate.txt
	@${REINPLACE_CMD} -e "s|.{PREFIX}|${PREFIX}|g" \
		 -e "s|.{LOCALBASE}|${LOCALBASE}|g" \
		 -e "s|^CC|#CC|" ${WRKSRC}/config.make
.if defined(FIDOGATE_RUNAS)
	@${REINPLACE_CMD} -e "s|OWNER.*= news|OWNER		= ${FIDOGATE_RUNAS}|" \
		${WRKSRC}/config.make
.endif
.if defined(NOPORTDOCS)
	@${REINPLACE_CMD} -e "s|test doc|test|" \
		-e "s|cp ANNOUNCE|#cp ANNOUNCE|" \
		 ${WRKSRC}/Makefile
	@${REINPLACE_CMD} -e "s|run www|run|" ${WRKSRC}/scripts/Makefile
.endif

pre-install:
	${MKDIR} ${PREFIX}/libexec/fidogate
.if !defined(NOPORTDOCS)
	${MKDIR} ${DOCSDIR}/html ${DOCSDIR}/info ${DOCSDIR}/fido \
		${DOCSDIR}/howto ${DOCSDIR}/misc ${DOCSDIR}/gatebau
.endif

post-install:
.if !defined(NOPORTDOCS)
	${MKDIR} ${DOCSDIR}
	@${TAR} -C ${WRKSRC}/doc -cf - ${DOCLIST} | ${TAR} -C ${DOCSDIR} -xf -
.endif
.if !defined(NOPORTEXAMPLES)
	${MKDIR} ${EXAMPLESDIR}
	@${TAR} -C ${WRKSRC}/examples -cf - . | ${TAR} -C ${EXAMPLESDIR} -xf -
.endif

.include <bsd.port.post.mk>
