# $FreeBSD$

PORTNAME=	bcrypt
PORTVERSION=	2.1
CATEGORIES=	security
PKGNAMEPREFIX=	${LUA_PKGNAMEPREFIX}

MAINTAINER=	mdw@freebsd.org
COMMENT=	Library providing OpenBSD's bcrypt hash function for Lua

LICENSE=	ISCL

USES=		gmake lua

USE_GITHUB=	yes
GH_ACCOUNT=	mikejsavage
GH_PROJECT=	lua-bcrypt
GH_TAGNAME=	d64cdc8

PLIST_FILES=	${LUA_MODLIBDIR}/bcrypt.so

do-install:
	@${MKDIR} ${STAGEDIR}${LUA_MODLIBDIR}
	${INSTALL_LIB} ${WRKSRC}/bcrypt.so ${STAGEDIR}${LUA_MODLIBDIR}

.include <bsd.port.mk>
