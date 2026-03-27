# WARNING: Automatically generated file using BAF (Build system Agnostic File) tooling (version 2.40.3)
# WARNING: You should contribute changes to https://gitlab.com/soft.at.home/usp/applications/usp-endpoint/-/blob/main/baf.yml instead
include $(TOPDIR)/rules.mk

PKG_NAME:=usp-endpoint
RAW_VERSION:=v2.0.13
PKG_VERSION:=$(if $(filter v0% v1% v2% v3% v4% v5% v6% v7% v8% v9%,$(RAW_VERSION)),$(patsubst v%,%,$(RAW_VERSION)),$(RAW_VERSION))
SHORT_DESCRIPTION:=Mini USP agent or controller

PKG_SOURCE:=usp-endpoint-v2.0.13.tar.gz
PKG_SOURCE_URL:=https://gitlab.com/soft.at.home/usp/applications/usp-endpoint/-/archive/v2.0.13
PKG_HASH:=f0d9172a407500cd7e5a5e68a0b5a0e20c34316158f590dcaadaaa1dae81c22c
PKG_BUILD_DIR:=$(BUILD_DIR)/usp-endpoint-v2.0.13
PKG_MAINTAINER:=Soft At Home <support.opensource@softathome.com>
PKG_LICENSE:=BSD-2-Clause-Patent
PKG_LICENSE_FILES:=LICENSE

COMPONENT:=usp-endpoint

PKG_RELEASE:=1

define SAHInit/Install
	install -d $(1)/etc/rc.d/
	ln -sfr $(1)/etc/init.d/uspa $(1)/etc/rc.d/S99uspa
	ln -sfr $(1)/etc/init.d/uspa $(1)/etc/rc.d/K99uspa
	ln -sfr $(1)/etc/init.d/uspc $(1)/etc/rc.d/S99uspc
	ln -sfr $(1)/etc/init.d/uspc $(1)/etc/rc.d/K99uspc
	ln -sfr $(1)/etc/init.d/uspe $(1)/etc/rc.d/S99uspe
	ln -sfr $(1)/etc/init.d/uspe $(1)/etc/rc.d/K99uspe
endef

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  CATEGORY:=SoftAtHome
  SUBMENU:=Ambiorix
  TITLE:=$(SHORT_DESCRIPTION)
  URL:=https://gitlab.com/soft.at.home/usp/applications/usp-endpoint
  DEPENDS += +libamxc
  DEPENDS += +libamxd
  DEPENDS += +libamxm
  DEPENDS += +libamxp
  DEPENDS += +libamxb
  DEPENDS += +libamxo
  DEPENDS += +libimtp
  DEPENDS += +libusp
  DEPENDS += +libuspi
  DEPENDS += +libsahtrace
  DEPENDS += +mod-dmext
  MENU:=1
endef

define Package/$(PKG_NAME)/description
	Mini USP agent or controller
endef

define Build/Compile
	$(call Build/Compile/Default, STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PKG_CONFIG_PATH=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(RAW_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include PKG_CONFIG=$(PKG_CONFIG) CONFIG_SAH_SERVICES_USP-ENDPOINT_INSTALL_USPA=$(CONFIG_SAH_SERVICES_USP-ENDPOINT_INSTALL_USPA) CONFIG_SAH_SERVICES_USP-ENDPOINT_INSTALL_USPC=$(CONFIG_SAH_SERVICES_USP-ENDPOINT_INSTALL_USPC) CONFIG_SAH_SERVICES_USP-ENDPOINT_INSTALL_USPE=$(CONFIG_SAH_SERVICES_USP-ENDPOINT_INSTALL_USPE))
endef

define Build/Install
	$(call Build/Install/Default, install INSTALL=install D=$(PKG_INSTALL_DIR) DEST=$(PKG_INSTALL_DIR) STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PV=$(RAW_VERSION) PKG_CONFIG_LIBDIR=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(RAW_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include PKG_CONFIG=$(PKG_CONFIG) CONFIG_SAH_SERVICES_USP-ENDPOINT_INSTALL_USPA=$(CONFIG_SAH_SERVICES_USP-ENDPOINT_INSTALL_USPA) CONFIG_SAH_SERVICES_USP-ENDPOINT_INSTALL_USPC=$(CONFIG_SAH_SERVICES_USP-ENDPOINT_INSTALL_USPC) CONFIG_SAH_SERVICES_USP-ENDPOINT_INSTALL_USPE=$(CONFIG_SAH_SERVICES_USP-ENDPOINT_INSTALL_USPE))

	$(call SAHInit/Install,$(PKG_INSTALL_DIR))
endef

define Build/InstallDev
	$(call Build/Install/Default, install INSTALL=install D=$(STAGING_DIR) DEST=$(STAGING_DIR) STAGINGDIR=$(STAGING_DIR) CONFIGDIR=$(STAGING_DIR) PV=$(RAW_VERSION) PKG_CONFIG_LIBDIR=$(STAGING_DIR)/usr/lib/pkgconfig LIBDIR=/usr/lib INSTALL_LIB_DIR=/lib INSTALL_BIN_DIR=/bin RAW_VERSION=$(RAW_VERSION) HARDCO_HAL_DIR=$(STAGING_DIR)/usr/include PKG_CONFIG=$(PKG_CONFIG) CONFIG_SAH_SERVICES_USP-ENDPOINT_INSTALL_USPA=$(CONFIG_SAH_SERVICES_USP-ENDPOINT_INSTALL_USPA) CONFIG_SAH_SERVICES_USP-ENDPOINT_INSTALL_USPC=$(CONFIG_SAH_SERVICES_USP-ENDPOINT_INSTALL_USPC) CONFIG_SAH_SERVICES_USP-ENDPOINT_INSTALL_USPE=$(CONFIG_SAH_SERVICES_USP-ENDPOINT_INSTALL_USPE))
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
