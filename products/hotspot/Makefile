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
		CONFIG_PACKAGE_fon-luci=y  \
		CONFIG_PACKAGE_luci-admin-fon=y  \
		CONFIG_PACKAGE_luci-admin-fon-rpc=y \
		CONFIG_PACKAGE_luci-admin-rpc=y \
		CONFIG_PACKAGE_luci-app-facebook=y \
		CONFIG_PACKAGE_luci-app-fonfw=y \
		CONFIG_PACKAGE_luci-app-qos=y \
		CONFIG_PACKAGE_luci-app-upgrade=y \
		CONFIG_PACKAGE_luci-app-wizard-fonera2=y \
		CONFIG_PACKAGE_luci-cbi=y \
		CONFIG_PACKAGE_luci-core=y \
		CONFIG_PACKAGE_luci-core_source=y \
		CONFIG_PACKAGE_luci-fon=y \
		CONFIG_PACKAGE_luci-http=y \
		CONFIG_PACKAGE_luci-httpclient=y \
		CONFIG_PACKAGE_luci-json=y \
		CONFIG_PACKAGE_luci-luanet=y \
		CONFIG_PACKAGE_luci-lucid=y \
		CONFIG_PACKAGE_luci-nixio=y \
		CONFIG_PACKAGE_luci-nixio_openssl=y \
		CONFIG_PACKAGE_luci-px5g=y \
		CONFIG_PACKAGE_luci-sgi-cgi=y \
		CONFIG_PACKAGE_luci-sys=y \
		CONFIG_PACKAGE_luci-twitter=y \
		CONFIG_PACKAGE_luci-uci=y \
		CONFIG_PACKAGE_luci-uvl=y \
		CONFIG_PACKAGE_luci-web=y \
		CONFIG_PACKAGE_luci-theme-fon=y \
		CONFIG_PACKAGE_luci-i18n-english=y \
		CONFIG_PACKAGE_luci-i18n-zh_cn=y \
		CONFIG_PACKAGE_fonbase=y \
		CONFIG_PACKAGE_fonstate=y \
		CONFIG_PACKAGE_fonsmcd=y \
		CONFIG_PACKAGE_onlined=y \
		CONFIG_PACKAGE_vboot_utils=y \
		CONFIG_PACKAGE_libcurl=y \
		CONFIG_LIBCURL_OPENSSL=y \
		CONFIG_LIBCURL_THREADED_RESOLVER=y \
		CONFIG_LIBCURL_ZLIB=y \
		CONFIG_LIBCURL_CRYPTO_AUTH=y \
		CONFIG_PACKAGE_lua-mosquitto=y \
		CONFIG_PACKAGE_mqtt-service=y \
		CONFIG_PACKAGE_easycwmp=y \
		CONFIG_EASYCWMP_DEVEL=y \
		CONFIG_EASYCWMP_DEBUG=y \
		CONFIG_PACKAGE_uhttpd-mod-lua=y \
		CONFIG_PACKAGE_libubus-lua=y \
		CONFIG_PACKAGE_luaposix=y \
		CONFIG_PACKAGE_uhttpd=y \
		CONFIG_PACKAGE_qos-gargoyle=y \
		CONFIG_PACKAGE_gargoyle-firewall-util=y \
		CONFIG_PACKAGE_libericstools=y \
		CONFIG_PACKAGE_libiptbwctl=y \
		CONFIG_PACKAGE_bwmon-gargoyle=y \
		CONFIG_PACKAGE_webmon-gargoyle=y \
		CONFIG_PACKAGE_ipset=y \
		CONFIG_PACKAGE_libmnl=y

	FEEDS += \
		mosquitto \
		libcurl \
		libmicroxml \
		shflags \
		ntpclient \
		libdaemon \
		luaposix

	TESTED := \
		ar71xx/openwrt-ar71xx-generic-tl-wr703n-v1-squashfs-factory.bin \
		ar71xx/openwrt-ar71xx-generic-tl-wr703n-v1-squashfs-sysupgrade.bin

endef

define Customization/debug
        $(call Customization/default)

        CONFIG += \
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

define Customization/managed
        $(call Customization/default)

        CONFIG += \
                CONFIG_PACKAGE_easycwmp=y

        TR69_MIGR_DIR := $(OPENWRT_DIR)/files/etc/uci-migrations/1.1.3-6
endef

define Customization/managed/prebuild
        mkdir -p $(TR69_MIGR_DIR)
        cp common/uci-migrations/tr69/set-fixed-acs.sh $(TR69_MIGR_DIR)/01-tr69-set-fixed-acs.sh
        cp common/uci-migrations/tr69/open-firewall.sh $(TR69_MIGR_DIR)/02-tr69-open-firewall.sh
        cp common/uci-migrations/tr69/fixup-wan-if.sh  $(TR69_MIGR_DIR)/03-tr69-fixup-wan-if.sh
endef
