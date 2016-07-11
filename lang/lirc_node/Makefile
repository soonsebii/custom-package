#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NPM_NAME:=lirc_node
PKG_NAME:=$(PKG_NPM_NAME)
PKG_VERSION:=0.0.4
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/alexbain/lirc_node.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=4144cad04b0edbea0257063a8186035cd9caaae7
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_DEPENDS:=node/host
PKG_NODE_VERSION:=0.12.7

include $(INCLUDE_DIR)/package.mk

define Package/lirc_node
  SUBMENU:=Node.js
  SECTION:=lang
  CATEGORY:=Languages
  DEPENDS:=+node
  TITLE:=Control LIRC from Node
  URL:=https://github.com/alexbain/lirc_node
endef

define Package/lirc_node/description
 Node.js package to access IR devices
endef

define Build/Compile
	$(MAKE_VARS) \
	$(MAKE_FLAGS) \
	npm_config_arch=$(CONFIG_ARCH) \
	npm_config_nodedir=$(BUILD_DIR)/node-v$(PKG_NODE_VERSION)/ \
	PREFIX="$(PKG_INSTALL_DIR)/usr/" \
	$(STAGING_DIR_HOST)/bin/npm install -g $(PKG_BUILD_DIR)
endef

define Package/lirc_node/install
	mkdir -p $(1)/usr/lib/node_modules/lirc_node
	$(CP) -r $(PKG_INSTALL_DIR)/usr/lib/node_modules/lirc_node/* $(1)/usr/lib/node_modules/lirc_node/
endef

$(eval $(call BuildPackage,lirc_node))

