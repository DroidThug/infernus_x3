The files in this directory are meant to be used as a base for Infernus base config. If you want to build a custom kernel with features, all options in infernus-custom.cfg enabled.
These enable advanced kernel features.

The way to enable these options would be:
```
     ARCH=arm64 scripts/kconfig/merge_config.sh arch/arm64/configs/infernus_defconfig infernus/configs/infernus-custom.cfg
```
This will generate a .config that can then be used to save a new defconfig or
compile a new kernel with advanced features enabled.
