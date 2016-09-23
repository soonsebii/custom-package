#
# Copyright (C) 2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NPM_NAME:=webworker-threads
PKG_NAME:=$(PKG_NPM_NAME)
PKG_VERSION:=0.7.8
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/audreyt/node-webworker-threads.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=4d1634fce0932dc5c597e8d29d88a83b4f4f7fc6
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_DEPENDS:=node/host
PKG_NODE_VERSION:=4.5.0

include $(INCLUDE_DIR)/package.mk

define Package/webworker-threads
  SUBMENU:=Node.js
  SECTION:=lang
  CATEGORY:=Languages
  DEPENDS:=+node
  TITLE:=Lightweight Web Worker.
  URL:=https://github.com/audreyt/node-webworker-threads
endef

define Package/webworker-threads/description
  Lightweight Web Worker API implementation with native threads https://npmjs.org/package/webworker-threads.
endef

define Build/Compile
	$(MAKE_VARS) \
	$(MAKE_FLAGS) \
	npm_config_arch=$(CONFIG_ARCH) \
	npm_config_nodedir=$(BUILD_DIR)/node-v$(PKG_NODE_VERSION)/ \
	PREFIX="$(PKG_INSTALL_DIR)/usr/" \
	$(STAGING_DIR_HOST)/bin/npm install -g $(PKG_BUILD_DIR)
endef

define Package/webworker-threads/install
	mkdir -p $(1)/usr/lib/node_modules/webworker-threads
	$(CP) -r $(PKG_INSTALL_DIR)/usr/lib/node_modules/webworker-threads/* $(1)/usr/lib/node_modules/webworker-threads/
endef

$(eval $(call BuildPackage,webworker-threads))
