#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NPM_NAME:=mqtt
PKG_NAME:=$(PKG_NPM_NAME)
PKG_VERSION:=1.13.0
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/mqttjs/MQTT.js
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=f2c133814dee8270bb67d1304da9aa29e51fb2b1
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_DEPENDS:=node/host
PKG_NODE_VERSION:=0.12.7

include $(INCLUDE_DIR)/package.mk

define Package/mqtt
  SUBMENU:=Node.js
  SECTION:=lang
  CATEGORY:=Languages
  DEPENDS:=+node
  TITLE:=A library for the MQTT protocol
  URL:=https://github.com/mqttjs/MQTT.js
endef

define Package/mqtt/description
 MQTT.js is a client library for the MQTT protocol, written in JavaScript for node.js and the browser.
endef

define Build/Compile
	$(MAKE_VARS) \
	$(MAKE_FLAGS) \
	npm_config_arch=$(CONFIG_ARCH) \
	npm_config_nodedir=$(BUILD_DIR)/node-v$(PKG_NODE_VERSION)/ \
	PREFIX="$(PKG_INSTALL_DIR)/usr/" \
	$(STAGING_DIR_HOST)/bin/npm install -g $(PKG_BUILD_DIR)
endef

define Package/mqtt/install
	mkdir -p $(1)/usr/lib/node_modules/mqtt
	$(CP) -r $(PKG_INSTALL_DIR)/usr/lib/node_modules/mqtt/* $(1)/usr/lib/node_modules/mqtt/
endef

$(eval $(call BuildPackage,mqtt))

