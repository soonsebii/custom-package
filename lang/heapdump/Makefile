#
# Copyright (C) 2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NPM_NAME:=heapdump
PKG_NAME:=$(PKG_NPM_NAME)
PKG_VERSION:=0.3.7
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/bnoordhuis/node-heapdump.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=3e308b302fb2d7beba5b1c4a6eaf92caba51cbf2
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_DEPENDS:=node/host
PKG_NODE_VERSION:=4.5.0

include $(INCLUDE_DIR)/package.mk

define Package/heapdump
  SUBMENU:=Node.js
  SECTION:=lang
  CATEGORY:=Languages
  DEPENDS:=+node
  TITLE:=Heapdump
  URL:=https://github.com/bnoordhuis/node-heapdump.git
endef

define Package/heapdump/description
  Make a dump of the V8 heap for later inspection.
endef

define Build/Compile
	$(MAKE_VARS) \
	$(MAKE_FLAGS) \
	npm_config_arch=$(CONFIG_ARCH) \
	npm_config_nodedir=$(BUILD_DIR)/node-v$(PKG_NODE_VERSION)/ \
	PREFIX="$(PKG_INSTALL_DIR)/usr/" \
	$(STAGING_DIR_HOST)/bin/npm install -g $(PKG_BUILD_DIR)
endef

define Package/heapdump/install
	mkdir -p $(1)/usr/lib/node_modules/$(PKG_NAME)
	$(CP) -r $(PKG_INSTALL_DIR)/usr/lib/node_modules/$(PKG_NAME)/* $(1)/usr/lib/node_modules/$(PKG_NAME)/
endef

$(eval $(call BuildPackage,heapdump))
