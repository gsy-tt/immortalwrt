include $(TOPDIR)/rules.mk

# 平台基本信息（固定配置）
ARCH:=aarch64
BOARD:=ipq807x
BOARDNAME:=Qualcomm Atheros IPQ807x
FEATURES:=squashfs ramdisk fpu nand rtc emmc
KERNELNAME:=Image dtbs  # 声明需要编译内核镜像和设备树
CPU_TYPE:=cortex-a53
SUBTARGETS:=generic  # 子目标（可理解为平台细分型号）

KERNEL_PATCHVER:=5.15  # 内核版本

include $(INCLUDE_DIR)/target.mk  # 引入通用目标配置

# 默认预装的包（按需添加）
DEFAULT_PACKAGES += \
    kmod-usb3 kmod-leds-gpio kmod-ath11k-ahb \
    wpad-openssl uboot-envtools

# 关键：引用当前目录下的dts/Makefile（管理DTS文件）
# $(CURDIR) 表示当前目录：target/linux/ipq807x/
include $(CURDIR)/dts/Makefile

# 构建目标（固定格式）
$(eval $(call BuildTarget))
