#
# Copyright (C) 2014 Thecarevoice.com
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=kangyu
PKG_VERSION:=1.0.0
PKG_RELEASE:=1
PKG_MAINTAINER:=Wenjie Zhang <wei.a.yang at gmail com>
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)-$(PKG_RELEASE)

include $(INCLUDE_DIR)/package.mk

define Package/kangyu
  SECTION:=base
  CATEGORY:=Base system
  TITLE:=Base configurations for KangYu product
endef

define Package/kangyu/Description
 This package contains many default configurations for KangYu product.
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
endef

define Build/Configure

endef

define Build/Compile/Default

endef

Build/Compile = $(Build/Compile/Default)

define Package/kangyu/install
	$(INSTALL_DIR) $(1)/etc/ $(1)/etc/config/ $(1)/etc/dropbear/

	$(INSTALL_DATA) ./files/etc/config/wireless $(1)/etc/config/wireless
	cp ./files/etc/dropbear/authorized_keys $(1)/etc/dropbear/authorized_keys
	chmod 0600 $(1)/etc/dropbear/authorized_keys
endef

$(eval $(call BuildPackage,kangyu))
