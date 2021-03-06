# $FreeBSD$

PORTNAME=	powerdns
PORTVERSION=	3.3
PORTREVISION?=	0
PORTEPOCH=	1
CATEGORIES=	dns ipv6
PKGNAMESUFFIX=	-devel
DISTNAME=	auth-${PORTVERSION:S/.r/-rc/}

MAINTAINER=	tremere@cainites.net
COMMENT=	An advanced DNS server with multiple backends including SQL

LICENSE=	GPLv2

BUILD_DEPENDS=	ragel:${PORTSDIR}/devel/ragel
LIB_DEPENDS=	libboost_serialization.so:${PORTSDIR}/devel/boost-libs

USE_GITHUB=	YES
GH_ACCOUNT=	PowerDNS
GH_PROJECT=	pdns
GH_TAGNAME=	auth-3.3
GH_COMMIT=	b8fe1df

USE_LUA=	5.1
LUA_COMPS=	lua

CONFLICTS=	powerdns-[2-3].[0-9]*

NO_LATEST_LINK=	YES

USES=		bison gmake pkgconfig
USE_SUBMAKE=	YES
USE_AUTOTOOLS=	autoconf:env automake:env libtool:env
USE_LDCONFIG=	YES
GNU_CONFIGURE=	YES
CXXFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib
CONFIGURE_ARGS=	--with-modules="" \
		--with-dynmodules="pipe ${CONFIGURE_MODULES}" \
		--sysconfdir="${PREFIX}/etc/pdns" \
		--with-boost="${LOCALBASE}"
SCRIPTS_ENV=	WRKDIRPREFIX="${WRKDIRPREFIX}" \
		CURDIR2="${.CURDIR}" \
		MKDIR="${MKDIR}" \
		DISTNAME="${DISTNAME}" \
		POWERDNS_OPTIONS="${POWERDNS_OPTIONS}"

SUB_FILES=	pkg-message

OPTIONS_DEFINE=	PGSQL PGSQL_LOCAL MYSQL MYSQL_LOCAL SQLITE SQLITE3 \
		OPENDBX OPENLDAP OPENLDAP_LOCAL GEO POLARSSL TOOLS
OPTIONS_MULTI=	DNSSEC
OPTIONS_MULTI_DNSSEC=	BOTAN110 CRYPTOPP

PGSQL_DESC=		PostgreSQL backend
PGSQL_LOCAL_DESC=	RUN_DEPEND on PostgreSQL server
MYSQL_DESC=		MySQL backend
MYSQL_LOCAL_DESC=	RUN_DEPEND on MySQL server
SQLITE_DESC=		SQLite 2 backend
SQLITE3_DESC=		SQLite 3 backend
OPENDBX_DESC=		OpenDBX backend
OPENLDAP_DESC=		OpenLDAP backend
OPENLDAP_LOCAL_DESC=	RUN_DEPEND on OpenLDAP server
GEO_DESC=		Geo backend
DNSSEC_DESC=		Enable extra DNSSEC options
BOTAN110_DESC=		Faster signing + ECDSA & GOST algorithms
CRYPTOPP_DESC=		ECDSA algorithms
POLARSSL_DESC=		Use embedded PolarSSL
TOOLS_DESC=		Build extra tools

OPTIONS_DEFAULT=	PGSQL DNSSEC BOTAN110 POLARSSL

.include <bsd.port.pre.mk>

USE_RC_SUBR+=	pdns-devel

.if ${PORT_OPTIONS:MTOOLS}
CONFIGURE_ARGS+=	--enable-tools
PLIST_SUB+=		WITHTOOLS=""
.else
PLIST_SUB+=		WITHTOOLS="@comment "
.endif

.if ${PORT_OPTIONS:MGEO}
CONFIGURE_MODULES+=	"geo"
PLIST_SUB+=		WITHGEO=""
.else
PLIST_SUB+=		WITHGEO="@comment "
.endif

.if ${PORT_OPTIONS:MSQLITE} && ${PORT_OPTIONS:MSQLITE3}
BROKEN=			choose only one SQLite backend version
.endif

.if ${PORT_OPTIONS:MPGSQL}
USE_PGSQL?=		YES
CONFIGURE_ARGS+=	--with-pgsql=${LOCALBASE}
CONFIGURE_MODULES+=	"gpgsql"
PLIST_SUB+=		WITHPGSQL=""
.else
CONFIGURE_ARGS+=	--without-pgsql
PLIST_SUB+=		WITHPGSQL="@comment "
.endif

.if ${PORT_OPTIONS:MMYSQL}
USE_MYSQL?=		YES
CONFIGURE_ARGS+=	--with-mysql=${LOCALBASE}
CONFIGURE_MODULES+=	"gmysql"
PLIST_SUB+=		WITHMYSQL=""
.else
CONFIGURE_ARGS+=	--without-mysql
PLIST_SUB+=		WITHMYSQL="@comment "
.endif

.if ${PORT_OPTIONS:MOPENDBX} || ${PORT_OPTIONS:MPGSQL}
.	if ${PORT_OPTIONS:MPGSQL_LOCAL}
USE_PGSQL?=		server
SUB_LIST+=		PGSQL=postgresql
.	endif
.else
SUB_LIST+=		PGSQL=
.endif
.if ${PORT_OPTIONS:MOPENDBX} || ${PORT_OPTIONS:MMYSQL}
.	if ${PORT_OPTIONS:MMYSQL_LOCAL}
USE_MYSQL?=		server
SUB_LIST+=		MYSQL=mysql
.	endif
.else
SUB_LIST+=		MYSQL=
.endif

