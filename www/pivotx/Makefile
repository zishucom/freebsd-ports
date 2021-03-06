# Created by: Fumiyuki Shimizu <fumifumi@abacustech.jp>
# $FreeBSD$

PORTNAME=	pivotx
PORTVERSION=	2.3.11
CATEGORIES=	www
MASTER_SITES=	http://pivotx.net/files/ \
		http://pivotx.net/files/archived/
DISTNAME=	pivotx_${PORTVERSION}

MAINTAINER=	fumifumi@abacustech.jp
COMMENT=	Software to help you maintain dynamic sites such as weblogs

LICENSE=	GPLv2

DEPRECATED=	inactive upstream and does not work with PHP 7
EXPIRATION_DATE=	2019-05-31

PORTDOCS=	LICENSE.txt README.txt
PORTEXAMPLES=	example.htaccess example.web.config

# Requirements:
# http://book.pivotx.net/index.php?page=app-e#anchor-determining-if-your-server-meets-pivotxs-requirements

OPTIONS_DEFINE=	PHPDOM DOCS EXAMPLES
PHPDOM_DESC=	Use PHP:DOM instead of SimpleXML

USES+=		cpe php:web tar:tgz
USE_PHP=	session gettext xml tokenizer gd pcre

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MPHPDOM}
USE_PHP+=	dom
.else
USE_PHP+=	simplexml
.endif

NO_BUILD=	YES

TEMP_WRKSRC=	${WRKDIR}/.temp-${PORTNAME}-${PORTVERSION}-${PORTREVISION}
TEMP_DIFF=	${WRKDIR}/.temp-diff-${PORTNAME}-${PORTVERSION}-${PORTREVISION}

BLOGURL=	${PORTNAME}
.if defined(BLOGDIR)
# Relative to ${PREFIX}
WWWDIR=		${PREFIX}/${BLOGDIR}
.endif

SUB_FILES=	pkg-message
SUB_LIST=	BLOGURL=${BLOGURL}

post-extract:
	@if ${TEST} -e '${TEMP_WRKSRC}'; then ${RM} -r '${TEMP_WRKSRC}'; fi
	@${MKDIR} '${TEMP_WRKSRC}'
	@${MV} '${WRKDIR}/'* '${TEMP_WRKSRC}'
	@${MV} '${TEMP_WRKSRC}' '${WRKSRC}'
	@${MKDIR} '${TEMP_WRKSRC}'
.for FILES in ${PORTDOCS}
	@${MV} '${WRKSRC}/${FILES}' '${TEMP_WRKSRC}'
.endfor

post-patch:
.for FILES in ${PORTEXAMPLES}
	@${SED} -e 's#%%BLOGURL%%#${BLOGURL}#g' '${WRKSRC}/${FILES}' >'${TEMP_WRKSRC}/${FILES}'
	@${RM} '${WRKSRC}/${FILES}'
.endfor
	@cd '${WRKSRC}' && ${FIND} . -type f -name '*.orig' -delete

do-install:
	@${MKDIR} '${STAGEDIR}${DOCSDIR}'
.for FILES in ${PORTDOCS}
	${INSTALL_DATA} '${TEMP_WRKSRC}/${FILES}' '${STAGEDIR}${DOCSDIR}'
.endfor
	@${MKDIR} '${STAGEDIR}${EXAMPLESDIR}'
.for FILES in ${PORTEXAMPLES}
	${INSTALL_DATA} '${TEMP_WRKSRC}/${FILES}' '${STAGEDIR}${EXAMPLESDIR}'
.endfor
	@${MKDIR} '${STAGEDIR}${WWWDIR}'
	@cd '${WRKSRC}' && ${COPYTREE_SHARE} . '${STAGEDIR}${WWWDIR}'

.include <bsd.port.mk>
