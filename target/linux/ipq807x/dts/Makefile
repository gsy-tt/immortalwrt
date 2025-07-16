include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

# 源DTS路径（你的DTS存放位置）
SRC_DTS := $(CURDIR)/qcom/ipq5332-jdcloud-be6500.dts
# 目标路径（内核编译目录）
DST_DTS := $(LINUX_DIR)/arch/arm64/boot/dts/qcom/ipq5332-jdcloud-be6500.dts

# 定义复制规则：确保DTS被复制到内核目录
$(DST_DTS): $(SRC_DTS)
	@mkdir -p $(dir $@)
	@cp -f $< $@
	@echo "Copied DTS to kernel directory: $@"

# 将复制规则添加到内核构建依赖
$(eval $(call AddDependencyFiles,$(DST_DTS),$(SRC_DTS)))
$(eval $(call BuildKernel))
