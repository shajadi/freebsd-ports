# Created by: Gunter Wambaugh <gunter@six-two.net>
# $FreeBSD$

PORTNAME=	Net-Google-Spreadsheets
PORTVERSION=	0.15.01
CATEGORIES=	net perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-
DISTNAME=	${PORTNAME}-${PORTVERSION:R}${PORTVERSION:E}

MAINTAINER=	gunter@six-two.net
COMMENT=	Perl module for using Google Spreadsheets API

BUILD_DEPENDS=	p5-Any-Moose>=0:${PORTSDIR}/devel/p5-Any-Moose \
		p5-Mouse>=0.51:${PORTSDIR}/devel/p5-Mouse \
		p5-Net-Google-AuthSub>=0:${PORTSDIR}/net/p5-Net-Google-AuthSub \
		p5-Net-Google-DataAPI>=0.27:${PORTSDIR}/net/p5-Net-Google-DataAPI \
		p5-URI>=0:${PORTSDIR}/net/p5-URI \
		p5-XML-Atom>=0:${PORTSDIR}/textproc/p5-XML-Atom
RUN_DEPENDS:=	${BUILD_DEPENDS}

TEST_DEPENDS=	p5-Test-Exception>=0:${PORTSDIR}/devel/p5-Test-Exception \
		p5-Test-MockModule>=0:${PORTSDIR}/devel/p5-Test-MockModule \
		p5-Test-MockObject>=0:${PORTSDIR}/devel/p5-Test-MockObject

USES=		perl5
USE_PERL5=	configure

MAN3=		Net::Google::Spreadsheets.3 \
		Net::Google::Spreadsheets::Cell.3 \
		Net::Google::Spreadsheets::Record.3 \
		Net::Google::Spreadsheets::Row.3 \
		Net::Google::Spreadsheets::Spreadsheet.3 \
		Net::Google::Spreadsheets::Table.3 \
		Net::Google::Spreadsheets::Worksheet.3

NO_STAGE=	yes
.include <bsd.port.mk>
