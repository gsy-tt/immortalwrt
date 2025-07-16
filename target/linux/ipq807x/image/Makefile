include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/image.mk

# 定义设备
define Device/jdcloud-be6500
	DEVICE_VENDOR := JDCloud
	DEVICE_MODEL := BE6500
	DEVICE_DTS := qcom/ipq5332-jdcloud-be6500  # DTS相对路径
	IMAGE/sysupgrade.bin := append-kernel | pad-to 16384k | append-rootfs | pad-to 128000k | sysupgrade-tar
endef
TARGET_DEVICES += jdcloud-be6500

# 核心规则：编译DTB前自动复制DTS到内核目录
# $@：目标DTB文件（build_dir下的image-xxx.dtb）
# $<：源DTS文件（你的dts目录下的文件）
$(BUILD_DIR)/image-$(DEVICE_DTS).dtb: $(CURDIR)/../dts/$(DEVICE_DTS).dts
	# 1. 创建内核DTS目录（确保存在）
	mkdir -p $(dir $(LINUX_DIR)/arch/arm64/boot/dts/$(DEVICE_DTS).dts)
	# 2. 复制源DTS到内核目录（强制覆盖，避开清理）
	cp -f $< $(LINUX_DIR)/arch/arm64/boot/dts/$(DEVICE_DTS).dts
	# 3. 编译DTB（使用OpenWRT的工具链）
	aarch64-openwrt-linux-musl-cpp -nostdinc -x assembler-with-cpp \
		-I$(LINUX_DIR)/arch/arm64/boot/dts \
		-I$(LINUX_DIR)/arch/arm64/boot/dts/include \
		-I$(LINUX_DIR)/include \
		-undef -D__DTS__ \
		-o $@.tmp $(LINUX_DIR)/arch/arm64/boot/dts/$(DEVICE_DTS).dts
	dtc -O dtb -o $@ $@.tmp

# 确保安装阶段依赖DTB文件
install: $(BUILD_DIR)/image-$(DEVICE_DTS).dtb

$(eval $(call BuildImage))
