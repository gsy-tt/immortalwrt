include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/image.mk

define Device/jdcloud-be6500
	DEVICE_VENDOR := JDCloud
	DEVICE_MODEL := BE6500
	DEVICE_DTS := qcom/ipq5332-jdcloud-be6500
	# 关键：显式依赖DTS文件，确保复制完成后再编译
	DEPENDS += @(TARGET_ipq807x_generic)
	IMAGE/sysupgrade.bin := append-kernel | pad-to 16384k | append-rootfs | pad-to 128000k | sysupgrade-tar
endef
TARGET_DEVICES += jdcloud-be6500

$(eval $(call BuildImage))
