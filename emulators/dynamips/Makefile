# Created by: Max Khon <fjoe@FreeBSD.org>
# $FreeBSD$

PORTNAME=	dynamips
DISTVERSION=	0.2.7
PORTREVISION=	2
CATEGORIES=	emulators
MASTER_SITES=	http://www.ipflow.utc.fr/dynamips/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Cisco 3600/7200 Simulator

LIB_DEPENDS=	elf.0:${PORTSDIR}/devel/libelf

USE_GMAKE=	yes
ALL_TARGET=	${PORTNAME} nvram_export
MAKE_ENV=	DYNAMIPS_ARCH=${DYNAMIPS_ARCH}\
		PTHREAD_CFLAGS=${PTHREAD_CFLAGS}\
		PTHREAD_LIBS=${PTHREAD_LIBS}
MAKE_JOBS_UNSAFE=	yes

PLIST_FILES=	bin/${PORTNAME} bin/nvram_export
.if !defined(NOPORTDOCS)
PORTDOCS=	README README.hypervisor
.endif
.if !defined(NO_INSTALL_MANPAGES)
MAN1=		${PORTNAME}.1 nvram_export.1
MAN7=		hypervisor_mode.7
.endif

NO_STAGE=	yes
.include <bsd.port.pre.mk>

.if ${ARCH} == "i386"
DYNAMIPS_ARCH=	"x86"
.elif ${ARCH} == "amd64"
DYNAMIPS_ARCH=	"amd64"
.else
DYNAMIPS_ARCH=	"nojit"
.endif

MAKE_ENV+=	HAS_POSIX_MEMALIGN=1

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/${PORTNAME} ${PREFIX}/bin
	${INSTALL_PROGRAM} ${WRKSRC}/nvram_export ${PREFIX}/bin
.if !defined(NOPORTDOCS)
	${MKDIR} ${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/README ${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/README.hypervisor ${DOCSDIR}
.endif
.if !defined(NO_INSTALL_MANPAGES)
	${INSTALL_MAN} ${WRKSRC}/${PORTNAME}.1 ${PREFIX}/man/man1
	${INSTALL_MAN} ${WRKSRC}/nvram_export.1 ${PREFIX}/man/man1
	${INSTALL_MAN} ${WRKSRC}/hypervisor_mode.7 ${PREFIX}/man/man7
.endif

.include <bsd.port.post.mk>
