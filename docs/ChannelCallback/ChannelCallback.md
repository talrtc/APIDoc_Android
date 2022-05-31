# IRTCChannelEventListener


**说明**

监听和报告指定频道的事件和数据。


## localUserJoinedWithUid()


public void localUserJoinedWithUid(String channelId, long uid)


**说明**

加入频道回调。


**参数**

变量名 | 描述
:--- | :---
channelId | 频道号
uid | 用户ID

## remotefirstVideoRecvWithUid()


public void remotefirstVideoRecvWithUid(String channelId, long uid)


**说明**

已完成远端视频首帧解码回调。


 本地收到远端第一个视频帧并解码成功后，会触发该回调。有两种情况：<br>
远端用户首次上线后发送视频<br>
远端用户视频离线再上线后发送视频

**参数**

变量名 | 描述
:--- | :---
uid | 用户 ID，指定是哪个用户的视频流
channelId | 频道ID

## remotefirstAudioRecvWithUid()


public void remotefirstAudioRecvWithUid(String channelId, long uid)


**说明**

已接收远端音频首帧回调


**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
uid | 用户ID

## remoteUserJoinWithUid()


public void remoteUserJoinWithUid(String channelId, long uid)


**说明**

远端用户（通信场景）/主播（直播场景）加入当前频道回调。


 通信场景下，该回调提示有远端用户加入了频道，并返回新加入用户的 ID； 如果加入之前，已经有其他用户在频道中了，新加入的用户也会收到这些已有用户加入频道的回调。<br>
直播场景下，该回调提示有主播加入了频道，并返回该主播的用户 ID。 如果在加入之前，已经有主播在频道中了，新加入的用户也会收到已有主播加入频道的回调。

**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
uid | 用户ID

## didOfflineOfUid()


public void didOfflineOfUid(String channelId, long uid)


**说明**

远端用户（通信场景）/主播（直播场景）离开当前频道回调。


 提示有远端用户/主播离开了频道（或掉线）。用户离开频道有两个原因，即正常离开和超时掉线：<br>
正常离开的时候，远端用户/主播会收到类似“再见”的消息，接收此消息后，判断用户离开频道<br>
超时掉线的依据是，在一定时间内（约 20 秒），用户没有收到对方的任何数据包，则判定为对方掉线。在网络较差的情况下，有可能会误报。

**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
uid | 用户ID

## didOccurError()


