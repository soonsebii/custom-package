#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NPM_NAME:=lirc_web
PKG_NAME:=$(PKG_NPM_NAME)
PKG_VERSION:=0.3.1
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/alexbain/lirc_web.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=51bbe9cb60979e1b0ffee68e35507e803babf5bc
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_DEPENDS:=node/host
PKG_NODE_VERSION:=4.5.0

include $(INCLUDE_DIR)/package.mk

define Package/lirc_web
  SUBMENU:=Node.js
  SECTION:=lang
  CATEGORY:=Languages
  DEPENDS:=+node
  TITLE:=Control LIRC from the web using Node.js and lirc_node
  URL:=https://github.com/alexbain/lirc_web
endef

define Package/lirc_web/description
 Control LIRC from the web using NodeJS and lirc_node
endef

define Build/Compile
	$(MAKE_VARS) \
	$(MAKE_FLAGS) \
	npm_config_arch=$(CONFIG_ARCH) \
	npm_config_nodedir=$(BUILD_DIR)/node-v$(PKG_NODE_VERSION)/ \
	PREFIX="$(PKG_INSTALL_DIR)/usr/" \
	$(STAGING_DIR_HOST)/bin/npm install -g $(PKG_BUILD_DIR)
endef

define Package/lirc_web/install
	mkdir -p $(1)/usr/lib/node_modules/lirc_web
	$(CP) -r $(PKG_INSTALL_DIR)/usr/lib/node_modules/lirc_web/* $(1)/usr/lib/node_modules/lirc_web/
endef

$(eval $(call BuildPackage,lirc_web))

