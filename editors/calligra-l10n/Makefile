# $FreeBSD$

PORTNAME=	calligra-l10n
PORTVERSION=	${CALLIGRA_VERSION}
CATEGORIES=	editors kde
MASTER_SITES=	# none
DISTFILES=	# none
EXTRACT_ONLY=	# none

MAINTAINER=	kde@FreeBSD.org
COMMENT=	Localized messages and documentation for Calligra

NO_BUILD=	yes
USE_KDE4=	kdeprefix

CALLIGRA_LANG_ALL=	bs ca ca@valencia cs da de el en_GB es et fi fr \
			gl hu it ja kk nb nds nl pl pt pt_BR ru sk sl \
			sv tr uk zh_CN zh_TW

ca@valencia_PORT=	editors/calligra-l10n-ca_valencia
de_PORT=	german/calligra-l10n
fr_PORT=	french/calligra-l10n
hu_PORT=	hungarian/calligra-l10n
ja_PORT=	japanese/calligra-l10n
pl_PORT=	polish/calligra-l10n
pt_PORT=	portuguese/calligra-l10n
pt_BR_PORT=	portuguese/calligra-l10n-pt_BR
ru_PORT=	russian/calligra-l10n
uk_PORT=	ukrainian/calligra-l10n
zh_CN_PORT=	chinese/calligra-l10n-zh_CN
zh_TW_PORT=	chinese/calligra-l10n-zh_TW

NO_STAGE=	yes
.include "${.CURDIR}/../../misc/kde4-l10n/files/kde4-lang-names"
nb_NAME=	Norwegian Bokmal

OPTIONS_DEFINE=	ALL ${LANG_OPT_ALL}
OPTIONS_DEFAULT=ALL

ALL_DESC=	All localizations

.for lang in ${CALLIGRA_LANG_ALL}
${lang}_DETECT?=	${KDE4_PREFIX}/share/locale/${lang}/LC_MESSAGES/calligra.mo
${lang}_PORT?=		editors/calligra-l10n-${lang}
${lang}_NAME?=		${lang}

${lang}_OPT=		${lang:S/@/_/}
LANG_OPT_ALL+=		${${lang}_OPT}
${${lang}_OPT}_DESC=	${${lang}_NAME} localization

${${lang}_OPT}_DEP=	${${lang}_DETECT}:${PORTSDIR}/${${lang}_PORT}
.endfor

.include <bsd.port.options.mk>

.for opt in ${LANG_OPT_ALL}
. if ${PORT_OPTIONS:M${opt}} || ${PORT_OPTIONS:MALL}
RUN_DEPENDS+=	${${opt}_DEP}
. endif
.endfor

do-install:
	${DO_NADA}

.include <bsd.port.mk>
