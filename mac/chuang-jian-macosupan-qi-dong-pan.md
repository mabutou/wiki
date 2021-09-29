# 创建 macOS U盘启动盘

## [如何创建可引导的 macOS 安装器](https://support.apple.com/zh-cn/HT201372) <a id="anchor-0"></a>

以下高级步骤主要适用于系统管理员以及熟悉命令行的其他人员。[升级 macOS](https://support.apple.com/zh-cn/HT201475) 或[重新安装 macOS](https://support.apple.com/zh-cn/HT204904) 不需要可引导安装器，但如果您要在多台电脑上安装 macOS，而又不想每次都下载安装器，这时可引导安装器就会很有用。

### 创建可引导安装器需要满足的条件 <a id="anchor-1"></a>

* USB 闪存驱动器或其他备用宗卷（格式化为 Mac OS 扩展格式），至少有 14 GB 可用储存空间
* 已下载 macOS Big Sur、Catalina、Mojave、High Sierra 或 El Capitan 的安装器

### 下载 macOS <a id="anchor-2"></a>

* **下载：**[**macOS Big Sur**](https://apps.apple.com/cn/app/macos-big-sur/id1526878132?mt=12)**、**[**macOS Catalina**](https://apps.apple.com/cn/app/macos-catalina/id1466841314?mt=12)**、**[**macOS Mojave**](https://apps.apple.com/cn/app/macos-mojave/id1398502828?mt=12) **或** [**macOS High Sierra**](https://apps.apple.com/cn/app/macos-high-sierra/id1246284741?mt=12) **** 这些内容会作为名为“安装 macOS \[版本名称\]”的 App 下载到您的“应用程序”文件夹。如果安装器在下载后打开，请退出而不要继续安装。要获取正确的安装器，请从运行 [macOS Sierra 10.12.5 或更高版本](https://support.apple.com/zh-cn/HT201260)或者 El Capitan 10.11.6 的 Mac 上进行下载。如果您是企业管理员，请通过 Apple 下载，而不要通过本地托管的软件更新服务器进行下载。 
* **下载：**[**OS X El Capitan** ](http://updates-http.cdn-apple.com/2019/cert/061-41424-20191024-218af9ec-cf50-4516-9011-228c78eda3d2/InstallMacOSX.dmg)这个内容会作为名为“InstallMacOSX.dmg”的磁盘映像下载。在与 El Capitan 兼容的 Mac 上，打开下载的磁盘映像，并运行其中名为“InstallMacOSX.pkg”的安装器。这时会在您的“应用程序”文件夹中安装一个名为“安装 OS X El Capitan”的 App。您将通过这个 App（而不是通过磁盘映像或 .pkg 安装器）创建可引导安装器。

### 在“终端”中使用“createinstallmedia”命令 <a id="anchor-3"></a>

1. 连接要用于保存可引导安装器的 USB 闪存驱动器或其他宗卷。 
2. 打开“应用程序”文件夹内“实用工具”文件夹中的“终端”。
3. 在“终端”中键入或粘贴以下命令之一。这些命令假设安装器位于您的“应用程序”文件夹中，并且“MyVolume”是您所使用的 USB 闪存驱动器或其他宗卷的名称。如果不是这个名称，请将这些命令中的 `MyVolume` 替换为您的宗卷名称。

**Big Sur\*：**

```text
sudo /Applications/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
```

**Catalina\*：**

```text
sudo /Applications/Install\ macOS\ Catalina.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
```

**Mojave\*：**

```text
sudo /Applications/Install\ macOS\ Mojave.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
```

**High Sierra\*：**

```text
sudo /Applications/Install\ macOS\ High\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
```

**El Capitan：**

```text
sudo /Applications/Install\ OS\ X\ El\ Capitan.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume --applicationpath /Applications/Install\ OS\ X\ El\ Capitan.app
```

\* 如果您的 Mac 运行的是 macOS Sierra 或更低版本，请使用 `--applicationpath` 参数和安装器路径，具体方法与在适用于 El Capitan 的命令中完成这个操作的方法类似。

  
键入命令后：

1. 按下 Return 键以输入这个命令。
2. 出现提示时，请键入您的管理员密码，然后再次按下 Return 键。在您键入密码时，“终端”不会显示任何字符。
3. 出现提示时，请键入 `Y` 以确认您要抹掉宗卷，然后按下 Return 键。在抹掉宗卷的过程中，“终端”会显示进度。
4. 宗卷被抹掉后，您可能会看到一条提醒，提示“终端”要访问可移除宗卷上的文件。点按“好”以允许继续拷贝。 
5. 当“终端”显示操作已完成时，相应宗卷将拥有与您下载的安装器相同的名称，例如“安装 macOS Big Sur”。您现在可以退出“终端”并弹出宗卷。 ![](https://support.apple.com/library/content/dam/edam/applecare/images/en_US/macos/Big-Sur/macos-big-sur-terminal-create-bootable-installer.jpg)

### 

### 使用可引导安装器 <a id="anchor-4"></a>

[确定您使用的是不是搭载 Apple 芯片的 Mac](https://support.apple.com/zh-cn/HT211814)，然后按照相应的步骤操作：

#### Apple 芯片 <a id="anchor-5"></a>

1. 将可引导安装器插入已连接到互联网且与您要安装的 macOS 版本兼容的 Mac。
2. 将 Mac 开机并继续按住电源按钮，直到看到启动选项窗口，其中会显示可引导宗卷。
3. 选择包含可引导安装器的宗卷，然后点按“继续”。
4. macOS 安装器打开后，请按照屏幕上的说明操作。

#### Intel 处理器 <a id="anchor-6"></a>

1. 将可引导安装器插入已连接到互联网且与您要安装的 macOS 版本兼容的 Mac。
2. 将 Mac 开机或重新启动后，立即按住 Option \(Alt\) ⌥ 键。
3. 当您看到显示可引导宗卷的黑屏时，松开 Option 键。
4. 选择包含可引导安装器的宗卷。然后点按向上箭头或按下 Return 键。  如果您无法从可引导安装器启动，请确保[“启动安全性实用工具”中的“外部启动”设置](https://support.apple.com/zh-cn/HT208198)已设为允许从外部介质启动。
5. 根据提示选取您的语言。
6. 从“实用工具”窗口中选择“安装 macOS”（或“安装 OS X”），然后点按“继续”，并按照屏幕上的说明进行操作。

### 

### 进一步了解 <a id="anchor-7"></a>

可引导安装器不会从互联网下载 macOS，但却需要互联网连接才能获取特定于 Mac 机型的固件和其他信息。

要了解 `createinstallmedia` 命令以及可与它搭配使用的参数，请确保 macOS 安装器位于您的“应用程序”文件夹中，然后在“终端”中输入相应的路径：

```text
/Applications/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia
```

```text
/Applications/Install\ macOS\ Catalina.app/Contents/Resources/createinstallmedia
```

```text
/Applications/Install\ macOS\ Mojave.app/Contents/Resources/createinstallmedia
```

```text
/Applications/Install\ macOS\ High\ Sierra.app/Contents/Resources/createinstallmedia
```

```text
/Applications/Install\ OS\ X\ El\ Capitan.app/Contents/Resources/createinstallmedia
```

* [Official website](http://circlereader.com/)
* [Download new version](http://circlereader.com/download)
* [Question feedback](https://support.qq.com/products/317910)
* [Donation support❤️](http://circlereader.com/donate)

Circle typesetting, copyright support.apple.com

