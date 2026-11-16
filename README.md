# android_device_lge_common

Fork of `LineageOS/android_device_lge_common` for the **LG G Pad X 8.0 (V521)**
LineageOS 15.1 port.  The port builds from `lineage-15.1-v521`; the other
branches are upstream.

Changes:

* LG's UART consumer IR service is not built for the v521.  It needs
  `libcir_driver.so`, which the v521 does not have; the v521 transmitter is
  on SPI and uses the AOSP IR HAL.

Port and device tree: <https://github.com/MicahOttah/android_device_lge_v521>
