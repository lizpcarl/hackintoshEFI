# hackintoshEFI
Hackintosh EFI files for Z370-HD3 + i7-8700k +Intel 6000p NVMe + rx580 8g || MSI-B75m + E3-1240v2/i5-3550 + GT730 || GA-B250m + i5-7500 + rx560 4.




---
#多款机型的EFI包。
主要参考网站：[OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide)

手头有以下几种PC机安装MacOS.附上相应的EFI包，需要自己替换序列号等三码。

##GA-Z370-HD3
| 规格   | 详细信息                                                     |
| ------ | ------------------------------------------------------------ |
| CPU    | 3.7 GHz 六核Intel Core i7-8700k                            |
| 主板   | GA-Z370-HD3                                                  |
| 显卡   | Radeon RX 580 8 GB 2048sp 祥祺                                    |
| 内存   | G-skill 16 GB 2400 MHz DDR4 |
| 主硬盘 | 英特尔（Intel） Intel 6000p NVMe 256GB M.2                         |
| macOS | Ventura 版本13.0.1 (22A400)                                   |

##GA-B75m
| 规格   | 详细信息                                                     |
| ------ | ------------------------------------------------------------ |
| CPU    | 3.3 GHz 四核Intel Xeon E3-1230v2                             |
| 主板   | GA-B75m                                 |
| 显卡   | Radeon RX 560 4 GB Sapphire           |
| 内存   | Kingston DDR3 1600 MHz 8 GB X 2 |
| 主硬盘 | Teclast 512GB SSD                        |
| macOS | Monetery 版本12.6.1                                   |

##MSI-B75m+e3-1240v2+GT730+macOS12.6.1
| 规格   | 详细信息                                                     |
| ------ | ------------------------------------------------------------ |
| CPU    | 3.4 GHz 四核Intel Xeon E3-1240v2/i5-3550                             |
| 主板   | MSI-B75m-31                                 |
| 显卡   | NVIDIA GeForce GT 730 1023 MB           |
| 内存   | Kingston DDR3 1600 MHz 8 GB X 2            |
| 主硬盘 | PANASONIC RP-SSB120GAK SSD/Teclast 512GB SSD                        |
| 网卡   | Realtek RTL8168E-VL/8111E-VL PCI Express Gigabit Ethernet |
| macOS | Monetery 版本12.6.1                                    |

##GA-B250m
| 规格   | 详细信息                                                     |
| ------ | ------------------------------------------------------------ |
| CPU    | 3.4 GHz 四核Intel Core i5-7500                             |
| 主板   | GA-B250m                                 |
| 显卡   | AMD Radeon RX 560 4 GB 1024sp XFX讯景RX 560 4G 战狼版           |
| 内存   | Kingston 8 GB 2400 MHz DDR4           |
| 主硬盘 | Liteon T10 120G 128GB NVMe M.2                        |
| 网卡   | Realtek RTL8168E-VL/8111E-VL PCI Express Gigabit Ethernet |
| macOS | Monetery 版本12.6.1                                    |
(设备ID：0x67ef,修正版ID：0x00e5,shikigva=80)12.6.1 (21G217)
revision-id:Data:E5000000;device-id:Data:0210EF67



---
#支持AMD 2048sp的RX580显卡
用在z370主板(MacOS ver 12.6.1、13.0.1)的系统上仿冒RX580,8G,2048sp显卡，实体显卡为祥祺rx580 8g显卡（京东上395元购入）.

