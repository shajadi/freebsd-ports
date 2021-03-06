# Created by: jburkhol@home.com
# $FreeBSD$

PORTNAME=	binutils
PORTVERSION=	2.15
CATEGORIES=	devel
MASTER_SITES=	${MASTER_SITE_GNU}
MASTER_SITE_SUBDIR=	binutils
PKGNAMEPREFIX=	m6811-

PATCH_SITES=	http://stephane.carrez.free.fr/snapshots/
PATCHFILES=	${PORTNAME}-${PORTVERSION}-m68hc1x-20040801.diffs.gz
PATCH_DIST_STRIP=	-p1

MAINTAINER=	ports@FreeBSD.org
COMMENT=	The binutils cross-toolchain for the 6811

NOT_FOR_ARCHS=	amd64
USE_GMAKE=	yes
HAS_CONFIGURE=	yes

M68_TARGET=	m6811-elf

CONFIGURE_ARGS=	--prefix=${PREFIX} \
		--target=${M68_TARGET} \
		--program-prefix=${M68_TARGET}- \
		--disable-nls

MAN1=		${M68_TARGET}-addr2line.1 \
		${M68_TARGET}-ar.1 \
		${M68_TARGET}-as.1 \
		${M68_TARGET}-c++filt.1 \
		${M68_TARGET}-dlltool.1 \
		${M68_TARGET}-ld.1 \
		${M68_TARGET}-nlmconv.1 \
		${M68_TARGET}-nm.1 \
		${M68_TARGET}-objcopy.1 \
		${M68_TARGET}-objdump.1 \
		${M68_TARGET}-ranlib.1 \
		${M68_TARGET}-readelf.1 \
		${M68_TARGET}-size.1 \
		${M68_TARGET}-strings.1 \
		${M68_TARGET}-strip.1 \
		${M68_TARGET}-windres.1

INFO=		${M68_TARGET}-as \
		${M68_TARGET}-bfd \
		${M68_TARGET}-binutils \
		${M68_TARGET}-ld \

NO_STAGE=	yes
post-patch:
	# as.info -> ${M68_TARGET}-as.info
	@${REINPLACE_CMD} -e 's|setfilename as.info|setfilename ${M68_TARGET}-as.info|' ${WRKSRC}/gas/doc/as.texinfo
	@${REINPLACE_CMD} -e 's|(as)|(${M68_TARGET}-as)|' ${WRKSRC}/gas/doc/as.texinfo
	@${REINPLACE_CMD} -e 's|@file{as}|@file{${M68_TARGET}-as}|' ${WRKSRC}/gas/doc/as.texinfo
	@${REINPLACE_CMD} -e 's|as.info|${M68_TARGET}-as.info|' ${WRKSRC}/gas/doc/Makefile.in
	@${REINPLACE_CMD} -e 's|as.texinfo|${M68_TARGET}-as.texinfo|' ${WRKSRC}/gas/doc/Makefile.in
	@${MV} ${WRKSRC}/gas/doc/as.texinfo ${WRKSRC}/gas/doc/${M68_TARGET}-as.texinfo
	# bfd.info -> ${M68_TARGET}-bfd.info
	@${REINPLACE_CMD} -e 's|setfilename bfd.info|setfilename ${M68_TARGET}-bfd.info|' ${WRKSRC}/bfd/doc/bfd.texinfo
	@${REINPLACE_CMD} -e 's|(bfd)|(${M68_TARGET}-bfd)|' ${WRKSRC}/bfd/doc/bfd.texinfo
	@${REINPLACE_CMD} -e 's|@file{bfd}|@file{${M68_TARGET}-bfd}|' ${WRKSRC}/bfd/doc/bfd.texinfo
	@${REINPLACE_CMD} -e 's|bfd.info|${M68_TARGET}-bfd.info|' ${WRKSRC}/bfd/doc/Makefile.in
	@${REINPLACE_CMD} -e 's|bfd.texinfo|${M68_TARGET}-bfd.texinfo|' ${WRKSRC}/bfd/doc/Makefile.in
	@${MV} ${WRKSRC}/bfd/doc/bfd.texinfo ${WRKSRC}/bfd/doc/${M68_TARGET}-bfd.texinfo
	# binutils.info -> ${M68_TARGET}-binutils.info
	@${REINPLACE_CMD} -e 's|setfilename binutils.info|setfilename ${M68_TARGET}-binutils.info|' ${WRKSRC}/binutils/doc/binutils.texi
	@${REINPLACE_CMD} -e 's|(binutils)|(${M68_TARGET}-binutils)|' ${WRKSRC}/binutils/doc/binutils.texi
	@${REINPLACE_CMD} -e 's|@file{binutils}|@file{${M68_TARGET}-binutils}|' ${WRKSRC}/binutils/doc/binutils.texi
	@${REINPLACE_CMD} -e 's|binutils.info|${M68_TARGET}-binutils.info|' ${WRKSRC}/binutils/doc/Makefile.in
	@${REINPLACE_CMD} -e 's|binutils.texi|${M68_TARGET}-binutils.texi|' ${WRKSRC}/binutils/doc/Makefile.in
	@${MV} ${WRKSRC}/binutils/doc/binutils.texi ${WRKSRC}/binutils/doc/${M68_TARGET}-binutils.texi
	# ld.info -> ${M68_TARGET}-ld.info
	@${REINPLACE_CMD} -e 's|setfilename ld.info|setfilename ${M68_TARGET}-ld.info|' ${WRKSRC}/ld/ld.texinfo
	@${REINPLACE_CMD} -e 's|(ld)|(${M68_TARGET}-ld)|' ${WRKSRC}/ld/ld.texinfo
	@${REINPLACE_CMD} -e 's|@file{ld}|@file{${M68_TARGET}-ld}|' ${WRKSRC}/ld/ld.texinfo
	@${REINPLACE_CMD} -e 's|ld.info|${M68_TARGET}-ld.info|' ${WRKSRC}/ld/Makefile.in
	@${REINPLACE_CMD} -e 's|ld.texinfo|${M68_TARGET}-ld.texinfo|' ${WRKSRC}/ld/Makefile.in
	@${MV} ${WRKSRC}/ld/ld.texinfo ${WRKSRC}/ld/${M68_TARGET}-ld.texinfo

.include <bsd.port.mk>
