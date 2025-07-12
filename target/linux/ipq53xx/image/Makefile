include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/image.mk

define Image/BuildKernel
    $(call Image/BuildDTB,$(KDIR)/arch/arm64/boot/dts/qcom/qcom-ipq5332-be6500.dtb)
    cat $(KDIR)/Image $(KDIR)/arch/arm64/boot/dts/qcom/qcom-ipq5332-be6500.dtb > $(KDIR)/zImage
endef

define Image/Build
    $(call Image/Build/jffs2-128k)
    $(call Image/Build/squashfs)
endef

$(eval $(call BuildImage))