public void didOccurError(String channelId, [RTCEngine.RTCEngineErrorCode](../members/members.md#rtcengineerrorcode) code)


**说明**

错误回调


**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
code | 错误码

## connectionChangedToState()


public void connectionChangedToState(String channelId, [RTCConnectionStateType](../members/members.md#rtcconnectionstatetype) state, String reason)


**说明**

网络连接状态已改变回调


**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
state | 网络状态
reason | 原因描述

## onRemoteVideoStateChanged()


public void onRemoteVideoStateChanged(String channelId, long uid, int state)


**说明**

远端用户视频状态发生改变回调。


 1.Starting<br>
2.Decoding<br>
3.Frozen   远端视频正常<br>
4.Failed   远端视频卡住

**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
uid | 用户ID
state | 状态

## reportRtcStats()


public void reportRtcStats(String channelId, [RTCEngine.ReportRtcStats](../members/members.md#reportrtcstats) stats)


**说明**

当前通话统计回调


**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
stats | 通话状态

## onNetworkQuality()


public void onNetworkQuality(String channelId, long uid, int txQuality, int rxQuality)


**说明**

通话中每个用户的网络上下行 last mile 质量报告回调


**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
uid | 用户ID
txQuality | 该用户的上行网络质量
rxQuality | 该用户的下行网络质量

## didAudioMuted()


public void didAudioMuted(String channelId, long uid, boolean muted)


**说明**

收到远端音频mute消息


**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
uid | 用户ID
muted | 状态

## didVideoMuted()


public void didVideoMuted(String channelId, long uid, boolean muted)


**说明**

收到远端视频mute消息


**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
uid | 用户ID
muted | 状态

## onVideoBufferingStateChanged()


public void onVideoBufferingStateChanged(String channelId, long uid, int state, long timestampInMs)


**说明**

流状缓冲态回调


**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
uid | 用户ID
state | 0: 开始缓冲  1: 缓冲结束
timestampInMs | 时间戳

## onLeaveChannel()


public void onLeaveChannel(String channelId)


**说明**

用户离开房间成功


**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID

## onStreamMessage()


public void onStreamMessage(long uid, byte data)


**说明**

IRC透传消息


**参数**

变量名 | 描述
:--- | :---
uid | 频道id
data | 数据

## onStreamMessage()


public void onStreamMessage(String channelId, long uid, byte data)


**说明**

IRC透传消息


**参数**

变量名 | 描述
:--- | :---
channelId | 频道id
uid | 用户ID
data | 数据

## onChannelMediaRelayStateChanged()


public void onChannelMediaRelayStateChanged(String channelId, int state, int code)


**说明**

跨频道媒体流转发事件回调


**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
state | 状态
code | 状态码

## onChannelMediaRelayEvent()


public void onChannelMediaRelayEvent(String channelId, int code)


**说明**

跨房间推流事件回调


**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
code | 状态码

## onRemoteStreamSubscribeAdvice()


public void onRemoteStreamSubscribeAdvice(String channelId, long uid, int currentStreamType, int suitableStreamType)


**说明**

建议设置的流类型


<br>
流类型 0: 大流<br>
1: 小流<br>
2: 音频

**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
uid | 用户Id
currentStreamType | 当前流类型
suitableStreamType | 建议流类型

## onTakeRemoteViewSnapshot()


public void onTakeRemoteViewSnapshot(String channelId, long uid, Bitmap bitmap)


**说明**

远端截图


**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
bitmap | 图像bitmap
uid | 用户ID

## onPublishVideoStateChanged()


public void onPublishVideoStateChanged(String channelId, int oldState, int newState)


**说明**

发布视频状态变化回调


 空闲(0)<br>
未发布(1)<br>
发布中(2)<br>
已发布(3)

**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
oldState | 旧状态
newState | 新状态

## onPublishAudioStateChanged()


public void onPublishAudioStateChanged(String channelId, int oldState, int newState)


**说明**

发布音频状态变化回调


 空闲(0)<br>
未发布(1)<br>
发布中(2)<br>
已发布(3)

**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
oldState | 旧状态
newState | 新状态

## onSubscribeVideoStateChanged()


public void onSubscribeVideoStateChanged(String channelId, int uid, int oldState, int newState)


**说明**

订阅视频状态通知回调


 空闲(0)<br>
未订阅(1)<br>
订阅中(2)<br>
已订阅(3)

**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
uid | 远端用户UID
oldState | 旧状态
newState | 新状态

## onSubscribeAudioStateChanged()


public void onSubscribeAudioStateChanged(String channelId, int uid, int oldState, int newState)


**说明**

订阅音频状态通知回调


 空闲(0)<br>
未订阅(1)<br>
订阅中(2)<br>
已订阅(3)

**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
uid | 远端用户UID
oldState | 旧状态
newState | 新状态

## onRemoteVideoStats()


public void onRemoteVideoStats(String channelId, [RTCEngine.RemoteVideoStats](../members/members.md#remotevideostats) stats)


**说明**

远端视频状态回调


**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
stats | 状态回调

## onRemoteAudioStats()


public void onRemoteAudioStats(String channelId, [RTCEngine.RemoteAudioStats](../members/members.md#remoteaudiostats) stats)


**说明**

远端音频状态回调


**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
stats | 状态回调

## onVideoSizeChanged()


public void onVideoSizeChanged(String channelId, long uid, int width, int height, int rotation)


**说明**

远端视频尺寸变化通知


**参数**

变量名 | 描述
:--- | :---
channelId | 频道ID
uid | 用户ID
width | 宽度
height | 高度
rotation | 旋转角度

