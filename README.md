## Telegram messenger for Android

[Telegram](https://telegram.org) is a messaging app with a focus on speed and security. It’s superfast, simple and free.
This repo contains the official source code for [Telegram App for Android](https://play.google.com/store/apps/details?id=org.telegram.messenger).

## Creating your Telegram Application

We welcome all developers to use our API and source code to create applications on our platform.
There are several things we require from **all developers** for the moment.

1. [**Obtain your own api_id**](https://core.telegram.org/api/obtaining_api_id) for your application.
2. Please **do not** use the name Telegram for your app — or make sure your users understand that it is unofficial.
3. Kindly **do not** use our standard logo (white paper plane in a blue circle) as your app's logo.
3. Please study our [**security guidelines**](https://core.telegram.org/mtproto/security_guidelines) and take good care of your users' data and privacy.
4. Please remember to publish **your** code too in order to comply with the licences.

### API, Protocol documentation

Telegram API manuals: https://core.telegram.org/api

MTproto protocol manuals: https://core.telegram.org/mtproto

### Compilation Guide

**Note**: In order to support [reproducible builds](https://core.telegram.org/reproducible-builds), this repo contains dummy release.keystore,  google-services.json and filled variables inside BuildVars.java. Before publishing your own APKs please make sure to replace all these files with your own.

You will require Android Studio 3.4, Android NDK rev. 20 and Android SDK 8.1

1. Download the Telegram source code from https://github.com/DrKLO/Telegram ( git clone https://github.com/DrKLO/Telegram.git )
2. Copy your release.keystore into TMessagesProj/config
3. Fill out RELEASE_KEY_PASSWORD, RELEASE_KEY_ALIAS, RELEASE_STORE_PASSWORD in gradle.properties to access your  release.keystore
4.  Go to https://console.firebase.google.com/, create two android apps with application IDs org.telegram.messenger and org.telegram.messenger.beta, turn on firebase messaging and download google-services.json, which should be copied to the same folder as TMessagesProj.
5. Open the project in the Studio (note that it should be opened, NOT imported).
6. Fill out values in TMessagesProj/src/main/java/org/telegram/messenger/BuildVars.java – there’s a link for each of the variables showing where and which data to obtain.
7. You are ready to compile Telegram.

### Localization

We moved all translations to https://translations.telegram.org/en/android/. Please use it.

### 要在Android Studio中创建和运行Telegram项目，可以按照以下详细步骤进行操作。我们将从获取Telegram源码到在Android Studio中设置和运行项目逐步进行。

步骤 1: 准备开发环境
安装Android Studio:

确保已经安装了最新版本的Android Studio。如果没有，请从Android Studio官方网站下载并安装。
安装Git:

您需要使用Git来克隆Telegram的源码。请确保安装了Git，可以从Git官方网站下载并安装。
安装Java Development Kit (JDK):

Telegram的源码通常使用JDK 8进行编译，请确保安装了JDK 8，并且JAVA_HOME环境变量指向JDK 8的安装路径。
步骤 2: 获取Telegram源码
克隆源码:
打开命令行终端，运行以下命令来克隆Telegram的源码仓库：

#####
git clone https://github.com/DrKLO/Telegram.git
进入克隆后的项目目录：
#####
cd Telegram
####
步骤 3: 导入Telegram项目到Android Studio
启动Android Studio:

打开Android Studio，选择Open an existing project。
导入项目:

导航到您克隆的Telegram项目目录，然后点击OK来导入项目。
等待Gradle同步:

Android Studio将会自动检测项目并尝试同步Gradle。这个过程可能需要下载所需的依赖库。

如果遇到任何错误，比如缺少某些SDK或插件，请按照提示进行修复。通常Android Studio会提示安装缺少的组件或升级Gradle插件。

步骤 4: 配置和检查项目设置
检查Gradle配置:

打开build.gradle文件，确保项目的Gradle配置正确。特别是检查是否使用了正确的Android SDK版本和依赖项。
配置签名密钥（可选）:

如果您计划在物理设备上运行并测试应用程序，可能需要配置签名密钥。在app/build.gradle中配置signingConfigs，或者使用默认的调试签名。
检查API密钥和配置:

一些功能可能需要配置API密钥或其他资源文件。您可能需要手动添加这些配置。
步骤 5: 构建和运行项目
选择目标设备:

在Android Studio的工具栏中选择一个模拟器或连接一个物理设备来进行测试。
构建项目:

点击Build > Make Project来确保项目可以正确编译。如果一切正常，Android Studio将会构建应用程序。
运行项目:

点击Run > Run 'app'，或直接点击工具栏上的运行按钮来在选定的设备上运行应用程序。
步骤 6: 调试和测试
使用调试工具:

Android Studio提供了强大的调试工具，您可以使用这些工具来设置断点、查看日志输出以及逐步调试代码。
查看日志输出:

使用Logcat来查看应用运行时的日志输出，这可以帮助您识别和修复潜在的问题。

###  导入项目报错Unsupported Gradle JVM.

Your build is currently configured to use Java 17.0.11 and Gradle 7.0.2.

Possible solutions:
 - Upgrade to Gradle 8.5 and re-sync
 - Upgrade to Gradle 7.2 and re-sync
为了解决这个问题，您可以按照以下两种方法之一来升级Gradle版本，以支持Java 17。

解决方案1：升级Gradle到8.5
升级到Gradle 8.5可以直接解决这个兼容性问题。

步骤：
打开gradle-wrapper.properties文件:

您可以在项目的gradle/wrapper/gradle-wrapper.properties文件中找到Gradle版本配置。
更新Gradle版本:

将distributionUrl更新为最新的Gradle 8.5版本，如下所示：
properties
复制代码
distributionUrl=https\://services.gradle.org/distributions/gradle-8.5-bin.zip
重新同步项目:

在Android Studio中点击File > Sync Project with Gradle Files，或重新打开项目，Android Studio将自动下载并配置新版本的Gradle。
解决方案2：升级到Gradle 7.2
如果您不想直接升级到Gradle 8.5，也可以升级到Gradle 7.2，它也支持Java 17。

步骤：
同样打开gradle-wrapper.properties文件:

导航到项目的gradle/wrapper/gradle-wrapper.properties文件。
更新Gradle版本到7.2:

将distributionUrl更新为：
properties
复制代码
distributionUrl=https\://services.gradle.org/distributions/gradle-7.2-bin.zip
重新同步项目:

同样在Android Studio中点击File > Sync Project with Gradle Files，让Android Studio重新下载并配置Gradle 7.2。
解决方案3：降级Java版本
如果您无法升级Gradle版本，也可以考虑将Java版本降级到16或以下。您需要安装较低版本的JDK，并将JAVA_HOME环境变量指向该版本。

步骤：
安装Java 16或更低版本:

从Oracle或OpenJDK网站下载并安装Java 16。
配置JAVA_HOME:

将JAVA_HOME环境变量指向Java 16的安装路径，并重新启动Android Studio。
同步项目:

再次同步项目，以确保使用的是Java 16。