.if ${PORT_OPTIONS:MOPENLDAP}
USE_OPENLDAP?=		YES
CONFIGURE_MODULES+=	"ldap"
CXXFLAGS+=		-L${LOCALBASE}/lib -DLDAP_DEPRECATED=1
PLIST_SUB+=		WITHOPENLDAP=""
.	if ${PORT_OPTIONS:MOPENLDAP_LOCAL}
RUN_DEPENDS+=		openldap-server>=0:${PORTSDIR}/net/openldap${WANT_OPENLDAP_VER}-server
SUB_LIST+=		SLAPD=slapd
.	else
SUB_LIST+=		SLAPD=
.	endif
.else
PLIST_SUB+=		WITHOPENLDAP="@comment "
SUB_LIST+=		SLAPD=
.endif

.if ${PORT_OPTIONS:MSQLITE}
USE_SQLITE?=		2
CONFIGURE_MODULES+=	"gsqlite"
PLIST_SUB+=		WITHSQLITE=""
.else
PLIST_SUB+=		WITHSQLITE="@comment "
.endif

.if ${PORT_OPTIONS:MSQLITE3}
USE_SQLITE?=		3
CONFIGURE_MODULES+=	"gsqlite3"
PLIST_SUB+=		WITHSQLITE3=""
.else
PLIST_SUB+=		WITHSQLITE3="@comment "
.endif

.if ${PORT_OPTIONS:MOPENDBX}
LIB_DEPENDS+=		libopendbx.so:${PORTSDIR}/databases/opendbx
CONFIGURE_MODULES+=	"opendbx"
PLIST_SUB+=		WITHOPENDBX=""
CXXFLAGS+=		-L${LOCALBASE}/lib
.else
PLIST_SUB+=		WITHOPENDBX="@comment "
.endif

.if ${PORT_OPTIONS:MPOLARSSL}
CONFIGURE_ARGS+=	--without-system-polarssl
.else
LIB_DEPENDS+=		libpolarssl.so:${PORTSDIR}/security/polarssl
.endif

.if ${PORT_OPTIONS:MBOTAN110}
CONFIGURE_ARGS+=	--enable-botan1.10
LIB_DEPENDS+=		libbotan-1.10.so:${PORTSDIR}/security/botan110
.endif

.if ${PORT_OPTIONS:MCRYPTOPP}
.	if exists(${LOCALBASE}/lib/libcryptopp.so)
LIB_DEPENDS+=		libcryptopp.so:${PORTSDIR}/security/cryptopp
.	else
BUILD_DEPENDS+=		${LOCALBASE}/lib/libcryptopp.a:${PORTSDIR}/security/cryptopp
.	endif
CONFIGURE_ARGS+=	--enable-cryptopp
.endif

pre-patch:
	@${REINPLACE_CMD} -e "s;/bin/bash;/usr/bin/env bash;" \
		-e "s;ssed -r;sed -E -e;g" \
		-e "s;-i;-i \.bak;g" \
		${WRKSRC}/build-scripts/set-version-auth
	@${REINPLACE_CMD} -e 's;\$$(LIBCURL_LIBS) \$$(MYSQL_lib);;g' \
		-e 's;\$$(LIBCURL_CFLAGS);;g' \
		${WRKSRC}/pdns/Makefile.am
.if ${PORT_OPTIONS:MBOTAN110}
	@${REINPLACE_CMD} -e 's;\$$(BOOST_CPPFLAGS);;g' \
		-e 's;-lgmp -lrt;;g' \
		${WRKSRC}/pdns/Makefile.am
	@${REINPLACE_CMD} -E -e 's;(\$$\(BOTAN110_CFLAGS\));\1 \$$\(BOOST_CPPFLAGS\);' \
		${WRKSRC}/pdns/Makefile.am
.endif
.if ${PORT_OPTIONS:MOPENLDAP}
	@${REINPLACE_CMD} -e 's;la_LDFLAGS =;la_LDFLAGS = -L${LOCALBASE}/lib ;' \
		${WRKSRC}/modules/ldapbackend/Makefile.am
.endif
.if ${PORT_OPTIONS:MPGSQL}
	@${REINPLACE_CMD} -E -e 's;(PGSQL_inc_check="\$$withval/include/pgsql)";\1 \$$withval/include";' \
		${WRKSRC}/configure.ac
.endif

pre-configure:
	@(cd ${WRKSRC} && ${WRKSRC}/build-scripts/set-version-auth git-${GH_TAGNAME} 0.0.${GH_TAGNAME} 0.0.${GH_TAGNAME} && ${WRKSRC}/bootstrap)

post-install:
	@${MKDIR} ${STAGEDIR}${EXAMPLESDIR}
.for i in pdns.conf
	${INSTALL_DATA} ${FILESDIR}/$i ${STAGEDIR}${EXAMPLESDIR}/
.endfor
.for j in libgpgsqlbackend.so libgmysqlbackend.so libgsqlitebackend.so \
	libgsqlite3backend.so libldapbackend.so libopendbxbackend.so \
	libgeobackend.so libpipebackend.so
	@if ([ -f ${STAGEDIR}${PREFIX}/lib/$j ] && [ ! -f ${STAGEDIR}${PREFIX}/lib/$j.0 ]); then \
		${LN} -sf ${PREFIX}/lib/$j ${STAGEDIR}${PREFIX}/lib/$j.0; \
	fi
.endfor

.include <bsd.port.post.mk>
