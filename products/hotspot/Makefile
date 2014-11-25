# (C) 2014 Thecarevoice.com

#
# Product profile: hotspot (Next generation hotspot)
#

define Product/hotspot

	CONFIG += \
		CONFIG_BUSYBOX_CONFIG_TELNETD=n

endef

define Customization/default

	CONFIG += \
		CONFIG_PACKAGE_kmod-usb-serial=y \
		CONFIG_PACKAGE_kmod-usb-serial-option=y \
		CONFIG_PACKAGE_kmod-usb-serial-wwan=y \
		CONFIG_PACKAGE_kmod-usb-net=y \
		CONFIG_PACKAGE_kmod-usb-net-cdc-ncm=y \
		CONFIG_PACKAGE_ncm=y \
		CONFIG_PACKAGE_ncm-huawei-e3276=y \
		CONFIG_PACKAGE_mwan3=y \
		CONFIG_PACKAGE_kangyu=y \
		CONFIG_PACKAGE_haserl=y \
		CONFIG_PACKAGE_coova-chilli=y \
		CONFIG_COOVACHILLI_REDIR=y \
		CONFIG_COOVACHILLI_MINIPORTAL=y \
		CONFIG_COOVACHILLI_USERAGENT=y \
		CONFIG_COOVACHILLI_DNSLOG=y \
		CONFIG_COOVACHILLI_UAMDOMAINFILE=y \
		CONFIG_COOVACHILLI_OPENSSL=y

	TESTED := \
		ar71xx/openwrt-ar71xx-generic-dragino2-kernel.bin \
		ar71xx/openwrt-ar71xx-generic-dragino2-rootfs-squashfs.bin \
		ar71xx/openwrt-ar71xx-generic-dragino2-squashfs-sysupgrade.bin

endef

define Customization/debug
        $(call Customization/default)

        CONFIG += \
		CONFIG_PACKAGE_luci=y \
		CONFIG_PACKAGE_luci-theme-bootstrap=y \
		CONFIG_PACKAGE_luci-branding=y \
		CONFIG_PACKAGE_luci-app-ncm-status=y \
		CONFIG_PACKAGE_luci-proto-ncm=y \
		CONFIG_PACKAGE_luci-app-mwan3=y \
		CONFIG_BUSYBOX_CONFIG_FEATURE_INIT_COREDUMPS=y \
		CONFIG_PACKAGE_ATH_DEBUG=y \
		CONFIG_PACKAGE_hostapd-utils=y

        LOG_MIGR_DIR := $(OPENWRT_DIR)/files/etc/uci-migrations/1.1.3-8
endef

define Customization/debug/prebuild
        touch $(OPENWRT_DIR)/files/.init_enable_core
        rm $(LOG_MIGR_DIR)/01-log-set-level-info.sh
        cp common/uci-migrations/log/set-level-debug.sh $(LOG_MIGR_DIR)/01-log-set-level-debug.sh
endef

define Customization/release
	$(call Customization/default)

	CONFIG += \
		CONFIG_PACKAGE_uhttpd=n
endef
