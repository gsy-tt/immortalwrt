include $(TOPDIR)/rules.mk

DTS_DIR := $(LINUX_DIR)/arch/arm64/boot/dts/qcom
DTS_FILES := ipq5332-jdcloud-be6500
DTS_TARGETS := $(DTS_FILES)
$(DTS_DIR)/%.dts: $(CURDIR)/qcom/%.dts
   mkdir -p $(dir $@)
   cp -f $< $@
$(foreach dts,$(DTS_TARGETS),$(eval $(call DTS_template,$(dts))))

