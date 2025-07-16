include $(TOPDIR)/rules.mk

# 平台基本信息（不变）
ARCH:=aarch64
BOARD:=ipq807x
BOARDNAME:=Qualcomm Atheros IPQ807x
FEATURES:=squashfs ramdisk fpu nand rtc emmc
KERNELNAME:=Image dtbs
CPU_TYPE:=cortex-a53
SUBTARGETS:=generic
KERNEL_PATCHVER:=5.15

include $(INCLUDE_DIR)/target.mk

DEFAULT_PACKAGES += \
    kmod-usb3 kmod-leds-gpio kmod-ath11k-ahb \
    wpad-openssl uboot-envtools

# 关键修正：用 $(TOPDIR) 拼接绝对路径
# $(TOPDIR) 是源码根目录，直接指向 ipq807x/dts/Makefile
# include $(TOPDIR)/target/linux/ipq807x/dts/Makefile

$(eval $(call BuildTarget))
