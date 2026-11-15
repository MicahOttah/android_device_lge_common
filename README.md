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
| `5a675e1` | v521: do not build the consumer IR HAL |

The consumer IR service is built from the CAF blob `libcir_driver.so` on
the other LG devices, and that blob does not exist for the V521.  Building
the AOSP `consumerir` service for the V521 instead fails at run time,
because the manifest of the service points at a service implementation that
is not in the ROM.  The whole module is therefore skipped for the V521.

## The port

The full description of the port is in the device tree:
<https://github.com/MicahOttah/android_device_lge_v521>
