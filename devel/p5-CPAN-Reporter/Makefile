# Created by: Steve Wills <swills@FreeBSD.org>
# $FreeBSD$

PORTNAME=	CPAN-Reporter
PORTVERSION=	1.2006
CATEGORIES=	devel
MASTER_SITES=	CPAN
MASTER_SITE_SUBDIR=	CPAN:DAGOLDEN
PKGNAMEPREFIX=	p5-

MAINTAINER=	swills@FreeBSD.org
COMMENT=	Adds CPAN Testers reporting to CPAN.pm

BUILD_DEPENDS=	p5-Archive-Tar>0:${PORTSDIR}/archivers/p5-Archive-Tar \
		p5-Capture-Tiny>0:${PORTSDIR}/devel/p5-Capture-Tiny \
		p5-Config-Tiny>0:${PORTSDIR}/devel/p5-Config-Tiny \
		p5-File-Copy-Recursive>0:${PORTSDIR}/devel/p5-File-Copy-Recursive \
		p5-File-HomeDir>0:${PORTSDIR}/devel/p5-File-HomeDir \
		p5-File-pushd>0:${PORTSDIR}/devel/p5-File-pushd \
		p5-IO-CaptureOutput>0:${PORTSDIR}/devel/p5-IO-CaptureOutput \
		p5-IPC-Cmd>=0.76:${PORTSDIR}/devel/p5-IPC-Cmd \
		p5-Probe-Perl>0:${PORTSDIR}/sysutils/p5-Probe-Perl \
		p5-Test-Reporter>1.54:${PORTSDIR}/devel/p5-Test-Reporter \
		p5-Devel-Autoflush>0:${PORTSDIR}/devel/p5-Devel-Autoflush \
		p5-Tee>0:${PORTSDIR}/devel/p5-Tee
RUN_DEPENDS:=	${BUILD_DEPENDS}

USES=		perl5
USE_PERL5=	configure

MAN3=	CPAN::Reporter::API.3 CPAN::Reporter::Config.3 \
	CPAN::Reporter::History.3 CPAN::Reporter::PrereqCheck.3 \
	CPAN::Reporter.3 CPAN::Reporter::FAQ.3

NO_STAGE=	yes
.include <bsd.port.mk>
