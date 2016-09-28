#
# Copyright (C) 2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NPM_NAME:=gc-profiler
PKG_NAME:=$(PKG_NPM_NAME)
PKG_VERSION:=1.3.1
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/bretcope/node-gc-profiler.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=ddfe19a6265a7c4bbe8cb9e6c748ddecc1b24c9f
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_DEPENDS:=node/host
PKG_NODE_VERSION:=4.5.0

include $(INCLUDE_DIR)/package.mk

define Package/gc-profiler
  SUBMENU:=Node.js
  SECTION:=lang
  CATEGORY:=Languages
  DEPENDS:=+node
  TITLE:=Node.js GC Profiler.
  URL:=https://github.com/bretcope/node-gc-profiler
endef

define Package/gc-profiler/description
  Allows you to profile when the garbage collector runs, and how long it takes.
endef

define Build/Compile
	$(MAKE_VARS) \
	$(MAKE_FLAGS) \
	npm_config_arch=$(CONFIG_ARCH) \
	npm_config_nodedir=$(BUILD_DIR)/node-v$(PKG_NODE_VERSION)/ \
	PREFIX="$(PKG_INSTALL_DIR)/usr/" \
	$(STAGING_DIR_HOST)/bin/npm install -g $(PKG_BUILD_DIR)
endef

define Package/gc-profiler/install
	mkdir -p $(1)/usr/lib/node_modules/$(PKG_NAME)
	$(CP) -r $(PKG_INSTALL_DIR)/usr/lib/node_modules/$(PKG_NAME)/* $(1)/usr/lib/node_modules/$(PKG_NAME)/
endef

$(eval $(call BuildPackage,gc-profiler))
