# android_device_lge_common

Fork of `LineageOS/android_device_lge_common` with the changes of the **LG
G Pad X 8.0 (V521)** port to **LineageOS 15.1** (Android 8.1).

| Branch | What it is |
| --- | --- |
| `lineage-15.1` | the upstream LineageOS 15.1 branch, unchanged |
| `lineage-15.1-v521` | the branch the V521 port builds from |

## What is different on `lineage-15.1-v521`

| Commit | Subject |
| --- | --- |
| `7a9c238` | v521: do not build LG's own consumer IR service |

The consumer IR service of the other LG devices is not the AOSP one: it
drives LG's IR transmitter over the device's own UART (`/dev/ttyHSL1`) and
gets the transmit function from the CAF blob `libcir_driver.so`, which is
only in the blob sets of the g2, g3, g4 and msm8996 (joan) devices.

`device/lge/common/Android.mk` includes every makefile under it for every
LG device, so the module was built for the V521 as well and the build
stopped with

```
device/lge/common/consumerir/Android.mk: error:
    android.hardware.ir@1.0-service.lge (EXECUTABLES android-arm)
    missing libcir_driver (SHARED_LIBRARIES android-arm)
```

The V521 does not need that service - its transmitter is on SPI6, and the
AOSP service loads the CAF blob `consumerir.msm8952.so` instead - so only
the LG specific module is skipped.

## The port

The full description of the port is in the device tree:
<https://github.com/MicahOttah/android_device_lge_v521>
