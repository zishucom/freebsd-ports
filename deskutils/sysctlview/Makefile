# $FreeBSD$

PORTNAME=	sysctlview
PORTVERSION=	1.1
CATEGORIES=	deskutils

MAINTAINER=	alfix86@gmail.com
COMMENT=	Show sysctl MIB Tree

LICENSE=	BSD2CLAUSE
LICENSE_FILE=	${WRKSRC}/LICENSE

LIB_DEPENDS=	libsysctlmibinfo.so:devel/libsysctlmibinfo

USES=		compiler:c++11-lang gettext-runtime gnome pkgconfig
USE_GNOME=	atk atkmm cairo cairomm gdkpixbuf2 glib20 glib20 glibmm glibmm \
		gtk30 gtkmm30 libsigc++20 pango pangomm

USE_GITLAB=	yes
GL_ACCOUNT=	alfix
GL_COMMIT=	3309fd66f4f7c32056bedc1e7b40f2d489b86fe8

INSTALLS_ICONS=	yes

DESKTOP_ENTRIES=	"Sysctlview" \
			"Show kernel state" \
			"sysctlview" \
			"sysctlview" \
			"System;" \
			false

OPTIONS_DEFINE=	NLS
OPTIONS_SUB=	yes

NLS_USES=		gettext
NLS_CONFIGURE_ENABLE=	nls

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/sysctlview ${STAGEDIR}${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/sysctlview.1 ${STAGEDIR}${MAN1PREFIX}/man/man1
.for i in 16 22 24 32 36 48 64 72 96 128 192 256
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/icons/hicolor/${i}x${i}/apps/ && \
	${MV} ${WRKSRC}/icon/sysctlview-${i}.png \
		${STAGEDIR}${PREFIX}/share/icons/hicolor/${i}x${i}/apps/sysctlview.png
.endfor
	${MKDIR} ${STAGEDIR}${PREFIX}/share/icons/hicolor/scalable/apps/ && \
	${MV} ${WRKSRC}/icon/sysctlview.svg \
		${STAGEDIR}${PREFIX}/share/icons/hicolor/scalable/apps/sysctlview.svg

.include <bsd.port.mk>
