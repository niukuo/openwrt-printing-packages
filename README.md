# Printing packages for OpenWrt

fork from FranciscoBorges/openwrt-printing-packages

包含组件：
- Gutenprint 5.2.11
- Cups 1.6.3
- OpenPrinting's cups-filters 1.0.37
- poppler 0.24.1
.......


使用方法（在LEDE 17.01.6上测试通过）
1） add this line to your `feeds.conf` or `feeds.conf.default`
src-git printing git://github.com/obanat/openwrt-printing-packages.git

2）./scripts/feeds update -a

3）./scripts/feeds install -a

4）make menuconfig，Network > Printing 选择如下

  │ │  -*- cups................................ Common UNIX Printing System (daemon)       │ │
  │ │  <*>   cups-bjnp................................. BJNP protocol backend for CUPS     │ │
  │ │  <*> cups-bsd................ Common UNIX Printing System - BSD commands (old)       │ │
  │ │  <*> cups-client................ Common UNIX Printing System - Client commands       │ │
  │ │  <*> cups-ppdc....................... Common UNIX Printing System - PPDC utils       │ │
  │ │  < > ghostscript.................................................. ghostscript       │ │
  │ │  < > ghostscript-fonts-std.............................. ghostscript-fonts-std       │ │
  │ │  < > ghostscript-gnu-gs-fonts-other............ ghostscript-gnu-gs-fonts-other       │ │
  │ │  <*> gutenprint-cups............... gutenprint-cups -- Gutenprint CUPS drivers       │ │
  │ │  < > liberation-fonts........................................ liberation-fonts       │ │
  │ │  <*> openprinting-cups-filters...................... OpenPrinting CUPS filters       │ │
  │ │  < > p910nd............................... A small non-spooling printer server       │ │
  │ │  < > ubuntu-fonts................................................ ubuntu-fonts 

5）make V=s

6) enjoy!

最终编译后，在bin\packages\archxxxx\printing目录下生成如下文件：
cups_1.6.3-4_mips_24kc.ipk
cups-bjnp_1.2-1_mips_24kc.ipk
cups-bsd_1.6.3-4_mips_24kc.ipk
cups-client_1.6.3-4_mips_24kc.ipk
cups-ppdc_1.6.3-4_mips_24kc.ipk
gutenprint-cups_5.2.11-1_mips_24kc.ipk
lcms2_2.5-1_mips_24kc.ipk
libcups_1.6.3-4_mips_24kc.ipk
libcupscgi_1.6.3-4_mips_24kc.ipk
libcupsimage_1.6.3-4_mips_24kc.ipk
libcupsmime_1.6.3-4_mips_24kc.ipk
libcupsppdc_1.6.3-4_mips_24kc.ipk
libijs_0.35-1_mips_24kc.ipk
openprinting-cups-filters_1.0.37-2_mips_24kc.ipk
poppler_0.24.1-1_mips_24kc.ipk
qpdf_4.0.1-1_mips_24kc.ipk
我用的是魔改的720N，16M flash，最终编译出来的sysupgrade.bin是11M，完全可以接受

### Issues / Missing / TODO
添加打印机过程中，设置打印机参数完毕点确认后，会显示“broken pip”，此错误可以忽略，打印机可以正常添加。
