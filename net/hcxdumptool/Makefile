#
# Copyright (C) 2009-2014 OpenWrt.org
# Copyright (C) 2019 Andreas Nilsen <adde88@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=hcxdumptool
PKG_VERSION:=5.1.4
PKG_RELEASE:=8

PKG_BUILD_DIR:=$(BUILD_DIR)/hcxdumptool-$(PKG_VERSION)
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/ZerBea/hcxdumptool.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_SOURCE_VERSION:=287c284d1c5fcaa6f6e7a6bd2c2e757e77c21324
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

PKG_BUILD_PARALLEL:=1

PKG_USE_MIPS16:=0

include $(INCLUDE_DIR)/package.mk

define Package/hcxdumptool
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+libpcap
  TITLE:=hcxdumptool
  URL:=https://github.com/ZerBea/hcxdumptool.git
  SUBMENU:=wireless
  MAINTAINER:=Andreas Nilsen <adde88@gmail.com>
endef

define Package/hcxdumptool/description
  Small tool to capture packets from wlan devices. After capturing, upload
  the "uncleaned" cap here (https://wpa-sec.stanev.org/?submit)
  to see if your ap or the client is vulnerable by using common wordlists.
  Convert the cap to hccapx and/or to WPA-PMKID-PBKDF2 hashline (16800) with hcxpcaptool (hcxtools)
  and check if wlan-key or plainmasterkey was transmitted unencrypted.
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR)/ \
		$(TARGET_CONFIGURE_OPTS) \
		CFLAGS="$(TARGET_CFLAGS) -static"
endef

define Package/hcxdumptool/install
	$(INSTALL_DIR) $(1)/sbin
	$(CP) $(PKG_BUILD_DIR)/hcxdumptool $(1)/sbin/
endef

$(eval $(call BuildPackage,hcxdumptool))
