include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/image.mk

define Device/Default
	PROFILES := Default
	KERNEL_LOADADDR := 0x41000000
	DEVICE_DTS = $$(SOC)-$(lastword $(subst _, ,$(1)))
	DEVICE_DTS_CONFIG := config@1
	DEVICE_DTS_DIR := $(DTS_DIR)/qcom
	IMAGES := sysupgrade.bin
	IMAGE/sysupgrade.bin = sysupgrade-tar | append-metadata
	IMAGE/sysupgrade.bin/squashfs :=
endef
BE6500_DEVICE_NAME := jdcloud-be6500
BE6500_DEVICES := jdcloud-be6500

define Device/jdcloud-be6500
  $(Device/qcom-ipq53xx)
  DEVICE_VENDOR := jdcloud
  DEVICE_MODEL := be6500
  DEVICE_DTS := ipq5322-jdcloud-be6500
  DEVICE_PACKAGES := kmod-usb3 kmod-usb-ledtrig-usbport \
                     kmod-mmc kmod-sdhci kmod-sdhci-pci \
                     kmod-qca-nss-drv-ipq53xx kmod-qca-nss-drv-eth \
                     kmod-qca-nss-drv-pcie kmod-qca-nss-gmac \
                     kmod-ath11k-ahb kmod-ath11k-pci
endef
TARGET_DEVICES += jdcloud-be6500
include $(SUBTARGET).mk

$(eval $(call BuildImage))
