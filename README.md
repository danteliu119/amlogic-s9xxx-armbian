试图解决 seewo-sv21 开发板dts设备树cpu频率不正常的问题，为编译方便（我菜），将所有ophub和unifreq都替换为了danteliu119
需fork以下repo
unifreq/linux-5.10.y-rk35xx
ophub/kernel
ophub/amlogic-s9xxx-armbian
ophub/firmware
替换所有danteliu119为你的用户名
dts瞎改的 来源参照：
rk3568-seewo-rubin
rk3568-seewo-new
rk3568-seewo-sv21_factory
以及 
liwei19920307/armbian
coolsnowwolf/lede


修改 linux-5.10.y/arch/arm64/boot/dts/rockchip/rk3568-seewo-sv21.dts
amlogic-s9xxx-armbian/build-armbian/armbian-files/common-files/etc/model_database.conf 中的 stable/6.6.y 为 rk35xx/5.10.y 可使用5.10.160内核

编译使用kernel中的compile-release-rk35xx-kernel，编译rk内核5.160
或者amlogic-s9xxx-armbian中的compile-kernel5.yml编译内核，Build armbian5编译armbian，Rebuild armbian5更新内核

root@armbian:~# lscpu
Architecture:            aarch64
  CPU op-mode(s):        32-bit, 64-bit
  Byte Order:            Little Endian
CPU(s):                  4
  On-line CPU(s) list:   0-3
Vendor ID:               ARM
  Model name:            Cortex-A55
    Model:               0
    Thread(s) per core:  1
    Core(s) per cluster: 4
    Socket(s):           -
    Cluster(s):          1
    Stepping:            r2p0
    CPU(s) scaling MHz:  71%
    CPU max MHz:         1992.0000
    CPU min MHz:         408.0000
    BogoMIPS:            48.00

sysbench cpu --cpu-max-prime=20000 --threads=4 run
General statistics:
    total time:                          10.0015s
    total number of events:              15822

比黑豹x2稍微高一点点 符合频率

网卡有一个，其它能力不足不看了。
