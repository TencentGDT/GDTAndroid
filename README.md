# 腾讯联盟 Android SDK 接入文档

##  概述

### 说明

本文档旨在帮助 Android 应用开发者在程序中快速植入腾讯广告联盟平台提供的广告。作为应用开发者，您只需要进行简单配置，就可以在您的应用中显示定制的广告。关于 SDK 的具体使用方法，请仔细阅读下面的文档。  

## 背景 

### 开发环境

- **操作系统**：支持 Linux/Mac/Windows 系统，具体依赖开发者选择的 IDE  
- **开发工具**：支持 Android studio、Eclipse、Intellij  
- **部署目标**：接入联盟流量的应用   
- **支持设备**：运行了 Android 4.0 以及以上系统的 Android 设备
- **接入方式**：[下载 aar](https://adnet.qq.com/resource/sdk) 或 gradle。如使用 gradle，请参考下方：
```gradle 
implementation 'com.qq.e.union:union:版本号' // 普通版本 
implementation 'com.qq.e.union:tbs:版本号' // X5 内核版本 
```

### 术语介绍

- APPID：媒体 ID，是您在[腾讯联盟开发者平台](http://e.qq.com/dev/index.html)创建媒体时获得的 ID，这个 ID 是我们在广告网络中识别您应用的唯一 ID。  
- POSID：广告位 ID，是您在[腾讯联盟开发者平台](http://e.qq.com/dev/index.html)为您的媒体所创建的某种类型（Banner、开屏、插屏、原生）的广告位置的 ID。

### 权限申请

部分广告样式的接入需要权限，您可以联系腾讯广告联盟商务进行了解和权限申请。在[腾讯联盟开发者平台](http://e.qq.com/dev/)新建广告位时**您只能看到您有相应权限的广告位类型**。

## 广告位创建流程

在您的媒体通过审核后，可以在[腾讯联盟开发者平台](http://e.qq.com/dev/index.html)选择“新建广告位”。

步骤说明：

- 1.在新建广告位之前，确保您已经下载最新版SDK并阅读完说明文档，了解如何在您的媒体中使用广告位 ID
- 2.选择需要嵌入广告的媒体名称。**注意此处只可选择已通过审核的媒体**
- 3.设置广告位的名称及格式。广告位名称用于区分媒体内设置的各个广告位，方便您在后台进行统一管理和查看数据报表；目前提供选择的广告位格式有 Banner 广告、原生广告、插屏广告和开屏广告
- 4.点击完成按钮以后即获得对应该广告位的 ID 号
- 5.成功得到广告位ID以后，您可以在应用代码内使用该ID进行广告联调测试（见“接入代码”部分）
- 6.通过测试后去掉测试代码部分（TestAd），即可发布带有联盟广告位的 Android 应用 

##  支持广告类型
优量汇支持以下几种广告类型，您可以根据开发需要选择合适的广告：

|    广告类型  | 简介  | 适用场景 | 版本备注 |
| ---------- | --- |--- |--- |
| [Banner广告](http://developers.adnet.qq.com/doc/android/union/union_banner2_0) |  位于app顶部、中部、底部任意一处，横向贯穿整个app页面 |常出现在文章页末尾，详情页面底部，信息流顶部等 |推荐接入banner2.0接口  |
| [插屏广告](http://developers.adnet.qq.com/doc/android/union/union_interstitial2_0)   |  插屏广告是移动广告的一种常见形式，在应用开流程中弹出，当应用展示插页式广告时，用户可以选择点按广告，访问其目标网址，也可以将其关闭，返回应用 | 在应用执行流程的自然停顿点，适合投放这类广告  | 推荐接入插屏2.0接口 |
|[开屏广告](http://developers.adnet.qq.com/doc/android/union/union_splash)|开屏广告以App启动作为曝光时机，提供5s的可感知广告展示|app启动时，常会使用开屏广告||
|[原生模板](http://developers.adnet.qq.com/doc/android/union/union_native_express)|相比于前文介绍的Banner广告、插屏广告等，原生广告提供了更加灵活、多样化的广告样式选择|如果我们提供的模板广告样式符合您的需求，建议直接使用该接口||
|[自渲染](http://developers.adnet.qq.com/doc/android/union/union_native2_0)|开发者可以自由拼合广告素材，包括广告标题、文字描述和图片|原生广告（模板方式）不能满足开发需求，可以使用自渲染|推荐接入自渲染2.0接口|
|[激励视频](http://developers.adnet.qq.com/doc/android/union/union_reward_video)|将短视频融入到app场景当中，成为app“任务”之一。用户观看短视频广告后可以得到一些应用内奖励|常出现在游戏的复活、登录等位置，或者网服类app的一些增值服务场景||
|[H5-激励视频](http://developers.adnet.qq.com/doc/android/union/union_h5_reward)|在<b>H5页面</b>中加入<b>激励视频广告位</b>发起广告请求，而H5可以借助外层SDK的功能进行视频播放|如果您需要在H5页面中“嵌入”激励视频广告，该接口可以非常快速便捷地完成这一开发需求。比如开发者可以在<b>H5小游戏</b>中，嵌入激励视频广告，用户完成收看后会获得游戏奖励||

## [更新日志](https://developers.adnet.qq.com/doc/android/union/union_version)