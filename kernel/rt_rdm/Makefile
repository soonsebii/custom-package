#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=rt_rdm
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define KernelPackage/rt_rdm
  SUBMENU:=Other modules
  TITLE:=rt_rdm
  DEPENDS:=
  KCONFIG:=
  FILES:=$(PKG_BUILD_DIR)/rt_rdm.ko
  AUTOLOAD:=$(call AutoLoad,88,rt_rdm)
endef

define KernelPackage/rt_rdm/description
  Ralink Reg Debug Module.

  version tested
  --------------
  OK: Chaos Calmer. MT7628AN
endef  

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

TARGET_CFLAGS := \
    -DMT7628_ASIC_BOARD 

define Build/Compile
	$(MAKE) -C "$(LINUX_DIR)" \
		CROSS_COMPILE="$(TARGET_CROSS)" \
		ARCH="$(LINUX_KARCH)" \
		SUBDIRS="$(PKG_BUILD_DIR)" \
		EXTRA_CFLAGS="$(TARGET_CFLAGS)" \
		modules
endef

$(eval $(call KernelPackage,rt_rdm))
