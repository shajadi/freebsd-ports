# Created by: Jui-Nan Lin <jnlin@csie.nctu.edu.tw>
# $FreeBSD$

PORTNAME=	smbftpd
PORTVERSION=	2.4
CATEGORIES=	ftp
MASTER_SITES=	SF/${PORTNAME}/SmbFTPD/${PORTVERSION}	\
		http://www.twbsd.org/download/download.php?file=smbftpd/

MAINTAINER=	jnlin@csie.nctu.edu.tw
COMMENT=	FTP daemon using Samba-like share management mechanism

OPTIONS_DEFINE=	MYSQL PGSQL SSL ICONV
MYSQL_DESC=	Users database is a MySQL database
PGSQL_DESC=	Users database is a PostgreSQL database
SSL_DESC=	Enable SSL/TLS support
ICONV_DESC=	Enable codepage to unicode conversion for UTF-8 FTP

HAS_CONFIGURE=	yes
MAKE_ENV=	OSTYPE=FreeBSD
CONFIGURE_ARGS=	"--prefix=${PREFIX}"

USES=		perl5
USE_RC_SUBR=	${PORTNAME}

NO_STAGE=	yes
.include <bsd.port.pre.mk>

.if ${PORT_OPTIONS:MMYSQL}
USE_MYSQL=	yes
CONFIGURE_ARGS+=	"--with-mysql"
.endif

.if ${PORT_OPTIONS:MPGSQL}
USE_PGSQL=	yes
CONFIGURE_ARGS+=	"--with-pgsql"
.endif

.if ${PORT_OPTIONS:MICONV}
USES+=		iconv
CONFIGURE_ARGS+=	"--with-iconv"
.endif

.if ${PORT_OPTIONS:MSSL}
CONFIGURE_ARGS+=	"--with-ssl"
.endif

post-extract:
	@${MV} ${WRKDIR}/${PORTNAME} ${WRKSRC}

post-patch:
	@${REINPLACE_CMD} -e '/^CONFIGS = / s|\.conf|&.sample|g' ${WRKSRC}/Makefile
	@cd ${WRKSRC}/conf/ && (${LS} *.conf | ${XARGS} -I % ${MV} % %.sample)

.include <bsd.port.post.mk>
