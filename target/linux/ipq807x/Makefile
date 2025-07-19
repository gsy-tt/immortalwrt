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
#include $(TOPDIR)/target/linux/ipq807x/dts/Makefile

# 关键配置：指定要编译的DTS文件（相对于内核源码的arch/arm64/boot/dts/qcom目录）
# 假设你的ipq5332-jdcloud-be6500.dts在target/linux/ipq807x/dts/qcom/下
DEVICE_DTS := qcom/ipq5332-jdcloud-be6500

# 关键配置：指定.dtsi文件的搜索路径（绝对路径）
# 这里填你的ipq5332-base.dtsi所在的目录（和DTS文件同目录）
DTS_INCLUDE_DIRS += $(TOPDIR)/target/linux/ipq807x/dts/qcom

# 关键：原始.dts和.dtsi所在目录（你的文件目录）
ORIG_DTS_DIR := $(TOPDIR)/target/linux/ipq807x/dts/qcom
# 内核DTS目录（编译时实际使用的目录）
KERNEL_DTS_DIR := $(LINUX_DIR)/arch/arm64/boot/dts/qcom


# 强制复制.dtsi到内核目录（核心修复）
define Build/Prepare
    $(call Build/Prepare/Default)  # 保留默认准备步骤

    # 复制.dtsi到内核DTS目录，确保和DTS在同一目录
    @echo "复制文件: $(ORIG_DTS_DIR)/ipq5332-base.dtsi -> $(KERNEL_DTS_DIR)/"
    cp $(ORIG_DTS_DIR)/ipq5332-base.dtsi $(KERNEL_DTS_DIR)/ || echo "复制失败!"

    # 验证文件是否存在
    @echo "验证文件是否存在:"
    @ls -l $(KERNEL_DTS_DIR)/ipq5332-base.dtsi || echo "文件不存在!"
endef

$(eval $(call BuildTarget))
