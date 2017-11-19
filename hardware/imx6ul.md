# NXP i.MX6UL

Expanding the i.MX 6 series, the i.MX 6UltraLite is a high performance, ultra-efficient processor family featuring an advanced implementation of a single ARM® Cortex®-A7 core. The Pico variant is pin-compatible with the Intel® Edison for sensors and low-speed I/O, but also adds additional expansion possibilities for multimedia and connectivity, giving you cutting edge technology that can easily be expanded and implemented for IoT designs.

从 i.MX 6 系列中扩展而来, i.MX 6UltraLite 是一个高性能，非常高效的处理器家族，采用的是单个ARM® Cortex®-A7核。 Pico 版本的是跟 Intel® Edison 管脚兼容的为传感器和低速 I/O 设计的, 但同时具备多媒体和联网的功能扩展可能性,是能够很容易用于 IoT 设计的前沿技术。
![](https://developer.android.google.cn/things/images/nxp-pico7-board.png) ![](https://developer.android.google.cn/things/images/nxp-spriot-board.png) ![](https://developer.android.google.cn/things/images/nxp-argon-board.png)

## Flashing the image

## 烧录映象

* * *

Before you begin flashing, you will need the following items in addition to your board:

烧录前除了板子还需要下面几项:

*   USB-C or Micro-USB cable

*   USB-C or Micro-USB 线

*   5V DC power adapter (not needed for the Pico i.MX6UL board)

*   5V 直流适配器 ( Pico i.MX6UL 板子不需要)

To flash Android Things onto your board, download the latest preview image in the [Android Things Console](https://partner.android.com/things/console) (see the [release notes](https://developer.android.google.cn/things/preview/releases.html)) and follow these steps:

为了烧录 Android Things 到板子上, 从 [Android Things Console](https://partner.android.com/things/console) 下载最新的映像(看下 [release notes](https://developer.android.google.cn/things/preview/releases.html)) 并按一下步骤来做:
### Step 1: Connect the Hardware

### Step 1: 连上硬件

Connect the board to your host computer:

连接板子到主机:


**For Pico i.MX6UL:**

**对于Pico i.MX6UL板:**

![""](https://developer.android.google.cn/things/images/pico7-connections.png)

1.  Connect a USB-C cable from your host computer to the USB OTG connector.

    把板子上的USB OTG接口和主机之间用 USB-C线连起来。
    

**For SprIoT i.MX6UL:**

**对于 SprIoT i.MX6UL板:**

![""](https://developer.android.google.cn/things/images/spriot-connections.png)

1.  Connect a Micro-USB cable to the USB OTG connector.

    把板子上的USB OTG接口和主机之间用 USB-C线连起来。

2.  Connect a 5V power adapter to the power input connector.

    连一个5V 电源适配器到电源输入接口


**For Argon i.MX6UL:**

**对于Argon i.MX6UL板:**

![""](https://developer.android.google.cn/things/images/vvdn-connections.png)

1.  Ensure switch **SW1** is in the **OFF** position.

    确保开关 **SW1** 保持在 **关** 。
2.  Connect a Micro-USB cable to the **OTG** (**J7**) connector.

    用Micro-USB 线连到 **OTG** (**J7**) 接口。
3.  Connect a 5V power adapter to the power input (**J2**) connector.
    
    用5V电源适配器连电源输入接口(**J2**)。
4.  Move **SW1** to the **ON** position to power the board.

    把 **SW1** 切换到**开** 给板子上电。

### Step 2: Flash Android Things

### 第二步： 烧录 Anroid Things 


Use the following steps to flash the Android image:

使用下面步骤来烧录 Android 映像：


1.  Download and install [Android Studio](https://developer.android.google.cn/studio/index.html) or the [`sdkmanager`](https://developer.android.google.cn/studio/command-line/sdkmanager.html) command-line tool. Update the Android SDK Platform Tools to version 25.0.3 or later from the [SDK Manager](https://developer.android.google.cn/studio/intro/update.html#sdk-manager).

   下载并安装 [Android Studio](https://developer.android.google.cn/studio/index.html) 或者安装 [`sdkmanager`](https://developer.android.google.cn/studio/command-line/sdkmanager.html) 命令行工具。从 [SDK Manager](https://developer.android.google.cn/studio/intro/update.html#sdk-manager)更新 Android SDK Platform Tools 到 25.0.3 版或者更新版本。

    *   Navigate to the Android SDK location on your computer; the path can be found in the system settings for Android Studio. Verify that the `fastboot` binary is installed in the `platform-tools/` directory.
    
    *   Navigate to the Android SDK location on your computer; the path can be found in the system settings for Android Studio. Verify that the `fastboot` binary is installed in the `platform-tools/` directory.
    *   找到你电脑上的 Android SDK 的位置; 路径可以在Android Studio的设置里面找到。确认 `fastboot` 在 `platform-tools/` 目录里。

    *   After you have the fastboot tool, add it to your `PATH` [environment variable](https://developer.android.google.cn/studio/command-line/variables.html#set). This command should be similar to the following:

    *   After you have the fastboot tool, add it to your `PATH` [environment variable](https://developer.android.google.cn/studio/command-line/variables.html#set). This command should be similar to the following:

    *   如果已经装了fastboot, 加到 `PATH` [环境变量](https://developer.android.google.cn/studio/command-line/variables.html#set)里面。命令如同如下:

        `export PATH=$PATH:"path/to/fastboot"`

2.  Open a command line terminal and navigate to the unzipped image directory.

    打开一个命令行终端并进到解开映像的目录。

3.  Verify that the device has booted into Fastboot mode by executing the following command:

     执行下面命令确保板子进入了fastboot 模式:

        $ fastboot devices1b2f21d4e1fe0129        fastboot

    <aside class="note">**Note:** <span>Your device will not boot into Fastboot mode if it was previously flashed with Android Things. You need to first execute the following command using the [adb tool](https://developer.android.google.cn/tools/help/adb.html) to reboot the device into Fastboot mode.

<aside class="note">**Note:** <span>如何前面已经烧了Android Things 映像，板子会进入不了 fastboot 模式。 这样就需要用[adb tool](https://developer.android.google.cn/tools/help/adb.html)执行下面命令使得板子进入 fastboot 模式。

        $ adb reboot bootloader</span></aside>

4.  Execute the `flash-all.sh` script. This script installs the necessary bootloader, baseband firmware(s), and operating system. (On Windows systems, use `flash-all.bat` instead).

   执行 `flash-all.sh` 脚本。 此脚本会安装 bootloader, 基带固件, 和操作系统 (On Windows systems, use `flash-all.bat` instead).

    <aside class="note">**Note:** <span>The device automatically reboots into Android Things when the process is complete.</span></aside>

5.  To verify that Android is running on the device, discover it using the [adb tool](https://developer.android.google.cn/tools/help/adb.html):

   为了验证 Android 正在板子上跑，可以用 [adb tool](https://developer.android.google.cn/tools/help/adb.html)执行如下命令:

        $ adb wait-for-device...$ adb devicesList of devices attached1b2f21d4e1fe0129        device

## Connecting Wi-Fi

* * *

After flashing your board, it is strongly recommended to connect it to the internet. This allows your device to deliver crash reports and receive updates.

<aside class="note">**Note:** <span>The device doesn't need to be on the same network as your computer.</span></aside>

Before connecting your board to a Wi-Fi network, attach an external IPEX or u.FL Wi-Fi antenna to your board as shown:

**For Pico i.MX6UL:**

![""](https://developer.android.google.cn/things/images/pico7-antenna.png)

**For SprIoT i.MX6UL:**

![""](https://developer.android.google.cn/things/images/spriot-antenna.png)

**For Argon i.MX6UL:**

![""](https://developer.android.google.cn/things/images/vvdn-antenna.png)

<aside class="note">**Note:** <span>The module can't resolve Wi-Fi signals if you proceed without connecting an antenna.</span></aside>

To connect your board to Wi-Fi, first access a shell prompt on the device. You can use either of the following methods:

*   Open a shell over adb with the `adb shell` command.
*   Connect to the [serial console](#serial_debug_console).

Once you can access a shell prompt, follow these steps:

1.  Send an intent to the Wi-Fi service that includes the SSID of your local network. Your [board](https://developer.android.google.cn/things/hardware/developer-kits.html) must support the network protocol and frequency band of the wireless network in order to establish a connection.

        $ am startservice \    -n com.google.wifisetup/.WifiSetupService \    -a WifiSetupService.Connect

    The following arguments are supported with this command:

    <table>

    <tbody>

    <tr>

    <th style="width: 240px;">Argument</th>

    <th>Description</th>

    </tr>

    <tr>

    <td>`-e ssid <var>network_ssid</var>`</td>

    <td>Connect to the wireless network SSID specified by <var>network_ssid</var>. _This argument is required_.</td>

    </tr>

    <tr>

    <td>`-e passphrase <var>network_pass</var>`</td>

    <td>Optional argument to use the passcode specified by <var>network_pass</var> to connect to the network SSID. This argument is not necessary if your network doesn't require a passcode.</td>

    </tr>

    <tr>

    <td>`-e passphrase64 <var>encoded_pass</var>`</td>

    <td>Optional argument used in place of `passphrase` for passcodes with special characters (`space, !, ", $, &, ', (, ), ;, <, >, `, or |`). Use [base64 encoding](https://www.base64encode.org/) to specify the value for <var>encoded_pass</var>.</td>

    </tr>

    <tr>

    <td>`--ez hidden true`</td>

    <td>Optional argument to indicate that the SSID specified in this command is hidden. If omitted, this value defaults to false.</td>

    </tr>

    </tbody>

    </table>

2.  Verify that the connection was successful through `logcat`:

    用 `logcat` 来验证连接成功:

        $ logcat -d | grep Wifi...V WifiWatcher: Network state changed to CONNECTEDV WifiWatcher: SSID changed: ...I WifiConfigurator: Successfully connected to ...

3.  Test that you can access a remote IP address:

    可以用访问一个远程 IP 地址来测试：

        $ ping 8.8.8.8PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.64 bytes from 8.8.8.8: icmp_seq=1 ttl=57 time=6.67 ms64 bytes from 8.8.8.8: icmp_seq=2 ttl=57 time=55.5 ms64 bytes from 8.8.8.8: icmp_seq=3 ttl=57 time=23.0 ms64 bytes from 8.8.8.8: icmp_seq=4 ttl=57 time=245 ms

4.  Check that the date and time are set correctly on the device:

     用如下命令来检查时间和日期在板子上设置
     
        $ date

    <aside class="note">**Note:** <span>An incorrect date or time may cause SSL errors. Restart the device to automatically set the correct date and time from a time server.</span></aside>

If you want to clear all of the saved networks on the board:

如果你想清除所有板子上保存下来的网络:

    $ am startservice \    -n com.google.wifisetup/.WifiSetupService \    -a WifiSetupService.Reset

## Serial debug console

## 调试串口
* * *

The serial console is a helpful tool for debugging your board and reviewing system log information. The console is the default output location for kernel log messages (i.e. `dmesg`), and it also provides access to a full shell prompt that you can use to access commands such as [logcat](https://developer.android.google.cn/tools/help/logcat.html). This is helpful if you are unable to access ADB on your board through other means and have not yet enabled a network connection.

串口是很有用的调试板子看系统打印信息的工具。 串口是内核打印信息的缺省输出口 (例如 `dmesg`), 串口能提供一个完全的命令行终端来执行类似 [logcat](https://developer.android.google.cn/tools/help/logcat.html)的命令。 如果此时板子不能用 ADB 命令来访问同时也不能联网时会特别有用。

To access the serial console:

连接串口:

**For Pico i.MX6UL:** Connect a micro USB cable to the debug interface as shown below.

**对 Pico i.MX6UL板:** 如下连 micro USB 线连到调试接口上
![""](https://developer.android.google.cn/things/images/pico7-console.png)

**For SprIoT i.MX6UL:** Connect a Micro-USB cable to the board as shown below.


**对 SprIoT i.MX6UL板:** 如下把 Micro-USB 线连到板子上。
![""](https://developer.android.google.cn/things/images/spriot-console.png)

**For Argon i.MX6UL:** Connect a USB Type B cable to the board as shown below.

**对 Argon i.MX6UL板:** 如下把 USB Type B 线连到板子上。
![""](https://developer.android.google.cn/things/images/vvdn-console.png)

Open a connection to the USB serial device on your development computer using a terminal program, such as [PuTTY](http://www.putty.org/) (Windows), [Serial](https://www.decisivetactics.com/products/serial/) (Mac OS), or [Minicom](https://en.wikipedia.org/wiki/Minicom) (Linux). The serial port parameters for the console are as follows:

使用串口终端程序在你的PC上打开 USB 串口设备, 例如 [PuTTY](http://www.putty.org/) (Windows下面), [Serial](https://www.decisivetactics.com/products/serial/) (Mac 下), 或者 [Minicom](https://en.wikipedia.org/wiki/Minicom) (Linux下)。串口的参数设置如下:
*   **Baud Rate**: 115200

*   **比特率**: 115200
*   **Data Bits**: 8

*   **数据位**: 8
*   **Parity**: None

*   **奇偶性**: None
*   **Stop Bits**: 1

*   **停止位**: 1

