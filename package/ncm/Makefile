#
# Copyright (C) 2007-2013 OpenWrt.org
# Copyright (C) 2010 Vertical Communications
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ncm
PKG_VERSION:=1.0.1
PKG_RELEASE:=1
PKG_MAINTAINER:=Oskari Rauta <oskari.rauta at gmail com>
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)-$(PKG_RELEASE)

include $(INCLUDE_DIR)/package.mk

define Package/ncm
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Protocol support for NCM
  DEPENDS:=+comgt +kmod-usb-net-cdc-ncm +kmod-usb-serial
endef

define Package/ncm/Description
 This package contains protocol support for NCM.
endef

define Package/ncm-huawei-e3276
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Huawei E3276 support for NCM protocol
  DEPENDS:=+comgt +kmod-usb-serial +kmod-usb-serial-option ncm
endef

define Package/ncm-huawei-e3276/Description
 This package contains communication scripts for Huawei E3276
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
endef

define Build/Configure

endef

define Build/Compile/Default

endef

Build/Compile = $(Build/Compile/Default)

define Package/ncm/install
	$(INSTALL_DIR) $(1)/lib/ $(1)/lib/netifd/ $(1)/lib/netifd/proto/ $(1)/etc/ \
		$(1)/etc/gcom/ $(1)/etc/gcom/ncm/ $(1)/etc/gcom/ncm/signal/ \
		$(1)/etc/gcom/ncm/carrier/ $(1)/etc/gcom/ncm/setmode/ \
		$(1)/etc/gcom/ncm/connect/ $(1)/etc/gcom/ncm/initscripts/ \
		$(1)/etc/modules.d/ $(1)/etc/config/

	$(INSTALL_BIN) ./files/lib/netifd/ncm_dhcp.script $(1)/lib/netifd/
	$(INSTALL_BIN) ./files/lib/netifd/proto/ncm.sh $(1)/lib/netifd/proto/
	$(INSTALL_DATA) ./files/etc/gcom/ncm/getcardinfo.gcom $(1)/etc/gcom/ncm/
	$(INSTALL_DATA) ./files/etc/modules.d/60-usb-serial $(1)/etc/modules.d/60-usb-serial
	$(INSTALL_DATA) ./files/etc/config/network $(1)/etc/config/network
endef

define Package/ncm-huawei-e3276/install
	$(INSTALL_DIR) $(1)/etc/ $(1)/etc/gcom/ $(1)/etc/gcom/ncm/ \
		$(1)/etc/gcom/ncm/signal/ $(1)/etc/gcom/ncm/carrier/ \
		$(1)/etc/gcom/ncm/setmode/ $(1)/etc/gcom/ncm/connect/ \
		$(1)/etc/gcom/ncm/initscripts/

	$(INSTALL_DATA) ./files/etc/gcom/ncm/signal/huawei_e3276.gcom $(1)/etc/gcom/ncm/signal/
	$(INSTALL_DATA) ./files/etc/gcom/ncm/carrier/huawei_e3276.gcom $(1)/etc/gcom/ncm/carrier/
	$(INSTALL_DATA) ./files/etc/gcom/ncm/setmode/huawei_e3276.gcom $(1)/etc/gcom/ncm/setmode/
	$(INSTALL_DATA) ./files/etc/gcom/ncm/connect/huawei_e3276.gcom $(1)/etc/gcom/ncm/connect/
	$(INSTALL_DATA) ./files/etc/gcom/ncm/initscripts/huawei_e3276.gcom $(1)/etc/gcom/ncm/initscripts/
endef

$(eval $(call BuildPackage,ncm))
$(eval $(call BuildPackage,ncm-huawei-e3276))
