# Created by: J.R. Oldroyd <fbsd@opal.com>
# $FreeBSD$

PORTNAME=	xfburn
PORTVERSION=	0.5.5
PORTREVISION=	1
CATEGORIES=	sysutils
MASTER_SITES=	XFCE/src/apps/${PORTNAME}/${PORTVERSION:R}
DIST_SUBDIR=	xfce4

MAINTAINER=	xfce@FreeBSD.org
COMMENT=	CD/DVD burning tool for Xfce

LICENSE=	GPLv2

LIB_DEPENDS=	libburn.so:devel/libburn \
		libfontconfig.so:x11-fonts/fontconfig \
		libfreetype.so:print/freetype2 \
		libisofs.so:devel/libisofs
RUN_DEPENDS=	cdrdao:sysutils/cdrdao \
		${LOCALBASE}/include/libburn/libburn.h:devel/libburn \
		${LOCALBASE}/include/libisofs/libisofs.h:devel/libisofs

USES=		pkgconfig gmake desktop-file-utils gettext-tools xfce tar:bzip2
GNU_CONFIGURE=	yes
USE_GNOME=	cairo intltool intlhack glib20 gtk20
USE_XFCE=	libexo
INSTALLS_ICONS=	yes

CONFIGURE_ARGS=--disable-gudev

OPTIONS_DEFINE=			GSTREAMER NLS
OPTIONS_DEFAULT=		GSTREAMER
OPTIONS_SUB=			yes
NLS_USES=			gettext-runtime
NLS_CONFIGURE_ENABLE=		nls
GSTREAMER_USE=			gstreamer1=yes,faac,flac,lame,vorbis,wavpack
GSTREAMER_CONFIGURE_ENABLE=	gstreamer

post-patch:
	${REINPLACE_CMD} -e 's|media-cdrom|media-optical|g' \
		${WRKSRC}/desktop-integration/thunar-sendto-xfburn.desktop.in \
		${WRKSRC}/xfburn.desktop.in

.include <bsd.port.mk>
