include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

# 定义 DTS 文件名（不含路径和后缀）
DTS_FILES := ipq5332-jdcloud-be6500
# 源码 DTS 所在子目录（相对于当前目录）
DTS_SUBDIR := qcom

# 标准 DTS 编译模板（自动生成复制和编译规则）
define Device/DTS_template
  $(eval $(call KernelPackage/$(1)))
  $(eval $(call BuildDTS,$(1),$(DTS_SUBDIR)))
endef

$(foreach dts,$(DTS_FILES),$(eval $(call Device/DTS_template,$(dts))))

# 关联内核编译目标
$(eval $(call BuildKernel))
