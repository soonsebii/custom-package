#
# Copyright (C) 2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NPM_NAME:=node-status-api
PKG_NAME:=$(PKG_NPM_NAME)
PKG_VERSION:=0.0.1
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/soonsebii/node-status-api.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=56808b18c6e854c189c9ebeb54a5c0d0dfaf033c
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_DEPENDS:=node/host
PKG_NODE_VERSION:=4.5.0

include $(INCLUDE_DIR)/package.mk

define Package/node-status-api
  SUBMENU:=Node.js
  SECTION:=lang
  CATEGORY:=Languages
  DEPENDS:=+node
  TITLE:=Lightweight RESTful API Server.
  URL:=https://github.com/soonsebii/node-status-api
endef

define Package/node-status-api/description
  Lightweight RESTful API Server.
endef

define Build/Compile
	$(MAKE_VARS) \
	$(MAKE_FLAGS) \
	npm_config_arch=$(CONFIG_ARCH) \
	npm_config_nodedir=$(BUILD_DIR)/node-v$(PKG_NODE_VERSION)/ \
	PREFIX="$(PKG_INSTALL_DIR)/usr/" \
	$(STAGING_DIR_HOST)/bin/npm install -g $(PKG_BUILD_DIR)
endef

define Package/node-status-api/install
	mkdir -p $(1)/usr/lib/node_modules/node-status-api
	$(CP) -r $(PKG_INSTALL_DIR)/usr/lib/node_modules/node-status-api/* $(1)/usr/lib/node_modules/node-status-api/
endef

$(eval $(call BuildPackage,node-status-api))

