---
title: "自制机械键盘"
date: 2019-10-03 14:30:23 +0800
category: Wenuo
tags: Technology
excerpt: 本文主要讲述68机械键盘的制作过程。
---

## 自制68键机械键盘
​		一直想要做一个机械键盘来办公或者打游戏，在网上看到各式各样的键盘，但是没有我想要的款式（价格太高）有着技术宅和垃圾佬的双重身份的我:kissing:，便有了自制键盘的想法。

​		通过查找资料，自制键盘又称为客制化键盘，最早的客制化键盘是来自国外[Geekhack](https://geekhack.org/index.php "Geekhack") 论坛上一位大神开发的GH60键盘，共有三个版本。而国内客制化键盘始终没法开源，如Satan。而且在某宝上一块PCB将近200打样😭。



------



### 键盘原理图

- 主控MCU（引脚说明）  ![mcu](https://github.com/Wenuo/Mechanical-keyboard/raw/master/keyboard_mcu/atmega32u4_pin.png)

- 键盘使用了按键矩阵（5*16）

  <img src="https://github.com/Wenuo/Mechanical-keyboard/raw/master/keyboard_pcb/key.png" alt="KEY"  />
  
- CapsLock灯光设置（键盘没有背光，只装了Caps灯光）

- ISP接口（下载MCU的Bootloader）

- Micro_USB接口

- Reset按键（方便下载键盘新配列）

具体详见[键盘原理图](https://github.com/Wenuo/Mechanical-keyboard/raw/master/keyboard_pcb/keyboard_pcb.pdf "pdf") 

------



### 键盘PCB		

​		由于键盘上轴的位置特殊，为了得到键盘轴体最佳摆放位置。所以先制作键盘定位板，进入[键盘布局编辑器](http://www.keyboard-layout-editor.com/#/ "editor")制作想要的键盘布局，导出Raw Data。

```
["~\n`","!\n1","@\n2","#\n3","$\n4","%\n5","^\n6","&\n7","*\n8","(\n9",")\n0","_\n-","+\n=",{w:2},"Backspace",{a:7},""],
[{a:4,w:1.5},"Tab","Q","W","E","R","T","Y","U","I","O","P","{\n[","}\n]",{w:1.5},"|\n\\",{a:7},""],
[{a:4,w:1.75},"Caps Lock","A","S","D","F","G","H","J","K","L",":\n;","\"\n'",{w:2.25},"Enter",{a:7},""],
[{a:4,w:2.25},"Shift","Z","X","C","V","B","N","M","<\n,",">\n.","?\n/",{w:1.75},"Shift","Up",{a:7},""],
[{a:4,w:1.25},"Ctrl",{w:1.25},"Win",{w:1.25},"Alt",{a:7,w:6.25},"",{a:4},"Alt","Win","Menu","Left","Down","Right"]
```

​		将得到的Raw Data导入进[定位板制作器](http://builder.swillkb.com/ "editor")，得到定位板CAD[文件](https://github.com/Wenuo/Mechanical-keyboard/blob/master/keyboard_cad/keyboard_cad.dxf "CAD") 。

![定位板](https://github.com/Wenuo/Mechanical-keyboard/raw/master/keyboard_cad/gauge_plate_cad%20.png)

​		将CAD文件导入进Altium Designer软件里面，制作键盘轴体的位置机械层，然后依据原理图文件导入进PCB文件内，进行布局，走线。

<img src="https://github.com/Wenuo/Mechanical-keyboard/raw/master/keyboard_pcb/pcb_picture.png" alt="PCB" style="zoom:150%;" />

具体详见[PCB](https://github.com/Wenuo/Mechanical-keyboard/blob/master/keyboard_pcb/keyboard_pcb.pdf)

------

### 键盘组装

- PCB
- GATERON 轴体
  - 选取了G黄，手感介于Cherry红与黑轴手感之间。
- 主控MCU
  - 应用Atmega32U4作为中控
- USB数据线

