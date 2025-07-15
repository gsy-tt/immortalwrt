include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

# 设备树源文件所在目录（你的源码路径）
SRC_DTS_DIR := $(CURDIR)/qcom
# 内核编译目录（目标路径）
DTS_DIR := $(LINUX_DIR)/arch/arm64/boot/dts

# 设备树列表（仅文件名，不含路径）
DTS_FILES := ipq5332-jdcloud-be6500

# 生成.dtb的规则：从源码目录复制到内核目录并编译
define DTS_template
$(DTS_DIR)/qcom/$(1).dtb: $(SRC_DTS_DIR)/$(1).dts
	# 确保内核目录存在
	mkdir -p $(DTS_DIR)/qcom
	# 复制源文件到内核目录（关键：预处理工具只能识别内核目录的文件）
	cp $(SRC_DTS_DIR)/$(1).dts $(DTS_DIR)/qcom/
	# 预处理并编译设备树
	$(call cmd,dtc)
endef

# 遍历所有设备树生成规则
$(foreach dts,$(DTS_FILES),$(eval $(call DTS_template,$(dts))))

clean:
	rm -f $(addprefix $(DTS_DIR)/qcom/,$(addsuffix .dtb,$(DTS_FILES)))
