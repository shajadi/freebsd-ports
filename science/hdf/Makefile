# Created by: mi
# $FreeBSD$

PORTNAME=	hdf
DISTVERSION=	4.2.8
PORTREVISION=	1
PORTEPOCH=	1
CATEGORIES=	science archivers graphics
MASTER_SITES=	http://www.hdfgroup.org/ftp/HDF/releases/%SUBDIR%/
MASTER_SITE_SUBDIR=	${PORTNAME:U}${PORTVERSION}/src/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Hierarchical Data Format library (from NCSA)

LIB_DEPENDS=	jpeg:${PORTSDIR}/graphics/jpeg \
		sz:${PORTSDIR}/science/szip

CONFLICTS=	netcdf-*

USE_BZIP2=	yes
USE_FORTRAN=	yes
GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--with-jpeg="${LOCALBASE}" \
		--with-szlib="${LOCALBASE}" \
		--enable-shared
USE_LDCONFIG=	yes

MAN1=		hdf.1 hdfunpac.1 ncdump.1 ncgen.1
MAN3=		gr_chunk.3

NO_STAGE=	yes
.include <bsd.port.pre.mk>

.if ${ARCH} == "powerpc"
BROKEN=		Does not compile on powerpc
.endif

post-patch:
	@${REINPLACE_CMD} -e \
		'/PROD_/s|=.*|=""|' ${WRKSRC}/config/freebsd

post-install:
	${INSTALL_MAN} ${WRKSRC}/man/hdfunpac.1 ${MAN1PREFIX}/man/man1
	${INSTALL_MAN} ${WRKSRC}/man/gr_chunk.3 ${MAN3PREFIX}/man/man3

check regression-test test: build
	${MAKE} -C ${WRKSRC}/hdf/test check

.include <bsd.port.post.mk>
