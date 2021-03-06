# Created by: Sergey Matveychuk <sem@FreeBSD.org>
# $FreeBSD$

PORTNAME=	pxlib
PORTVERSION=	0.6.3
PORTREVISION=	1
CATEGORIES=	databases
MASTER_SITES=	SF

MAINTAINER=	sem@FreeBSD.org
COMMENT=	C library to read various Paradox files

BUILD_DEPENDS=	p5-XML-Parser>=0:${PORTSDIR}/textproc/p5-XML-Parser

USE_GMAKE=	yes
USE_AUTOTOOLS=	libtool
USES=		gettext iconv perl5
GNU_CONFIGURE=	yes
CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

USE_LDCONFIG=	yes

OPTIONS_DEFINE=	MAN
MAN_DESC=	Build and install manpages

NO_STAGE=	yes
.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MMAN}
BUILD_DEPENDS+=	docbook-to-man:${PORTSDIR}/textproc/docbook-to-man \
		docbook2man:${PORTSDIR}/textproc/docbook-utils

MAN3=	PX_add_primary_index.3 PX_close.3 PX_close_blob.3 PX_create_blob_file.3 \
	PX_create_file.3 PX_create_fp.3 PX_date2string.3 PX_delete.3 \
	PX_delete_record.3 PX_get_data_alpha.3 PX_get_data_bcd.3 \
	PX_get_data_blob.3 PX_get_data_byte.3 PX_get_data_bytes.3 \
	PX_get_data_double.3 PX_get_data_graphic.3 PX_get_data_long.3 \
	PX_get_data_short.3 PX_get_field.3 PX_get_fields.3 PX_get_majorversion.3 \
	PX_get_minorversion.3 PX_get_num_fields.3 PX_get_num_records.3 \
	PX_get_opaque.3 PX_get_parameter.3 PX_get_record.3 PX_get_record2.3 \
	PX_get_recordsize.3 PX_get_subminorversion.3 PX_get_value.3 \
	PX_insert_record.3 PX_new.3 PX_new2.3 PX_new3.3 PX_new_blob.3 \
	PX_open_blob_file.3 PX_open_blob_fp.3 PX_open_file.3 PX_open_fp.3 \
	PX_open_gsf.3 PX_put_data_alpha.3 PX_put_data_bcd.3 PX_put_data_byte.3 \
	PX_put_data_bytes.3 PX_put_data_double.3 PX_put_data_long.3 \
	PX_put_data_short.3 PX_put_record.3 PX_put_recordn.3 PX_read_blobdata.3 \
	PX_read_primary_index.3 PX_retrieve_record.3 PX_set_blob_file.3 \
	PX_set_inputencoding.3 PX_set_parameter.3 PX_set_tablename.3 \
	PX_set_targetencoding.3 PX_set_value.3 PX_strdup.3 PX_time2string.3 \
	PX_timestamp2string.3 PX_update_record.3 PX_write_primary_index.3 pxlib.3
.else
pre-build:
	${REINPLACE_CMD} -e 's/^DOCDIR =.*/DOCDIR =/' ${WRKSRC}/Makefile
.endif

.include <bsd.port.mk>
