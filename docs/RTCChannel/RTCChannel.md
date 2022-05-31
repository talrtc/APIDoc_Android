# RTCChannel


**说明**

RtcChannel 类在指定频道中实现实时音视频功能。通过创建多个 RtcChannel 对象，用户可以同时加入多个频道。


## initWithToken()


public int initWithToken(String token)


**说明**

初始化token


**参数**

变量名 | 描述
:--- | :---
token | 从业务服务器下发走网关的token

**返回**

 0 成功 其它失败


## init()


public int init(String roomId)


**说明**

培优初始化方式, 在Engine初始化之后调用


**参数**

变量名 | 描述
:--- | :---
roomId | 房间号

**返回**

 0 代表成功，其他代表失败


## createRendererView()


public SurfaceView createRendererView()


**说明**

创建 RendererView。


 该方法创建视频 RendererView，返回 SurfaceView 的类型。View 的操作和布局由 app 管理， Agora SDK 在 app 提供的 View 上进行渲染。显示视频视图必须调用该方法，而不是直接调用 SurfaceView。<br>
如果你需要使用 SurfaceView，请调用本方法；如果你需要使用 TextureView，请调用 CreateTextureView 方法。

**返回**

 SurfaceView


## setupRemoteVideo()


public void setupRemoteVideo(View view, long uid)


**说明**

设置远端视频iew


**参数**

变量名 | 描述
:--- | :---
view | 视图
uid | 用户ID

## setRemoteVolume()


public void setRemoteVolume(long uid, int volume)


**说明**

设置远端用户音量


**参数**

变量名 | 描述
:--- | :---
uid | 用户ID
volume | 音量值

## setRemoteRenderMode()


