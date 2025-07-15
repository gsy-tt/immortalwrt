#
# Copyright (C) 2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

DTS_DIR := $(LINUX_DIR)/arch/arm64/boot/dts

# 设备树文件列表（不含 .dts 后缀）
DTS_FILES := \
    qcom/ipq5332-jdcloud-be6500  

# 默认编译所有设备树
DTS_TARGETS := $(DTS_FILES)

# 生成 .dtb 文件的规则
$(foreach dts,$(DTS_TARGETS),$(eval $(call DTS_template,$(dts))))

# 清理规则
clean:
    rm -f $(addprefix $(DTS_DIR)/,$(addsuffix .dtb,$(DTS_FILES)))
