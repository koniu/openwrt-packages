#
# Copyright © 1997-2011 by Secret Labs AB
# Copyright © 1995-2011 by Fredrik Lundh
# Copyright © 2016 by Alex Clark and contributors
#

include $(TOPDIR)/rules.mk

PKG_NAME:=pillow
PKG_VERSION:=3.2.0
PKG_RELEASE=1
PKG_LICENSE:=CUSTOM
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/python-pillow/Pillow.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=344cb709ed0111adcc6ad47cc007507c3f5efeb3
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_BUILD_DEPENDS:=python python-setuptools

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/pillow
    SUBMENU:=Python
    SECTION:=lang
    CATEGORY:=Languages
    TITLE:=The friendly PIL fork
    MAINTAINER:=Gergely Kiss <mail.gery@gmail.com>
    URL:=https://www.pillowproject.com/
    DEPENDS:=+python +libfreetype +libjpeg +zlib +libtiff
endef

define Package/pillow/description
    The friendly PIL fork
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/pillow/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin
	$(CP) $(PKG_BUILD_DIR)/LICENSE $(1)$(PYTHON_PKG_DIR)/PIL/
endef

$(eval $(call BuildPackage,pillow))
