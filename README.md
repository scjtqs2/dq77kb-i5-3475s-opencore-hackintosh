# dq77kb-i5-3475s-opencore-hackintosh
opencore + macos `big sur` (11.6.5) 的 efi 配置。基本上完美。

## 硬件配置

| 配件           | 型号                                   | 说明                    |
|--------------|--------------------------------------|-----------------------|
| 主板           | Intel dq77kb                         |                       |
| CPU          | i5-3475s                             | 4核4线程                 |
| 内存           | 三星 ddr3 1600（笔记本）                    | 8G * 2                |
| 显卡           | HD 4000                              | DP * 1, HDMI * 1      |
| SSD          | 三星 1t ssd （引导+win） + nvme 1t (macos) | msata + pcie 4x转 nvme |
| 声卡           | APPLEALC仿冒                           | 注入ID 1                |
| 有线网卡         | intel 82579LM（红）                     | 千兆网卡                  |
| 无线网卡         | BCM94360CS2                          | 免驱                    |
| 电源           | DC电源                                 | DELL 120w             |
| 机箱           | SKTC M06                             | 前面板音频ok               |
| hackintosh版本 | 11.6.5                               |                       |

之前用的clover 引导,没什么问题。但是随着各种kext不再支持clover，因此迁移到opencore是一种趋势。

由于 mac `10.15` 很多app已经不兼容了。因此需要升级到 `big sur` + 版本。dq77kb最高也只能升级到 `big sur`了，12的系统核显已经不支持了（需要单独打显卡补丁），不过11的系统兼容性已经够了。

用我这个配置的话，自己记得改三码。用 2.61.1 的 occ（OpenCore Configurator)重新生成一下就行。

因为我网卡用的是 苹果的原生无线网卡，因此没有加任何其他bcm的驱动。也建议用转换器+原生网卡，这样wifi和蓝牙 一点问题也没有，甚至还能apple watch解锁。


## BIOS设置
先把BIOS恢复到默认设置

+ 关闭串口，将configuration/onboard devices/serial prot修改为disable
+ 禁用 VT-d，将secuity/intel vt directed i/o修改为disable
+ 确保BIOS快速启动与安全启动关闭，显存大于128mb，SATA mode为AHCI，一般dq77kb恢复默认即可