public void setRemoteRenderMode(long uid, [RTCEngine.RTCVideoRenderMode](../members/members.md#rtcvideorendermode) mode)


**说明**

设置远端渲染方式


**参数**

变量名 | 描述
:--- | :---
uid | 
mode | RTCVideoRenderModeHidden:填充 RTCVideoRenderModeFit:留黑边

## getTimestamp()


public long getTimestamp(int uid)


**说明**

获取SEI时间戳


**参数**

变量名 | 描述
:--- | :---
uid | 用户ID

**返回**

 0:无效 >0:有效时间戳


## joinChannel()


public void joinChannel()


**说明**

加入channel


 加入Other room<br>
加入这个房间必须使用观众身份.(无论是教师端还是学生端)

**回调**

```java
 IRTCChannelEventListener.localUserJoinedWithUid(String channelId, long uid)
```


## muteRemoteVideo()


public void muteRemoteVideo(long uid, boolean mute)


**说明**

取消或恢复订阅指定远端用户的视频流。


 该方法需要在加入频道后调用。

**参数**

变量名 | 描述
:--- | :---
uid | 用户ID
mute | 是否取消订阅指定远端用户的视频流。<br>true: 取消订阅。<br>false: （默认）订阅。

## muteRemoteAudio()


public void muteRemoteAudio(long uid, boolean mute)


**说明**

取消或恢复订阅指定远端用户的音频流。


 该方法需要在加入频道后调用。

**参数**

变量名 | 描述
:--- | :---
uid | 用户ID
mute | 是否取消订阅指定远端用户的音频流。<br>true：取消订阅。<br>false：（默认）订阅。

## muteAllRemoteVideo()


public void muteAllRemoteVideo(boolean mute)


**说明**

取消或恢复订阅所有远端用户的视频流。


 成功调用该方法后，本地用户会取消或恢复订阅所有远端用户的视频流，包括在调用该方法后加入频道的用户的视频流。

**参数**

变量名 | 描述
:--- | :---
mute | 是否取消订阅所有远端用户的视频流。<br>true: 取消订阅。<br>false:（默认）订阅。

>  该方法需要在加入频道后调用。


## muteAllRemoteAudio()


public void muteAllRemoteAudio(boolean mute)


**说明**

取消或恢复订阅所有远端用户的音频流。


 成功调用该方法后，本地用户会取消或恢复订阅所有远端用户的音频流，包括在调用该方法后加入频道的用户的音频流。

**参数**

变量名 | 描述
:--- | :---
mute | 是否取消订阅所有远端用户的音频流。<br>true: 取消订阅。<br>false:（默认）订阅。

## leaveChannel()


public void leaveChannel()


**说明**

离开channel


## destroy()


public void destroy()


**说明**

channel销毁


## setRemoteVideoStreamType()


public int setRemoteVideoStreamType(long uid, int streamType)


**说明**

设置订阅的视频流类型。大小流切换


 在网络条件受限的情况下，如果发送端没有调用 enableDualStreamMode(false) 关闭双流模式，接收端可以选择接收大流还是小流。其中，大流为高分辨率高码率的视频流， 小流则是低分辨率低码率的视频流。<br>
正常情况下，用户默认接收大流。如需节约带宽和计算资源，则可以调用该方法动态调整对应远端视频流的大小。 SDK 会根据该方法中的设置，切换大小流。<br>
视频小流默认的宽高比和视频大流的宽高比一致。根据当前大流的宽高比，系统会自动分配小流的分辨率、帧率及码率。

**参数**

变量名 | 描述
:--- | :---
uid | 用户 ID
streamType | 视频流类型：<br>(0): 视频大流，即高分辨率、高码率视频流。<br>(1): 视频小流，即低分辨率、低码率视频流。

**返回**

 0 代表成功，其他代表失败


## setEventListener()


public void setEventListener([IRTCChannelEventListener](../ChannelCallback/ChannelCallback.md#irtcchanneleventlistener) listener)


**说明**

设置channel的回调


**参数**

变量名 | 描述
:--- | :---
listener | 回调监听类

## setRole()


public int setRole([RTCEngine.RTCRole](../members/members.md#rtcrole) role)


**说明**

设置直播场景下的用户角色。


 调用 setRole(BROADCASTING) 后，SDK 会默认设置用户角色为观众，你可以调用 setRole 设置用户角色为主播。<br>
该方法在加入频道前后均可调用。

**参数**

变量名 | 描述
:--- | :---
role | RTCRoleBroadcaster:主播<br>RTCRoleAudience:观众

**返回**

 0 代表成功，其他代表失败


## muteLocalVideo()


public int muteLocalVideo(boolean mute)


**说明**

取消或恢复发布本地视频流。


 成功调用该方法后，远端会触发 didVideoMuted 回调。<br>
同一时间，本地的音视频流只能发布到一个频道。如果你创建了多个频道，请确保你只在一个频道中调用 muteLocalVideo(false)， 否则方法会调用失败并返回 -5 (ERR_REFUSED)。<br>
该方法不会改变视频采集设备的使用状态。<br>
该方法的调用是否生效受 joinRoom 和 setClientRole 方法的影响，

**参数**

变量名 | 描述
:--- | :---
mute | 是否mute

**回调**

```java
 IRTCChannelEventListener:: void didVideoMuted(long uid, boolean muted);
```


## muteLocalAudio()


public int muteLocalAudio(boolean muted)


**说明**

取消或恢复发布本地音频流。


 成功调用该方法后，远端会触发 onUserMuteAudio 回调。<br>
同一时间，本地的音视频流只能发布到一个频道。如果你创建了多个频道，请确保你只在一个频道中调用 muteLocalVideo(false)，否则方法会调用失败并返回 -5 (ERR_REFUSED)。

**参数**

变量名 | 描述
:--- | :---
muted | 是否取消发布本地音频流。<br>true：取消发布。<br>false：发布。

**回调**

```java
 IRTCChannelEventListener.didAudioMuted(long uid, boolean muted);
```


## startChannelMediaRelay()


public int startChannelMediaRelay([RTCEngine.RTCChannelMediaRelayConfiguration](../members/members.md#rtcchannelmediarelayconfiguration) channelMediaRelayConfiguration)


**说明**

开始跨房间转推流


**参数**

变量名 | 描述
:--- | :---
channelMediaRelayConfiguration | 转推配置

**返回**

 0 成功, 其它失败


## stopChannelMediaRelay()


public int stopChannelMediaRelay()


**说明**

停止跨房间转推流


**返回**

 0 成功, 其它失败


## updateChannelMediaRelay()


public int updateChannelMediaRelay([RTCEngine.RTCChannelMediaRelayConfiguration](../members/members.md#rtcchannelmediarelayconfiguration) channelMediaRelayConfiguration)


**说明**

更新转推流信息


**参数**

变量名 | 描述
:--- | :---
channelMediaRelayConfiguration | 转推配置

**返回**

 0 成功, 其它失败


## addPublishStreamUrl()


public int addPublishStreamUrl(String url, boolean needTranscode)


**说明**

推流到CDN,增加旁路推流地址


 调用该方法后，你可以向 CDN 推送 RTMP 或 RTMPS 协议的媒体流。

**参数**

变量名 | 描述
:--- | :---
url | CDN 推流地址，格式为 RTMP 或 RTMPS。该字符长度不能超过 1024 字节。url 不支持中文等特殊字符。
needTranscode | 是否转码。<br>true：转码。转码是指在旁路推流时对音视频流进行转码处理后，再推送到其他 CDN 服务器。多适用于频道内有多个主播，需要进行混流、合图的场景。<br>false：不转码。

**返回**

 0 代表成功，其他代表失败


## removePublishStreamUrl()


public int removePublishStreamUrl(String url)


**说明**

移除CDN推流，删除旁路推流地址


**参数**

变量名 | 描述
:--- | :---
url | 推流地址

**返回**

 0 代表成功，其他代表失败


## setRtmpConfig()


public int setRtmpConfig([RTCEngine.RTCRtmpConfig](../members/members.md#rtcrtmpconfig) config)


**说明**

设置rtmp配置，该方法用于旁路推流的视图布局及音频设置等。


 请确保已开通旁路推流的功能。<br>
该方法仅适用于直播场景下的主播用户。

**参数**

变量名 | 描述
:--- | :---
config | 推流配置

**返回**

 0 代表成功，其他代表失败


## sendStreamMessage()


public int sendStreamMessage(long timestamp, byte data)


**说明**

发送数据流。


 方法发送数据流消息到频道内所有用户。SDK 对该方法的实现进行了如下限制：频道内每秒最多能发送 30 个包，且每个包最大为 1 KB。 每个客户端每秒最多能发送 6 KB 数据。频道内每人最多能同时有 5 个数据通道。<br>
请确保在调用该方法前，已调用 createDataStream 创建了数据通道。<br>
该方法仅适用于通信场景以及直播场景下的主播用户。

**参数**

变量名 | 描述
:--- | :---
timestamp | 时间戳
data | 待发送的数据

**返回**

 0 代表成功，其他代表失败


## applyRemoteStreamSubscribeAdvice()


public int applyRemoteStreamSubscribeAdvice(long uid, int streamType)


**说明**

设置远端拉流的方式


**参数**

变量名 | 描述
:--- | :---
uid | 远端UID
streamType | 流类型 0: 大流  1: 小流   2: 音频

**返回**

 0(ERR_OK): 方法调用成功。<br>
< 0: 方法调用失败。


## takeRemoteViewSnapshot()


public int takeRemoteViewSnapshot(long uid)


**说明**

获取拉流视频截图。


 该方法用于对指定用户的视频流进行截图，生成一张 JPG 格式的图片，并保存至指定的路径。<br>
该方法是异步操作，调用返回时 SDK 并没有真正获取截图。<br>
该方法需要在加入频道后调用。<br>
如果用户的视频经过前处理，例如，添加了水印或美颜，生成的截图会包含前处理效果。

**参数**

变量名 | 描述
:--- | :---
uid | 用户id

**返回**

 0 代表成功，其他代表失败


## setupRemoteVideo()


public int setupRemoteVideo(long uid, TextureView view)


**说明**

初始化远端用户视图。


 该方法绑定远端用户和显示视图，并设置远端用户视图在本地显示时的渲染模式和镜像模式，只影响本地用户看到的视频画面。<br>
请在主线程调用该方法。<br>
如果你希望在通话中更新远端用户的渲染或镜像模式，请使用 setRemoteRenderMode 方法。

**参数**

变量名 | 描述
:--- | :---
uid | 用户id
view | 远端view

**返回**

 0 代表成功，其他代表失败


## setDefaultMuteAllRemoteAudioStreams()


public int setDefaultMuteAllRemoteAudioStreams(boolean muted)


**说明**

设置是否默认接收音频流。 - 后续通过 mute false打开


 默认取消或恢复订阅远端用户的音频流。<br>
该方法需要在加入频道后调用。调用成功后，本地用户取消或恢复订阅调用时刻之后加入频道的远端用户。

**参数**

变量名 | 描述
:--- | :---
muted | 是否默认取消订阅远端用户的音频流：<br>true：默认取消订阅。<br>false：（默认）默认订阅。

**返回**

 0 代表成功，其他代表失败


## setDefaultMuteAllRemoteVideoStreams()


public int setDefaultMuteAllRemoteVideoStreams(boolean muted)


**说明**

设置是否默认接收视频流。 - 后续通过 mute false打开


 默认取消或恢复订阅远端用户的视频流。<br>
该方法需要在加入频道后调用。调用成功后，本地用户取消或恢复订阅调用时刻之后加入频道的远端用户。

**参数**

变量名 | 描述
:--- | :---
muted | 是否默认取消订阅远端用户的视频流：<br>true：默认取消订阅。<br>false：（默认）默认订阅。

**返回**

 0 代表成功，其他代表失败


