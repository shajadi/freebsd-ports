# Created by: ports@c0decafe.net
# $FreeBSD$

PORTNAME=	Glade
PORTVERSION=	1.007
PORTREVISION=	3
CATEGORIES=	x11-toolkits gnome perl5
MASTER_SITES=	CPAN
MASTER_SITE_SUBDIR=	CPAN:TSCH
PKGNAMEPREFIX=	p5-
PKGNAMESUFFIX=	2
DISTNAME=	Gtk2-GladeXML-${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Gtk2-Perl bindings to libglade2

EXTRACT_DEPENDS=p5-ExtUtils-Depends>=0:${PORTSDIR}/devel/p5-ExtUtils-Depends
BUILD_DEPENDS=	p5-ExtUtils-Depends>=0:${PORTSDIR}/devel/p5-ExtUtils-Depends \
		p5-Cairo>=0:${PORTSDIR}/graphics/p5-Cairo \
		p5-Gtk2>=0:${PORTSDIR}/x11-toolkits/p5-Gtk2 \
		p5-ExtUtils-PkgConfig>=0:${PORTSDIR}/devel/p5-ExtUtils-PkgConfig
RUN_DEPENDS=	p5-Gtk2>=0:${PORTSDIR}/x11-toolkits/p5-Gtk2

USE_GNOME=	libglade2
USES=		perl5
USE_PERL5=	configure

.include <bsd.port.mk>