仿冒正式版的RX580，参考[这里](https://bbs.pcbeta.com/viewthread-1802638-1-1.html),[黑苹果星球](https://heipg.cn/tutorial/spoof-gpu-device-id.html)，(http://www.zztongyun.com/article/显卡型号修改)；
上有复杂的多种方案，但不值得看，太繁杂没有重点。
```
			<key>PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x0)</key>
			<dict>
				<key>device-id</key>
				<data>32cAAA==</data>
				<key>model</key>
				<string>Radeon RX 580</string>
				<key>revision-id</key>
				<data>wgAAAA==</data>
			</dict>
```
此处的原ID按Hex查看是0xDF670000，修正id为0xC2000000.

以下第一部分为AppleALC音频的layout-id选项，可以在boot-args的alcid=1另外指定。
```

			<dict>
				<key>layout-id</key>
				<integer>1</integer>
			</dict>
```

Z370主板的i7-8700k核显补丁，完美驱动核显U630.
```
			<key>PciRoot(0x0)/Pci(0x2,0x0)</key>
			<dict>
				<key>AAPL,ig-platform-id</key>
				<data>BwCbPg==</data>
				<key>framebuffer-patch-enable</key>
				<data>AQAAAA==</data>
				<key>framebuffer-stolenmem</key>
				<data>AAAwAQ==</data>
				<key>framebuffer-con1-enable</key>
				<data>AQAAAA==</data>
				<key>framebuffer-con1-type</key>
				<data>AAgAAA==</data>
				<key>framebuffer-con0-enable</key>
				<data>AQAAAA==</data>
				<key>framebuffer-con0-type</key>
				<data>AAgAAA==</data>
			</dict>
```


[E3-1230v2_GTX760_OpenCore](https://github.com/hunanhjx/E3-1230v2_GTX760_OpenCore.git)
在MSI B75M主板+Teclast512G_SSD上已经试验过，可以安装12.6.1版本


[Hac-z370hd3-efi](https://github.com/dione2017/Hac-z370hd3-efi.git)
在Ga Z370主板上已经可以boot起 B75m上安装的teclast512_SSD硬盘，但没有独显驱动。


[MSI-B250M-G1-Gamer-i5-7500-rx460macos12-EFI](https://github.com/wshdliu/MSI-B250M-G1-Gamer-i5-7500-rx460macos12-EFI.git)
正在试验中。sanDisk16G,12.6.1


[macadmin-scripts](https://github.com/munki/macadmin-scripts.git)
下载macOS各版本的安装包，命令：sudo ./installinstallmacos.py 就会出现列表，选择需要的版本即可。



##创建启动U盘
###版本12.6
参考文章《How to Create a macOS Monterey Installation USB》(https://www.tonymacx86.com/threads/how-to-create-a-macos-monterey-installation-usb.313754/)
总结后主要分成以下几步：
1.通过前面的途径先下载到“安装macOS Monterey”安装包，这里下载到了12.6.1的pkg包，双击解压后，就有“安装到...”的目录了。
2.使用“磁盘工具”格式化一个16G的u盘，“Partition tab”，“Current and choose 1 Partition”，“GUID Partition Table”，Name:"USB"，Format:"Mac OS Extended (Journaled)"
3.使用
官方提供的安装指令
```
sudo /Applications/Install\ macOS\ Monterey.app/Contents/Resources/createinstallmedia --volume /Volumes/USB /Applications/Install\ macOS\ Monterey.app --nointeraction
```
由于我的安装文件在一个HP的U盘上，修改了路径，实际安装指令
```
sudo /Volumes/HP\ x796w/12.6.1/Install\ macOS\ Monterey.app/Contents/Resources/createinstallmedia --volume /Volumes/USB /Volumes/HP\ x796w/12.6.1/Install\ macOS\ Monterey.app --nointeraction
```

###版本13参考
From 《How to Create a macOS Ventura Installation USB》(https://www.tonymacx86.com/threads/how-to-create-a-macos-ventura-installation-usb.320675/)




---
#让Monterey正式版支持Kepler独显：GeForce Kepler Patcher V5
[Geforce-Kepler-patcher Github官方地址](https://github.com/chris1111/Geforce-Kepler-patcher)
[中文说明](https://heipg.cn/drivers/geforce-kepler-patcher-v5.html)
在MSI B75M-31的主板上，使用了E3-1230v2的EFI包，然后按github上述地址安装Kepler-patcher成功。可以正常驱动GA显卡，显示“NVIDIA GeForce GT 730 1023 MB”，分辨率：2560x1080@ 60.00Hz，非常完美。

在Asus P8-Z77主板上，使用E3-1240v2 + GTX760(2G)，使用Kepler-patcher完美驱动了。


