#
# Copyright (C) 2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NPM_NAME:=noble
PKG_NAME:=$(PKG_NPM_NAME)
PKG_VERSION:=1.6
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/sandeepmistry/noble.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=bb9a12da815cf0c0e43792cfcd9ba4d61ad712c9
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_DEPENDS:=node/host libbluetooth libudev
PKG_NODE_VERSION:=4.5.0

include $(INCLUDE_DIR)/package.mk

define Package/noble
  SUBMENU:=Node.js
  SECTION:=lang
  CATEGORY:=Languages
  DEPENDS:=+node +bluez-libs +udev
  TITLE:=A Node.js BLE central module.
  URL:=https://github.com/sandeepmistry/noble
endef

define Package/noble/description
  A Node.js BLE central module.
endef

define Build/Compile
	$(MAKE_VARS) \
	$(MAKE_FLAGS) \
	npm_config_arch=$(CONFIG_ARCH) \
	npm_config_nodedir=$(BUILD_DIR)/node-v$(PKG_NODE_VERSION)/ \
	PREFIX="$(PKG_INSTALL_DIR)/usr/" \
	$(STAGING_DIR_HOST)/bin/npm install -g $(PKG_BUILD_DIR)
endef

define Package/noble/install
	mkdir -p $(1)/usr/lib/node_modules/noble
	$(CP) -r $(PKG_INSTALL_DIR)/usr/lib/node_modules/noble/* $(1)/usr/lib/node_modules/noble/
endef

$(eval $(call BuildPackage,noble))
