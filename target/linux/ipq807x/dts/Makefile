include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

# 定义要编译的DTS文件名（不含路径和后缀）
DTS_FILES := ipq5332-jdcloud-be6500
# DTS文件存放路径（相对于当前目录）
DTS_DIR := $(CURDIR)/qcom

# 自动复制DTS到内核目录并编译的规则（OpenWRT标准写法）
define Build/Compile
	$(foreach dts,$(DTS_FILES), \
		$(KERNEL_MAKE_FLAGS) \
		DTBO=$(dts).dtbo \
		$(MAKE) -C $(LINUX_DIR) M=$(LINUX_DIR)/arch/arm64/boot/dts/qcom \
		$(dts).dtb; \
	)
endef

$(eval $(call BuildKernel))
