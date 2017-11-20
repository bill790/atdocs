# NXP i.MX7D

# NXP i.MX7D 平台

The i.MX 7Dual delivers high-performance processing for low-power requirements with a high degree of functional integration. The i.MX 7Dual features an advanced implementation of two ARM®Cortex®-A7 cores, which operate at speeds of up to 1.2 GHz, as well as the ARM® Cortex®-M4 core. The Pico variant is pin-compatible with the Intel® Edison for sensors and low-speed I/O, but also adds additional expansion possibilities for multimedia and connectivity, giving you cutting edge technology that can easily be expanded and implemented for IoT designs.

i.MX 7Dual处理器是带有高度功能集成、低功耗、高性能的, 工作频率最高到 1.2 GHz, 核心是 ARM® Cortex®-M4。Pico 板和 Intel® Edison 板对传感器和低速 I/O 来讲是管脚兼容的,但也加了对多媒体和联网的扩展可能，这使得板子可以很容易的用到最新的 IoT 技术。
![""](https://developer.android.google.cn/things/images/nxp-pico7-board.png)

## Flashing the image

## 烧录映像

* * *

Before you begin flashing, you will need the following items in addition to your board:

烧录前除了板子还需要下面几项:

*   USB-C cable
    
   USB-C 线
    
To flash Android Things onto your board, download the latest preview image in the [Android Things Console](https://partner.android.com/things/console) (see the [release notes](https://developer.android.google.cn/things/preview/releases.html)) and follow these steps:

为了烧录 Android Things 到板子上, 从 [Android Things Console](https://partner.android.com/things/console) 下载最新的映像(看下 [release notes](https://developer.android.google.cn/things/preview/releases.html)) 并按一下步骤来做:

### Step 1: Connect the Hardware

### Step 1: 连上硬件

Connect the board to your host computer as shown below:

连接板子到主机如下图：

![""](https://developer.android.google.cn/things/images/pico7-connections.png)

1.  Connect a USB-C cable from your host computer for Power and USB OTG.

    把板子上的USB OTG接口和主机之间用 USB-C 线连起来。

### Step 2: Flash Android Things

### 第二步： 烧录 Anroid Things 

Use the following steps to flash the Android image:

1.  Download and install [Android Studio](https://developer.android.google.cn/studio/index.html) or the [`sdkmanager`](https://developer.android.google.cn/studio/command-line/sdkmanager.html) command-line tool. Update the Android SDK Platform Tools to version 25.0.3 or later from the [SDK Manager](https://developer.android.google.cn/studio/intro/update.html#sdk-manager).

下载并安装 [Android Studio](https://developer.android.google.cn/studio/index.html) 或者安装 [`sdkmanager`](https://developer.android.google.cn/studio/command-line/sdkmanager.html) 命令行工具。从 [SDK Manager](https://developer.android.google.cn/studio/intro/update.html#sdk-manager)更新 Android SDK Platform Tools 到 25.0.3 版或者更新版本。

    *   Navigate to the Android SDK location on your computer; the path can be found in the system settings for Android Studio. Verify that the `fastboot` binary is installed in the `platform-tools/` directory.

    *   找到你电脑上的 Android SDK 的位置; 路径可以在Android Studio的设置里面找到。确认 `fastboot` 在 `platform-tools/` 目录里。

    *   After you have the fastboot tool, add it to your `PATH` [environment variable](https://developer.android.google.cn/studio/command-line/variables.html#set). This command should be similar to the following:
    
    *   如果已经装了fastboot, 加到 `PATH` [环境变量](https://developer.android.google.cn/studio/command-line/variables.html#set)里面。命令如同如下:

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

    <aside class="note">**Note:** <span>当处理程序结束会自动启动到 Android Things 。</span></aside>

5.  To verify that Android is running on the device, discover it using the [adb tool](https://developer.android.google.cn/tools/help/adb.html):

    为了验证 Android 正在板子上跑，可以用 [adb tool](https://developer.android.google.cn/tools/help/adb.html)执行如下命令:

        $ adb wait-for-device...$ adb devicesList of devices attached1b2f21d4e1fe0129        device

## Connecting Wi-Fi

## 连接 Wi-Fi

* * *

After flashing your board, it is strongly recommended to connect it to the internet. This allows your device to deliver crash reports and receive updates.

在板子烧过后, 强烈建议要连上网。 这会让你的板子能上传崩溃报告并接受更新。

<aside class="note">**Note:** <span>The device doesn't need to be on the same network as your computer.</span></aside>

**注意**板子不需要和你的主机在一个网络上。</aside>

Before connecting your board to a Wi-Fi network, attach an external IPEX or u.FL Wi-Fi antenna to your board as shown:

在连到Wi-Fi之前, 连一根 IPEX 或者 u.FL Wi-Fi 天线到板子上如下所示

![""](https://developer.android.google.cn/things/images/pico7-antenna.png)

<aside class="note">**Note:** <span>The module can't resolve Wi-Fi signals if you proceed without connecting an antenna.</span></aside>

<aside class="note">**Note:** <span>如果不连接天线模块无法处理 Wi-Fi信号。</span></aside>

To connect your board to Wi-Fi, first access a shell prompt on the device. You can use either of the following methods:

为了连板子到 Wi-Fi, 先连上板子的 shell 终端。 可以使用下面任一种方法：

*   Open a shell over adb with the `adb shell` command.

*   用 adb 命令 `adb shell` 打开一个 shell 终端。

*   Connect to the [serial console](#serial_debug_console).

*   连 [串口](#serial_debug_console)。

Once you can access a shell prompt, follow these steps:

一旦连到一个 shell 终端, 按下面步骤来:
Once you can access a shell prompt, follow these steps:

1.  Send an intent to the Wi-Fi service that includes the SSID of your local network. Your [board](https://developer.android.google.cn/things/hardware/developer-kits.html) must support the network protocol and frequency band of the wireless network in order to establish a connection.

向 Wi-Fi 服务发送带有你的本地网络 SSID 的请求。你的 [开发板](https://developer.android.google.cn/things/hardware/developer-kits.html) 必须支持无线网络协定和无线网络频率以建立连接。

        $ am startservice \    -n com.google.wifisetup/.WifiSetupService \    -a WifiSetupService.Connect

    The following arguments are supported with this command:
	
	此命令支持以下参数：
	
    <table>

    <tbody>

    <tr>

    <th style="width: 240px;">Argument
	
	参数</th>

    <th>Description
	
	具体细节</th>

    </tr>

    <tr>

    <td>`-e ssid <var>network_ssid</var>`</td>

    <td>Connect to the wireless network SSID specified by <var>network_ssid</var>. _This argument is required_.
	
	连接到由 <var>network_ssid</var> 指定的无线网络 SSID 。此参数为必须参数</td>

    </tr>

    <tr>

    <td>`-e passphrase <var>network_pass</var>`</td>

    <td>Optional argument to use the passcode specified by <var>network_pass</var> to connect to the network SSID. This argument is not necessary if your network doesn't require a passcode.
	
	可选操作，通过 <var>network_pass</var> 指定的密码来连接网络 SSID 。不必要操作如果你的网络不需要密码。</td>

    </tr>

    <tr>

    <td>`-e passphrase64 <var>encoded_pass</var>`</td>

    <td>Optional argument used in place of `passphrase` for passcodes with special characters (`space, !, ", $, &, ', (, ), ;, <, >, `, or |`). Use [base64 encoding](https://www.base64encode.org/) to specify the value for <var>encoded_pass</var>.
	
	可选操作，设置密码 `passphrase` 可用特殊字符 (`space, !, ", $, &, ', (, ), ;, <, >, `, or |`)。使用 [base64 encoding](https://www.base64encode.org/) 来指定 <var>encoded_pass</var> 的值</td>

    </tr>

    <tr>

    <td>`--ez hidden true`</td>

    <td>Optional argument to indicate that the SSID specified in this command is hidden. If omitted, this value defaults to false.
	
	可选操作，用来表明此命令中的 SSID 不可见。如果省略，此值会被默认为 false</td>

    </tr>

    </tbody>

    </table>

2.  Verify that the connection was successful through `logcat`:

    用 `logcat`命令 确认连接成功：

        $ logcat -d | grep Wifi...V WifiWatcher: Network state changed to CONNECTEDV WifiWatcher: SSID changed: ...I WifiConfigurator: Successfully connected to ...

3.  Test that you can access a remote IP address:

    测试能否访问远程 IP 地址：

        $ ping 8.8.8.8 PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.64 bytes from 8.8.8.8: icmp_seq=1 ttl=57 time=6.67 ms64 bytes from 8.8.8.8: icmp_seq=2 ttl=57 time=55.5 ms64 bytes from 8.8.8.8: icmp_seq=3 ttl=57 time=23.0 ms64 bytes from 8.8.8.8: icmp_seq=4 ttl=57 time=245 ms

4.  Check that the date and time are set correctly on the device:

    确认板子上的日期与时间设置正确：

        $ date

    <aside class="note">**Note:** <span>An incorrect date or time may cause SSL errors. Restart the device to automatically set the correct date and time from a time server.</span>
						**注意** <span>不正确的日期或者时间可能造成 SSL 错误。重启设备从服务器自动获取正确的日期和时间</aside>

If you want to clear all of the saved networks on the board:

如果你要清空开发板上所有已存的网络：

    $ am startservice \    -n com.google.wifisetup/.WifiSetupService \    -a WifiSetupService.Reset

## Serial debug console

## 调试串口
* * *

The serial console is a helpful tool for debugging your board and reviewing system log information. The console is the default output location for kernel log messages (i.e. `dmesg`), and it also provides access to a full shell prompt that you can use to access commands such as [logcat](https://developer.android.google.cn/tools/help/logcat.html). This is helpful if you are unable to access ADB on your board through other means and have not yet enabled a network connection.

串口是很有用的调试板子看系统打印信息的工具。 串口是内核打印信息的缺省输出口 (例如 `dmesg`), 串口能提供一个完全的命令行终端来执行类似 [logcat](https://developer.android.google.cn/tools/help/logcat.html)的命令。 如果此时板子不能用 ADB 命令来访问同时也不能联网时会特别有用。

To access the serial console:

连接串口:

![""](https://developer.android.google.cn/things/images/pico7-console.png)

Open a connection to the USB serial device on your development computer using a terminal program, such as [PuTTY](http://www.putty.org/) (Windows), [Serial](https://www.decisivetactics.com/products/serial/) (Mac OS), or [Minicom](https://en.wikipedia.org/wiki/Minicom) (Linux). The serial port parameters for the console are as follows:

使用串口终端程序在你的PC上打开 USB 串口设备, 例如 [PuTTY](http://www.putty.org/) (Windows下面), [Serial](https://www.decisivetactics.com/products/serial/) (Mac 下), 或者 [Minicom](https://en.wikipedia.org/wiki/Minicom) (Linux下)。串口的参数设置如下:

*   **Baud Rate**: 115200
*   **Data Bits**: 8
*   **Parity**: None
*   **Stop Bits**: 1

