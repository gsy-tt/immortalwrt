# 添加必要的包含文件，引入DTS_template宏
include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk  # 关键：引入DTS编译规则

DTS_DIR := $(LINUX_DIR)/arch/arm64/boot/dts

# 设备树文件列表（含路径）
DTS_FILES := \
    qcom/ipq5332-jdcloud-be6500  

# 定义DTS_template宏（如果引入kernel.mk后仍无效，手动添加）
define DTS_template
$(1).dtb: $(DTS_DIR)/$(1).dts
	$(call cmd,dtc)
endef

# 生成.dtb文件
$(foreach dts,$(DTS_FILES),$(eval $(call DTS_template,$(dts))))

# 清理规则
clean:
	rm -f $(addprefix $(DTS_DIR)/,$(addsuffix .dtb,$(DTS_FILES)))
