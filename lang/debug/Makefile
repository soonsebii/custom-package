#
# Copyright (C) 2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NPM_NAME:=debug
PKG_NAME:=$(PKG_NPM_NAME)
PKG_VERSION:=2.2.0
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/visionmedia/debug.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=b38458422b5aa8aa6d286b10dfe427e8a67e2b35
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_DEPENDS:=node/host
PKG_NODE_VERSION:=4.5.0

include $(INCLUDE_DIR)/package.mk

define Package/debug
  SUBMENU:=Node.js
  SECTION:=lang
  CATEGORY:=Languages
  DEPENDS:=+node
  TITLE:=Node.js debugging utility.
  URL:=https://github.com/visionmedia/debug
endef

define Package/debug/description
  tiny node.js & browser debugging utility for your libraries and applications.
endef

define Build/Compile
	$(MAKE_VARS) \
	$(MAKE_FLAGS) \
	npm_config_arch=$(CONFIG_ARCH) \
	npm_config_nodedir=$(BUILD_DIR)/node-v$(PKG_NODE_VERSION)/ \
	PREFIX="$(PKG_INSTALL_DIR)/usr/" \
	$(STAGING_DIR_HOST)/bin/npm install -g $(PKG_BUILD_DIR)
endef

define Package/debug/install
	mkdir -p $(1)/usr/lib/node_modules/$(PKG_NAME)
	$(CP) -r $(PKG_INSTALL_DIR)/usr/lib/node_modules/$(PKG_NAME)/* $(1)/usr/lib/node_modules/$(PKG_NAME)/
endef

$(eval $(call BuildPackage,debug))
