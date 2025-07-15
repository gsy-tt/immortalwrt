include $(TOPDIR)/rules.mk

DTS_DIR := $(LINUX_DIR)/arch/arm64/boot/dts/qcom
DTS_FILES := ipq5332-jdcloud-be6500
DTS_TARGETS := $(DTS_FILES)

# 自动复制DTS文件的规则（核心）
$(DTS_DIR)/%.dts: $(CURDIR)/qcom/%.dts
    mkdir -p $(dir $@)
    cp -f $< $@

# 生成.dtb的规则
$(foreach dts,$(DTS_TARGETS),$(eval $(call DTS_template,$(dts))))

# 删除以下clean规则，避免冲突
# clean:
#     rm -f $(addprefix $(DTS_DIR)/,$(addsuffix .dtb,$(DTS_FILES)))
