#
# Copyright (C) 2009-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=hcxdumptool
PKG_VERSION:=4.2.1
PKG_RELEASE:=2

PKG_BUILD_DIR:=$(BUILD_DIR)/hcxdumptool-$(PKG_VERSION)
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/ZerBea/hcxdumptool.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_SOURCE_VERSION:=c79a67caa175db2ad52fa5aba165e470e7ee879a
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

PKG_MAINTAINER:=Andreas Nilsen <adde88@gmail.com.com>

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/hcxdumptool
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+libpthread +libpcap
  TITLE:= hcxdumptool
  URL:=https://github.com/ZerBea/hcxdumptool.git
  SUBMENU:=wireless
endef

define Package/hcxdumptool/description
  Small tool to capture packets from wlan devices. After capturing, upload
  the "uncleaned" cap here (https://wpa-sec.stanev.org/?submit)
  to see if your ap or the client is vulnerable by using common wordlists.
  Convert the cap to hccapx and/or to WPA-PMKID-PBKDF2 hashline (16800) with hcxpcaptool (hcxtools)
  and check if wlan-key or plainmasterkey was transmitted unencrypted.
endef

define Package/hcxtools/postinst
#!/bin/sh
# Let's fix the Pineapples damn PATH environment variable permanently!
echo 'export PATH=/usr/bin/pineapple:/bin:/sbin:/usr/bin:/usr/sbin:/sd/usr/sbin:/sd/usr/bin:/sd/bin:/sd/sbin' >> /etc/profile
endef

define Package/hcxdumptool/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(CP) $(PKG_BUILD_DIR)/hcxdumptool $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,hcxdumptool))