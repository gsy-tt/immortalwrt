include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/image.mk  # 关键：引入内置的prereq等规则
# 定义设备
define Device/jdcloud-be6500
  DEVICE_VENDOR := JDCloud
  DEVICE_MODEL := BE6500
  # 明确DTS路径（与dts/Makefile中的目标路径一致）
  DEVICE_DTS := qcom/ipq5332-jdcloud-be6500
  # 生成sysupgrade镜像的规则
  IMAGE/sysupgrade.bin := append-kernel | pad-to 16384k | append-rootfs | pad-to 128000k | sysupgrade-tar
endef
TARGET_DEVICES += jdcloud-be6500



$(eval $(call BuildImage))
