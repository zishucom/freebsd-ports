# Created by: Pakhom Golynga <pakhom@pakhom.spb.ru>
# $FreeBSD$

PORTNAME=	zabbix22
PORTREVISION=	1
CATEGORIES=	net-mgmt
PKGNAMESUFFIX=	-agent

MASTERDIR=	${.CURDIR}/../zabbix22-server

PLIST=		${PKGDIR}/pkg-plist.agent

OPTIONS_DEFINE=		CURL IPV6
OPTIONS_DEFAULT=	CURL


.include "${MASTERDIR}/Makefile"
