include $(TOPDIR)/rules.mk

# 定义设备
define Device/jdcloud-be6500
DEVICE_VENDOR := JDCloud
DEVICE_MODEL := BE6500
# 明确DTS路径（与dts/Makefile中的目标路径一致）
DEVICE_DTS := qcom/ipq5332-jdcloud-be6500
# 生成sysupgrade镜像的规则
IMAGE/sysupgrade.bin := append-kernel | pad-to 16384k | append-rootfs | pad-to 128000k | sysupgrade-tar
endef
TARGET_DEVICES += jdcloud-be6500

# 编译DTB的规则（依赖dts/Makefile中的复制规则）
$(BUILD_DIR)/image-$(DEVICE_DTS).dtb: $(DTS_DIR)/$(DEVICE_DTS).dts
	aarch64-openwrt-linux-musl-cpp -nostdinc -x assembler-with-cpp \
		-I$(LINUX_DIR)/arch/arm64/boot/dts \
		-I$(LINUX_DIR)/arch/arm64/boot/dts/include \
		-I$(LINUX_DIR)/include \
		-undef -D__DTS__ \
    -o $@.tmp $<
	dtc -O dtb -o $@ $@.tmp

# 保留image/Makefile的clean规则（删除冲突的旧规则后，此规则生效）
clean:
	rm -f $(BUILD_DIR)/image-*.dtb

$(eval $(call BuildImage))
