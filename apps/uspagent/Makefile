# WARNING: Automatically generated file using BAF (Build system Agnostic File) tooling (version 2.40.3)
# WARNING: You should contribute changes to https://gitlab.com/soft.at.home/usp/applications/uspagent/-/blob/main/baf.yml instead
include $(TOPDIR)/rules.mk

PKG_NAME:=uspagent
RAW_VERSION:=v5.4.4
PKG_VERSION:=$(if $(filter v0% v1% v2% v3% v4% v5% v6% v7% v8% v9%,$(RAW_VERSION)),$(patsubst v%,%,$(RAW_VERSION)),$(RAW_VERSION))
SHORT_DESCRIPTION:=USP agent as specified by TR-369

PKG_SOURCE:=uspagent-v5.4.4.tar.gz
PKG_SOURCE_URL:=https://gitlab.com/soft.at.home/usp/applications/uspagent/-/archive/v5.4.4
PKG_HASH:=75e7b4fbeb83359e8ce826b20aab89f470a9385c870ca8319c9c17e5bb5df10e
PKG_BUILD_DIR:=$(BUILD_DIR)/uspagent-v5.4.4
PKG_MAINTAINER:=Soft At Home <support.opensource@softathome.com>
PKG_LICENSE:=BSD-2-Clause-Patent
PKG_LICENSE_FILES:=LICENSE

COMPONENT:=uspagent

PKG_RELEASE:=1

define SAHInit/Install
	install -d $(1)/etc/rc.d/
	ln -sfr $(1)/etc/init.d/$(COMPONENT) $(1)/etc/rc.d/S$(CONFIG_SAH_SERVICES_USPAGENT_START_ORDER)$(COMPONENT)
	ln -sfr $(1)/etc/init.d/$(COMPONENT) $(1)/etc/rc.d/K$(CONFIG_SAH_SERVICES_USPAGENT_STOP_ORDER)$(COMPONENT)
endef

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  CATEGORY:=SoftAtHome
  SUBMENU:=Applications
  TITLE:=$(SHORT_DESCRIPTION)
  URL:=https://gitlab.com/soft.at.home/usp/applications/uspagent
  DEPENDS += +libamxc
  DEPENDS += +libamxp
  DEPENDS += +libamxj
  DEPENDS += +libamxd
  DEPENDS += +libamxb
  DEPENDS += +libamxa
  DEPENDS += +libamxo
  DEPENDS += +libsahtrace
  DEPENDS += +libimtp
  DEPENDS += +libusp
  DEPENDS += +libuspi
  DEPENDS += +mod-dmext
  DEPENDS += +mod-amxb-usp
  MENU:=1
endef

define Package/$(PKG_NAME)/description
	USP agent as specified by TR-369
endef

define Build/Compile
	$(call Build/Compile/Default, STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PKG_CONFIG_PATH=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(RAW_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include PKG_CONFIG=$(PKG_CONFIG) CONFIG_SAH_SERVICES_USPAGENT_START_ORDER=$(CONFIG_SAH_SERVICES_USPAGENT_START_ORDER) CONFIG_SAH_SERVICES_USPAGENT_STOP_ORDER=$(CONFIG_SAH_SERVICES_USPAGENT_STOP_ORDER))
endef

define Build/Install
	$(call Build/Install/Default, install INSTALL=install D=$(PKG_INSTALL_DIR) DEST=$(PKG_INSTALL_DIR) STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PV=$(RAW_VERSION) PKG_CONFIG_LIBDIR=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(RAW_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include PKG_CONFIG=$(PKG_CONFIG) CONFIG_SAH_SERVICES_USPAGENT_START_ORDER=$(CONFIG_SAH_SERVICES_USPAGENT_START_ORDER) CONFIG_SAH_SERVICES_USPAGENT_STOP_ORDER=$(CONFIG_SAH_SERVICES_USPAGENT_STOP_ORDER))

	$(call SAHInit/Install,$(PKG_INSTALL_DIR))
endef

define Build/InstallDev
	$(call Build/Install/Default, install INSTALL=install D=$(STAGING_DIR) DEST=$(STAGING_DIR) STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PV=$(RAW_VERSION) PKG_CONFIG_LIBDIR=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(RAW_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include PKG_CONFIG=$(PKG_CONFIG) CONFIG_SAH_SERVICES_USPAGENT_START_ORDER=$(CONFIG_SAH_SERVICES_USPAGENT_START_ORDER) CONFIG_SAH_SERVICES_USPAGENT_STOP_ORDER=$(CONFIG_SAH_SERVICES_USPAGENT_STOP_ORDER))
	$(call SAHInit/Install,$(STAGING_DIR))
endef

define Package/$(PKG_NAME)/install
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
	if [ -d ./files ]; then \
		$(CP) ./files/* $(1)/; \
	fi
	find $(1) -name *.a -exec rm {} +;
	find $(1) -name *.h -exec rm {} +;
	find $(1) -name *.pc -exec rm {} +;
endef

define Package/$(PKG_NAME)/config
	source "$(SOURCE)/Config.in"
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
