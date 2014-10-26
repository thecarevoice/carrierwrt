## Getting Started

You need to have installed git, svn, gcc, g++, binutils, patch, bzip2, flex,
make, gettext, pkg-config, unzip, libz-dev, libncurses-dev, gawk and libc
headers. For example, on a Debian or Ubuntu based system run the command:

```
  apt-get install -y git subversion gcc g++ binutils patch bzip2 flex make \
                     gettext pkg-config unzip libz-dev libncurses-dev gawk \
                     gcc-multilib
```

Then:

1. git clone https://github.com/thecarevoice/carrierwrt.git

2. cd carrierwrt && make PRODUCT=hotspot TARGET=draginoV2

Basic build configuration is in config.mk. Functionality and default settings
are controlled through what we call product profiles and customizations (in
`products/*/Makefile`), e.g. the product entry for Thecarevoice is `products/hotspot/*`

## Add a new target for hotspot product

1. Copy a template dictionary into product named with your product name `xx`, e.g. `./product/ap/*`
2. Modify the follow files under `./product/xx/*`:
	* `./product/xx/Makefile` - Configuration for your product
	* `./product/xx/targets` - Different hardware/chipset platform for your product
	* `./product/xx/patches` - Patches modified by your product for the OpenWRT platform
	* `./product/ap/files` - Your customization files which will be installed into OpenWRT directly

## Add a new package for hotspot product

1. The package in the CarrierWRT is the same as OpenWRT, the only difference is that it is placed in the `./product/package/*`
2. Add the configuration flag into `./product/xx/Makefile` using `CONFIG_PACKAGE_XX=y`

## Add a patch for a package or OpenWRT platform

You can also add a patch for the OpenWRT platform or the package in the OpenWRT, as follow:

1. Make a dictionary in the `./patches/`, e.g. `./patches/uci` for `uci` package
2. Add the package enable flag into `./product/xx/Makefile` with `CONFIG_PACKAGE_uci=y`