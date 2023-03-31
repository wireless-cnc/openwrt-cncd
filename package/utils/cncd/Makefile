include $(TOPDIR)/rules.mk

PKG_NAME:=cncd
PKG_VERSION:=0.1
PKG_RELEASE:=$(AUTORELEASE)
PKG_REV:=master

PKG_MAINTAINER:=Glebka <Glebka@users.noreply.github.com>
PKG_LICENSE:=MIT

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/wireless-cnc/cncd.git
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_REV).tar.gz

include $(INCLUDE_DIR)/package.mk

define Package/cncd
	SECTION:=utils
	CATEGORY:=Utilities
	TITLE:=Control your GRBL CNC over WiFi
endef

define Package/cncd/description
	WebSocket server that re-transmits G-code commands and responses from / to serial conenction with GRBL board.
endef

define Build/Prepare
	$(PKG_UNPACK)
	$(Build/Patch)
endef

# Package build instructions; invoke the target-specific compiler to first compile the source file, and then to link the file into the final executable
define Build/Compile
	cd $(PKG_BUILD_DIR) && TARGET_CC=$(TARGET_CC) cargo build --release --target=mipsel-unknown-linux-musl
	$(STRIP) $(PKG_BUILD_DIR)/target/mipsel-unknown-linux-musl/release/cncd
endef

define Package/cncd/install
	$(CP) ./files/* $(1)/
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/target/mipsel-unknown-linux-musl/release/cncd $(1)/usr/bin
endef

$(eval $(call BuildPackage,cncd))
