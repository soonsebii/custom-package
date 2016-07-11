#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=reg
PKG_RELEASE:=1.0

PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/kernel.mk

define Package/reg
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+kmod-rt_rdm
  TITLE:=Userspace port of the MT7628AN reg manipulation tool
endef

define Package/reg/description
 Register the read/write test program.
 It works on MT7268AN (Linux 3.18) without using the kernel api.
endef

TARGET_CFLAGS := \
    -I$(KERNEL_BUILD_DIR)/rt_rdm

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Build/Configure
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		CC="$(TARGET_CC)" \
		CFLAGS="$(TARGET_CFLAGS)" \
		LDFLAGS="$(TARGET_LDFLAGS)"
endef

define Package/reg/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/reg $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,reg))
