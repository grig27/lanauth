include $(TOPDIR)/rules.mk

PKG_NAME:=lanauth
PKG_RELEASE:=1
#PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/lanauth
	SECTION:=net
	CATEGORY:=Network
	TITLE:=lanauth -- Kabinet authenticator
endef

define Package/lanauth/description
	Kabinet authenticator.
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		LIBS="-nodefaultlibs -lc" \
		LDFLAGS="$(EXTRA_LDFLAGS) -L$(TOPDIR)/staging_dir/mipsel/usr/lib -I$(TOPDIR)/staging_dir/mipsel/usr/include" \
		CFLAGS="$(TARGET_CFLAGS) -L$(TOPDIR)/staging_dir/mipsel/usr/lib -I$(TOPDIR)/staging_dir/mipsel/usr/include" -I"$(PKG_BUILD_DIR)/src/include" \
		$(TARGET_CONFIGURE_OPTS) \
		CROSS="$(TARGET_CROSS)" \
		ARCH="$(ARCH)" \
		$(1);
endef

define Package/lanauth/install
	$(INSTALL_DIR) $(1)/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/lanauth $(1)/bin/
endef


$(eval $(call BuildPackage,lanauth))
