试图解决 seewo-sv21 开发板dts设备树cpu频率不正常的问题，为编译方便（我菜），将所有ophub和unifreq都替换为了danteliu119
需fork以下repo
unifreq/linux-5.10.y-rk35xx
ophub/kernel
ophub/amlogic-s9xxx-armbian
ophub/firmware
替换所有danteliu119为你的用户名
dts主要来自
rk3568-seewo-rubin
rk3568-seewo-new
rk3568-seewo-sv21_factory
以及 liwei19920307/armbian

有网就cpu不正常 cpu有400/1900就没网卡 还在探索中

修改 linux-5.10.y/arch/arm64/boot/dts/rockchip/rk3568-seewo-sv21.dts

编译使用kernel中的compile-release-rk35xx-kernel，编译rk内核5.160
或者amlogic-s9xxx-armbian中的compile-kernel5.yml编译内核，Build armbian5编译armbian，Rebuild armbian5更新内核
