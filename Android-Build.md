#Android 之 Build 类.(Android 获取手机配置信息)[参考1](https://blog.csdn.net/gjy211/article/details/52015198)

##一、类结构

  android.os.Build

##二、类概述

    从系统属性中提取设备硬件和版本信息。
    
##  三、内部类：

1、Build.VERSION    各种版本字符串

2、Build.VERSION_CODES    目前已知的版本代码的枚举类

## 四、常量：UNKNOWN   当一个版本属性不知道时所设定的值。其字符串值为 "unknown" .

## 五、构造方法： Build ()

## 六、静态属性

1、BOARD   主板：The name of the underlying board, like "goldfish".

2、BOOTLOADER 系统启动程序版本号：The system bootloader version number.

3、BRAND  系统定制商：The consumer-visible brand with which the product/hardware will be associated, if any.

4、CPU_ABI  cpu指令集：The name of the instruction set (CPU type + ABI convention) of native code.

5、CPU_ABI2 cpu指令集2：The name of the second instruction set (CPU type + ABI convention) of native code.

6、DEVICE 设备参数：The name of the industrial design.

7、DISPLAY  显示屏参数：A build ID string meant for displaying to the user

8、FINGERPRINT   唯一识别码：A string that uniquely identifies this build. Do not attempt to parse this value.

9、HARDWARE   硬件名称：The name of the hardware (from the kernel command line or /proc).

10、HOST

11、ID  修订版本列表：Either a changelist number, or a label like "M4-rc20".

12、MANUFACTURER  硬件制造商：The manufacturer of the product/hardware.

13、MODEL  版本即最终用户可见的名称：The end-user-visible name for the end product.

14、PRODUCT 整个产品的名称：The name of the overall product.

15、RADIO  无线电固件版本：The radio firmware version number.   在API14后已过时。使用 getRadioVersion()代替。

16、SERIAL 硬件序列号：A hardware serial number, if available. Alphanumeric only, case-insensitive.

17、TAGS  描述build的标签,如未签名，debug等等。：Comma-separated tags describing the build, like "unsigned,debug".

18、TIME

19、TYPE build的类型：The type of build, like "user" or "eng".

20、USER

//BOARD 主板
String phoneInfo = "BOARD: " + android.os.Build.BOARD;
phoneInfo += ", BOOTLOADER: " + android.os.Build.BOOTLOADER;
//BRAND 运营商
phoneInfo += ", BRAND: " + android.os.Build.BRAND;
phoneInfo += ", CPU_ABI: " + android.os.Build.CPU_ABI;
phoneInfo += ", CPU_ABI2: " + android.os.Build.CPU_ABI2;
//DEVICE 驱动
phoneInfo += ", DEVICE: " + android.os.Build.DEVICE;
//DISPLAY 显示
phoneInfo += ", DISPLAY: " + android.os.Build.DISPLAY;
//指纹
phoneInfo += ", FINGERPRINT: " + android.os.Build.FINGERPRINT;
//HARDWARE 硬件
phoneInfo += ", HARDWARE: " + android.os.Build.HARDWARE;
phoneInfo += ", HOST: " + android.os.Build.HOST;
phoneInfo += ", ID: " + android.os.Build.ID;
//MANUFACTURER 生产厂家
phoneInfo += ", MANUFACTURER: " + android.os.Build.MANUFACTURER;
//MODEL 机型
phoneInfo += ", MODEL: " + android.os.Build.MODEL;
phoneInfo += ", PRODUCT: " + android.os.Build.PRODUCT;
phoneInfo += ", RADIO: " + android.os.Build.RADIO;
phoneInfo += ", RADITAGSO: " + android.os.Build.TAGS;
phoneInfo += ", TIME: " + android.os.Build.TIME;
phoneInfo += ", TYPE: " + android.os.Build.TYPE;
phoneInfo += ", USER: " + android.os.Build.USER;
//VERSION.RELEASE 固件版本
phoneInfo += ", VERSION.RELEASE: " + android.os.Build.VERSION.RELEASE;
phoneInfo += ", VERSION.CODENAME: " + android.os.Build.VERSION.CODENAME;
//VERSION.INCREMENTAL 基带版本
phoneInfo += ", VERSION.INCREMENTAL: " + android.os.Build.VERSION.INCREMENTAL;
//VERSION.SDK SDK版本
phoneInfo += ", VERSION.SDK: " + android.os.Build.VERSION.SDK;
phoneInfo += ", VERSION.SDK_INT: " + android.os.Build.VERSION.SDK_INT

## 七、公共方法：

public static String getRadioVersion() 获取无线电固件版本  


