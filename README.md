# Device Tree overlays for RockChip devices

## Version

Initial work to get DT-overlay working on RK SoCs (4.4 Kernel)
This repo is based on https://github.com/armbian/sunxi-DT-overlays but will be adjusted to RK-Devices
## Technical info

##### Requirements

- mainline u-boot 2017.03 or newer with `CONFIG_OF_LIBFDT_OVERLAY` enabled
- existing armbianEnv.txt with correct `overlay_prefix` value
- Device Tree compiler with overlays support for compiling the overlays

Notes:

##### Implementation details

Boot script reads `/boot/armbianEnv.txt` which may contain following environment variables:

- `overlay_prefix`
- `overlays`
- `user_overlays`
- overlay specific parameters

Overlay files referenced by `overlays` and `user_overlays` variables are loaded and applied using `fdt apply` command. After applying all overlays a SoC specific fixup script is executed to process overlay specific parameters.

