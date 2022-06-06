# openwrt-rtl8812au-rtl8821cu
Out of tree rtl8812au and rtl8821cu driver integration for OpenWrt, tested on 19.07.8. Contains Makefiles that pull drivers from https://github.com/morrownr with patches to make them compile on OpenWrt, also includes a patch that fixes a bug in rtl8821cu where connecting to 5GHz network is giving out `config_phydm_switch_bandwidth_8821c fail` error. 

## Steps

To compile the kernel modules for your specific device, following the steps below:

1. `git clone https://git.openwrt.org/openwrt/openwrt.git`
2. `cd openwrt`
3. `git checkout v19.07.8`
4. `./scripts/feeds update -a`
5. `./scripts/feeds install -a`
6. `wget https://downloads.openwrt.org/releases/19.07.8/targets/ar71xx/generic/config.buildinfo -o .config #This is to get the exact kernel config so the kernel module built is compatible with the device `
7. Extract the content of this repo to the openwrt directory, so folder structure is `package/kernel/rtl8812au/` and `package/kernel/rtl8821cu/`
8. `make defconfig`
9. `make -j $(nproc) download`
10. `make -j $(nproc)`
