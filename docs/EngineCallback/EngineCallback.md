# IRTCMediaVideoProcess


**说明**

视频回调监听接口


## didCapturedVideoData()


void didCapturedVideoData([RTCVideoData](../members/members.md#rtcvideodata) data)


**说明**

采集数据回调（本地）


**参数**

变量名 | 描述
:--- | :---
data | 视频数据

## didRenderVideoData()


void didRenderVideoData(long uid, [RTCVideoData](../members/members.md#rtcvideodata) data)


**说明**

渲染数据回调（远端）


**参数**

变量名 | 描述
:--- | :---
uid | 用户ID
data | 视频数据

# IRTCMediaAudioProcess


**说明**

音频回调


## didCapturedAuidoData()


void didCapturedAuidoData([RTCAudioData](../members/members.md#rtcaudiodata) data)


**说明**

采集音频数据回调（本地）


**参数**

变量名 | 描述
:--- | :---
data | 音频数据

## didRenderAudioData()


void didRenderAudioData(long uid, [RTCAudioData](../members/members.md#rtcaudiodata) data)


**说明**

渲染音频数据（远端）


**参数**

变量名 | 描述
:--- | :---
uid | 用户ID
data | 音频数据

# IRTCAudioObserver


**说明**

混音后音频回调


## onPlaybackAudioData()


public void onPlaybackAudioData([RTCPlayBackAudioFrame](../members/members.md#rtcplaybackaudioframe) frame)


**说明**

音频回放数据


**参数**

变量名 | 描述
:--- | :---
frame | 音频数据

# RtcEngineEventObserver


**说明**




## onEngineCreateError()


public void onEngineCreateError(int engineType, String reason)


**说明**

创建引擎失败


**参数**

变量名 | 描述
:--- | :---
engineType | 引擎类型
reason | 失败原因

## onRtmpStreamingStateChanged()


public void onRtmpStreamingStateChanged(String url, int state, int errCode)


**说明**

RTMP/RTMPS 推流状态发生改变回调。


 RTMP/RTMPS 推流状态发生改变时，SDK 会触发该回调，并在回调中明确状态发生改变的 URL 地址及当前推流状态<br>
该回调方便推流用户了解当前的推流状态；推流出错时，你可以通过返回的错误码了解出错的原因，方便排查问题。

**参数**

变量名 | 描述
:--- | :---
url | 推流状态发生改变的 URL 地址
state | 当前的推流状态：<br>(0)：推流未开始或已结束。成功调用 removePublishStreamUrl 方法删除推流地址后，也会返回该状态<br>(1)：正在连接推流服务器和 CDN 服务器。SDK 调用 addPublishStreamUrl 方法后，会返回该状态<br>(2)：推流正在进行。SDK 成功推流后，会返回该状态<br>(3)：正在恢复推流。当 CDN 出现异常，或推流短暂中断时，SDK 会自动尝试恢复推流，并返回该状态。如成功恢复推流，则进入状态 RTMP_STREAM_PUBLISH_STATE_RUNNING(2)；如服务器出错或 60 秒内未成功恢复，则进入状态 RTMP_STREAM_PUBLISH_STATE_FAILURE(4)。如果觉得 60 秒太长，也可以主动调用 removePublishStreamUrl 和 addPublishStreamUrl 方法尝试重连<br>(4)：推流失败。你可以再次调用 addPublishStreamUrl 重新尝试推流<br>(5)：SDK 正在与  推流服务器和 CDN 服务器断开连接。当你调用 remove 或 stop 方法正常结束推流时，SDK 会依次报告推流状态为 DISCONNECTING，IDLE。
errCode | 详细的推流错误信息：

## onPlayMusicSateChanged()


public void onPlayMusicSateChanged(int state, int errCode)


**说明**

本地用户的音乐文件播放状态已改变回调。


 该回调在音乐文件播放状态发生改变时触发，并报告当前的播放状态和播放状态改变的原因。

**参数**

变量名 | 描述
:--- | :---
state | 当前音乐文件播放状态：<br>(710)：音乐文件正常播放。<br>(711)：音乐文件暂停播放。<br>(713)：音乐文件停止播放。<br>(714)：音乐文件播放失败。
errCode | 音乐文件播放状态改变的原因：<br>(701)：音乐文件打开出错。例如，本地音乐文件不存在、文件格式不支持或无法访问在线音乐文件 URL。<br>(702)：音乐文件打开太频繁。如需多次调用 startAudioMixing，请确保调用间隔大于 500 ms。<br>(703)：音乐文件播放中断。<br>(720)：成功调用 startAudioMixing 播放音乐文件。<br>(721)：音乐文件完成一次循环播放。<br>(722)：音乐文件开始新的一次循环播放。<br>(723)：音乐文件完成所有循环播放。<br>(724)：成功调用 stopAudioMixing 停止播放音乐文件。<br>(725)：成功调用 pauseAudioMixing 暂停播放音乐文件。<br>(726)：成功调用 resumeAudioMixing 恢复音乐文件播放。

## onAudioStats()


public void onAudioStats([RTCAudioStats](../members/members.md#rtcaudiostats) stats)


**说明**

通话中远端音频流的统计信息回调。


 该回调描述远端用户在通话中端到端的音频流统计信息，针对每个远端用户/主播每 2 秒触发一次。如果远端同时存在多个用户/主播，该回调每 2 秒会被触发多次。

**参数**

变量名 | 描述
:--- | :---
stats | 接收到的远端音频统计数据

## onNetworkQuality()


public void onNetworkQuality(long uid, int txQuality, int rxQuality)


**说明**

通话中每个用户的网络上下行 last mile 质量报告回调。


 该回调描述每个用户在通话中的 last mile 网络状态，其中 last mile 是指设备到  边缘服务器的网络状态。该回调每秒触发一次。如果远端有多个用户/主播，该回调每 2 秒会被触发多次。

**参数**

变量名 | 描述
:--- | :---
uid | 用户 ID。表示该回调报告的是持有该 ID 的用户的网络质量。
txQuality | 该用户的上行网络质量，基于上行视频的发送码率、上行丢包率、平均往返时延和网络抖动计算。该值代表当前的上行网络质量，帮助判断是否可以支持当前设置的视频编码属性。假设上行码率是 1000 Kbps，那么支持 640 × 480 的分辨率、30 fps 的帧率没有问题，但是支持 1280 x 720 的分辨率就会有困难<br>有困难<br>(0)：质量未知<br>(1)：质量极好<br>(2)：用户主观感觉和极好差不多，但码率可能略低于极好<br>(3)：用户主观感受有瑕疵但不影响沟通<br>(4)：勉强能沟通但不顺畅<br>(5)：网络质量非常差，基本不能沟通<br>(6)：网络连接断开，完全无法沟通<br>(8)：SDK 正在探测网络质量
rxQuality | 该用户的下行网络质量，基于下行网络的丢包率、平均往返延时和网络抖动计算<br>(0)：质量未知<br>(1)：质量极好<br>(2)：用户主观感觉和极好差不多，但码率可能略低于极好<br>(3)：用户主观感受有瑕疵但不影响沟通<br>(4)：勉强能沟通但不顺畅<br>(5)：网络质量非常差，基本不能沟通<br>(6)：网络连接断开，完全无法沟通<br>(8)：SDK 正在探测网络质量

>  用户不发流时，txQuality 为 UNKNOWN; 用户不收流时，rxQuality 为 UNKNOWN。


## onHttpMetadataStateStateChanged()


protected void onHttpMetadataStateStateChanged(String streamId, int category, int state, int errorCode)


**说明**

Http打点状态回调


**参数**

变量名 | 描述
:--- | :---
streamId | 打点使用的流id
category | 要打点的category<br>6. 开始上课<br>7. 下课
state | 状态<br>0: 成功<br>-1: 失败
errorCode | 错误码<br>0: 成功<br>-999 失败 -- 打点服务器返回失败

## onStreamPublished()


public void onStreamPublished(String url, int error)


**说明**

开启旁路推流的结果回调。


**参数**

变量名 | 描述
:--- | :---
url | 打点使用的流id
error | 当error为errorcode的值时需要删除并重新添加旁路推流 RTCRtmpErrorCode 返回值

## onStreamUnpublished()


public void onStreamUnpublished(String url)


**说明**

停止旁路推流的结果回调。


 该回调返回 removePublishStreamUrl 方法的调用结果。用于通知主播是否停止推流成功。

**参数**

变量名 | 描述
:--- | :---
url | 主播停止推流的地址

## onEngineChangeNotify()


public void onEngineChangeNotify()


**说明**

需要进行切换引擎的通知


## onVideoBufferingStateChanged()


public void onVideoBufferingStateChanged(long uid, int state, long timestampInMs)


**说明**

流状态回调


**参数**

变量名 | 描述
:--- | :---
uid | 用户ID
state | 0: 开始缓冲  1: 缓冲结束
timestampInMs | 时间戳

## onLeaveChannel()


public void onLeaveChannel()


**说明**

用户离开房间成功


 App 调用 leaveChannel 方法时，SDK 提示 App 离开频道成功。 在该回调方法中，App 可以得到此次通话的总通话时长、SDK 收发数据的流量等信息。

## onStreamMessage()


public void onStreamMessage(long uid, byte data)


**说明**

IRC透传消息


 接收到对方数据流消息的回调。<br>
该回调表示本地用户收到了远端用户调用 sendStreamMessage 方法发送的流消息。

**参数**

变量名 | 描述
:--- | :---
uid | 用户ID
data | 接收到的数据

## onLocalVideoStateChanged()


public void onLocalVideoStateChanged(int localVideoState, int error)


**说明**

本地视频状态改变回调


 本地视频的状态发生改变时，SDK 会触发该回调返回当前的本地视频状态。<br>
该接口在本地视频出现故障时，方便你了解当前视频的状态以及出现故障的原因，方便排查问题。

**参数**

变量名 | 描述
:--- | :---
localVideoState | 当前的本地视频状态
error | 本地视频出错原因

## onLocalAudioStateChanged()


public void onLocalAudioStateChanged(int state, int error)


**说明**

本地音频状态改变回调


 state    当前的本地音频状态：<br>
LOCAL_AUDIO_STREAM_STATE_STOPPED(0)：本地音频默认初始状态<br>
LOCAL_AUDIO_STREAM_STATE_CAPTURING(1)：本地音频录制设备启动成功<br>
LOCAL_AUDIO_STREAM_STATE_ENCODING(2)：本地音频首帧编码成功<br>
LOCAL_AUDIO_STREAM_STATE_FAILED(3)：本地音频启动失败<br>
error	本地音频出错原因：<br>
LOCAL_AUDIO_STREAM_ERROR_OK(0)：本地音频状态正常<br>
LOCAL_AUDIO_STREAM_ERROR_FAILURE(1)：本地音频出错原因不明确<br>
LOCAL_AUDIO_STREAM_ERROR_DEVICE_NO_PERMISSION(2)：没有权限启动本地音频录制设备<br>
LOCAL_AUDIO_STREAM_ERROR_DEVICE_BUSY(3)：本地音频录制设备已经在使用中<br>
LOCAL_AUDIO_STREAM_ERROR_CAPTURE_FAILURE(4)：本地音频录制失败，建议你检查录制设备是否正常工作<br>
LOCAL_AUDIO_STREAM_ERROR_ENCODE_FAILURE(5)：本地音频编码失败

**参数**

变量名 | 描述
:--- | :---
state | 当前的本地音频状态
error | 本地音频出错原因

## onChannelMediaRelayStateChanged()


public void onChannelMediaRelayStateChanged(int state, int code)


**说明**

跨频道媒体流转发事件回调


 state    跨频道媒体流转发状态：<br>
RELAY_STATE_IDLE(0)：SDK 正在初始化<br>
RELAY_STATE_CONNECTING(1)：SDK 尝试跨频道<br>
RELAY_STATE_RUNNING(2)：源频道主播成功加入目标频道<br>
RELAY_STATE_FAILURE(3)：发生异常，详见 code 中提示的错误信息<br>
code	跨频道媒体流转发出错的错误码：<br>
RELAY_OK(0)：一切正常<br>
RELAY_ERROR_SERVER_ERROR_RESPONSE(1)：服务器回应出错<br>
RELAY_ERROR_SERVER_NO_RESPONSE(2)：服务器无回应。你可以调用 leaveChannel 方法离开频道<br>
RELAY_ERROR_NO_RESOURCE_AVAILABLE(3)：SDK 无法获取服务，可能是因为服务器资源有限导致<br>
RELAY_ERROR_FAILED_JOIN_SRC(4)：服务器加入源频道失败<br>
RELAY_ERROR_FAILED_JOIN_DEST(5)：服务器加入目标频道失败<br>
RELAY_ERROR_FAILED_PACKET_RECEIVED_FROM_SRC(6)：服务器未收到源频道发送的数据<br>
RELAY_ERROR_FAILED_PACKET_SENT_TO_DEST(7)：源频道发送数据失败<br>
RELAY_ERROR_SERVER_CONNECTION_LOST(8)：SDK 因网络质量不佳与服务器断开。你可以调用 leaveChannel 方法离开当前频道<br>
RELAY_ERROR_INTERNAL_ERROR(9)：服务器内部出错<br>
RELAY_ERROR_SRC_TOKEN_EXPIRED(10)：源频道的 Token 已过期<br>
RELAY_ERROR_DEST_TOKEN_EXPIRED(11)：目标频道的 Token 已过期

**参数**

变量名 | 描述
:--- | :---
state | 跨频道媒体流转发状态
code | 跨频道媒体流转发出错的错误码

## onChannelMediaRelayEvent()


public void onChannelMediaRelayEvent(int code)


**说明**

跨房间推流事件回调


 跨频道媒体流转发事件码：<br>
RELAY_EVENT_NETWORK_DISCONNECTED(0)：网络中断导致用户与服务器连接断开<br>
RELAY_EVENT_NETWORK_CONNECTED(1)：用户与服务器建立连接<br>
RELAY_EVENT_PACKET_JOINED_SRC_CHANNEL(2)：用户已加入源频道<br>
RELAY_EVENT_PACKET_JOINED_DEST_CHANNEL(3)：用户已加入目标频道<br>
RELAY_EVENT_PACKET_SENT_TO_DEST_CHANNEL(4)：SDK 开始向目标频道发送数据包<br>
RELAY_EVENT_PACKET_RECEIVED_VIDEO_FROM_SRC(5)：服务器收到了目标频道发送的视频流<br>
RELAY_EVENT_PACKET_RECEIVED_AUDIO_FROM_SRC(6)：服务器收到了目标频道发送的音频流<br>
RELAY_EVENT_PACKET_UPDATE_DEST_CHANNEL(7)：目标频道已更新<br>
RELAY_EVENT_PACKET_UPDATE_DEST_CHANNEL_REFUSED(8)：内部原因导致目标频道更新失败<br>
RELAY_EVENT_PACKET_UPDATE_DEST_CHANNEL_NOT_CHANGE(9)：目标频道未发生改变，即目标频道更新失败<br>
RELAY_EVENT_PACKET_UPDATE_DEST_CHANNEL_IS_NULL(10)：目标频道名为 NULL<br>
RELAY_EVENT_VIDEO_PROFILE_UPDATE(11)：视频属性已发送至服务器

**参数**

变量名 | 描述
:--- | :---
code | 跨频道媒体流转发事件码

## didOfflineOfUid()


public void didOfflineOfUid(long uid, int reason)


**说明**

远端用户离开房间 (优网海外使用-其它业务线暂时不要用)


**参数**

变量名 | 描述
:--- | :---
reason | 离开原因
uid | 用户id<br>0: 用户主动离开<br>1: 因过长时间收不到对方数据包，超时掉线。<br>2: 用户身份从主播切换为观众（直播模式下）

## onRemoteStreamSubscribeAdvice()


public void onRemoteStreamSubscribeAdvice(long uid, int currentStreamType, int suitableStreamType)


**说明**

建议设置的流类型


 流类型 0: 大流<br>
1: 小流<br>
2: 音频

**参数**

变量名 | 描述
:--- | :---
uid | 用户Id
currentStreamType | 当前流类型
suitableStreamType | 建议流类型

## onCaptureVideoSize()


public void onCaptureVideoSize(int width, int height)


**说明**

采集视频宽高变化


**参数**

变量名 | 描述
:--- | :---
width | 视频宽度
height | 视频高度

## onTakeRemoteViewSnapshot()


public void onTakeRemoteViewSnapshot(long uid, Bitmap bitmap)


**说明**

远端截图


 成功调用 后，SDK 触发该回调报告截图是否成功和获取截图的详情。

**参数**

变量名 | 描述
:--- | :---
bitmap | 图像bitmap
uid | 用户ID

## onTakeLocalViewSnapshot()


public void onTakeLocalViewSnapshot(Bitmap bitmap)


**说明**

本地截图


**参数**

变量名 | 描述
:--- | :---
bitmap | 

## onPublishVideoStateChanged()


public void onPublishVideoStateChanged(int oldState, int newState)


**说明**

发布视频状态变化回调


 空闲(0)<br>
未发布(1)<br>
发布中(2)<br>
已发布(3)

**参数**

变量名 | 描述
:--- | :---
oldState | 旧状态
newState | 新状态

## onPublishAudioStateChanged()


public void onPublishAudioStateChanged(int oldState, int newState)


**说明**

发布音频状态变化回调


 空闲(0)<br>
未发布(1)<br>
发布中(2)<br>
已发布(3)

**参数**

变量名 | 描述
:--- | :---
oldState | 旧状态
newState | 新状态

## onSubscribeVideoStateChanged()


public void onSubscribeVideoStateChanged(int uid, int oldState, int newState)


**说明**

订阅视频状态通知回调


 空闲(0)<br>
未订阅(1)<br>
订阅中(2)<br>
已订阅(3)

**参数**

变量名 | 描述
:--- | :---
uid | 远端用户UID
oldState | 旧状态
newState | 新状态

## onSubscribeAudioStateChanged()


public void onSubscribeAudioStateChanged(int uid, int oldState, int newState)


**说明**

订阅音频状态通知回调


 空闲(0)<br>
未订阅(1)<br>
订阅中(2)<br>
已订阅(3)

**参数**

变量名 | 描述
:--- | :---
uid | 远端用户UID
oldState | 旧状态
newState | 新状态

## onLocalVideoStats()


public void onLocalVideoStats([RTCEngine.LocalVideoStats](../members/members.md#localvideostats) stats)


**说明**

本地视频状态回调


 通话中本地视频流的统计信息回调。<br>
该回调描述本地设备发送视频流的统计信息，每秒触发一次。

**参数**

变量名 | 描述
:--- | :---
stats | 本地视频统计数据

## onLocalAudioStats()


public void onLocalAudioStats([RTCEngine.LocalAudioStats](../members/members.md#localaudiostats) stats)


**说明**

本地音频状态回调


 该回调描述本地设备发送音频流的统计信息。SDK 每秒触发该回调一次。

**参数**

变量名 | 描述
:--- | :---
stats | 本地音频统计数据

## onRemoteVideoStats()


public void onRemoteVideoStats([RTCEngine.RemoteVideoStats](../members/members.md#remotevideostats) stats)


**说明**

远端视频状态回调


 报告远端视频统计信息，该回调函数每秒触发一次。

**参数**

变量名 | 描述
:--- | :---
stats | 远端视频状态回调

## onRemoteAudioStats()


public void onRemoteAudioStats([RTCEngine.RemoteAudioStats](../members/members.md#remoteaudiostats) stats)


**说明**

远端音频状态回调


 报告更新本地视频统计信息，该回调函数每秒触发一次。

**参数**

变量名 | 描述
:--- | :---
stats | 远端音频状态

## reportAudioVolumeOfSpeaker()


public void reportAudioVolumeOfSpeaker(String channelId, long uid, int volume)


**说明**

音量上报


**参数**

变量名 | 描述
:--- | :---
channelId | channel id
uid | 用户ID
volume | 混音后的总音量，取值范围为 [0,255]。<br>在本地用户的回调中， 为本地发流用户的音量。<br>在远端用户的回调中， 为瞬时音量最高的远端用户（最多 3 位）混音后的总音量。 如果用户调用了 startAudioMixing，则 为音乐文件和用户声音的总音量。

# IRtcEngineEventListener


**说明**

监听和报告指定频道的事件和数据。


## localUserJoindWithUid()


void localUserJoindWithUid(long uid)


**说明**

加入频道回调。


 表示客户端已经登入服务器，且分配了频道 ID 和用户 ID

**参数**

变量名 | 描述
:--- | :---
uid | 用户 ID

## remotefirstVideoRecvWithUid()


void remotefirstVideoRecvWithUid(long uid)


**说明**

已完成远端视频首帧解码回调。


 本地收到远端第一个视频帧并解码成功后，会触发该回调。有两种情况：<br>
远端用户首次上线后发送视频<br>
远端用户视频离线再上线后发送视频

**参数**

变量名 | 描述
:--- | :---
uid | 用户 ID，指定是哪个用户的视频流

## remotefirstAudioRecvWithUid()


void remotefirstAudioRecvWithUid(long uid)


**说明**

已接收远端音频首帧回调。


**参数**

变量名 | 描述
:--- | :---
uid | 用户 ID，指定是哪个用户的音频流

## remoteUserJoinWitnUid()


void remoteUserJoinWitnUid(long uid)


**说明**

远端用户（通信场景）/主播（直播场景）加入当前频道回调。


 通信场景下，该回调提示有远端用户加入了频道，并返回新加入用户的 ID；如果加入之前，已经有其他用户在频道中了，新加入的用户也会收到这些已有用户加入频道的回调<br>
直播场景下，该回调提示有主播加入了频道，并返回该主播的用户 ID。如果在加入之前，已经有主播在频道中了，新加入的用户也会收到已有主播加入频道的回调。

**参数**

变量名 | 描述
:--- | :---
uid | 新加入频道的远端用户/主播 ID

## didOfflineOfUid()


void didOfflineOfUid(long uid)


**说明**

远端用户（通信场景）/主播（直播场景）离开当前频道回调。


 提示有远端用户/主播离开了频道（或掉线）。用户离开频道有两个原因，即正常离开和超时掉线：<br>
正常离开的时候，远端用户/主播会收到类似“再见”的消息，接收此消息后，判断用户离开频道<br>
超时掉线的依据是，在一定时间内（约 20 秒），用户没有收到对方的任何数据包，则判定为对方掉线。在网络较差的情况下，有可能会误报。

**参数**

变量名 | 描述
:--- | :---
uid | 用户ID

## didAudioMuted()


void didAudioMuted(long uid, boolean muted)


**说明**

远端用户停止/恢复发送音频流回调。


 提示有其他用户将他的音频流静音/取消静音。

**参数**

变量名 | 描述
:--- | :---
muted | 该用户是否静音：<br>true: 该用户已静音音频<br>false: 该用户已取消音频静音
uid | 用户 ID

## didVideoMuted()


void didVideoMuted(long uid, boolean muted)


**说明**

远端用户取消或恢复发布视频流回调。


**参数**

变量名 | 描述
:--- | :---
uid | 远端用户 UID。
muted | 远端用户是否取消发布视频流：<br>true：取消发布视频流。<br>false：发布视频流。

## didOccurError()


void didOccurError([RTCEngineErrorCode](../members/members.md#rtcengineerrorcode) code)


**说明**

发生错误回调。


 表示 SDK 运行时出现了（网络或媒体相关的）错误。通常情况下，SDK 上报的错误意味着 SDK 无法自动恢复，需要 App 干预或提示用户。

**参数**

变量名 | 描述
:--- | :---
code | 错误代码

## connectionChangedToState()


void connectionChangedToState([RTCConnectionStateType](../members/members.md#rtcconnectionstatetype) state, String reason)


**说明**

网络连接状态已改变回调。


**参数**

变量名 | 描述
:--- | :---
state | 当前的网络连接状态：
reason | 引起当前网络连接状态发生改变的原因：

## reportAudioVolumeOfSpeaker()


void reportAudioVolumeOfSpeaker(long uid, int volume)


**说明**

用户音量提示回调。


 启用该功能后，如果有用户将自己静音（调用了 muteLocalAudioStream），SDK 行为会受如下影响：<br>
本地用户静音后，SDK 立即停止报告本地用户的音量提示回调。<br>
瞬时音量最高的远端用户静音后 20 秒，远端的音量提示回调中将不再包含该用户；如果远端所有用户都将自己静音，20 秒后 SDK 停止报告远端用户的音量提示回调。

**参数**

变量名 | 描述
:--- | :---
uid | 用户ID
volume | 混音后的总音量，取值范围为 [0,255]。<br>在本地用户的回调中，totalVolume 为本地发流用户的音量。<br>在远端用户的回调中，totalVolume 为瞬时音量最高的远端用户（最多 3 位）混音后的总音量。 如果用户调用了 startAudioMixing，则 totalVolume 为音乐文件和用户声音的总音量。

## onRemoteVideoStateChanged()


void onRemoteVideoStateChanged(long uid, int state)


**说明**

远端用户视频状态发生改变回调。


 1.Starting<br>
2.Decoding<br>
3.Frozen   远端视频正常<br>
4.Failed   远端视频卡住

**参数**

变量名 | 描述
:--- | :---
uid | 发生视频状态改变的远端用户 ID
state | 远端视频流状态:1.Starting<br>2.Decoding<br>3.Frozen   远端视频正常<br>4.Failed   远端视频卡住

## onOnceLastMileQuality()


void onOnceLastMileQuality([RTC_LASTMILE_QUALITY](../members/members.md#rtc-lastmile-quality) lastmileQuality)


**说明**

通话前网络上下行 last mile 质量报告回调。


 该回调描述本地用户在加入频道前的 last mile 网络探测的结果，其中 last mile 是指设备到边缘服务器的网络状态。在 enableLastmileTest 之后，该回调函数每 2 秒触发一次。如果远端有多个用户/主播，该回调每 2 秒会被触发多次。

**参数**

变量名 | 描述
:--- | :---
lastmileQuality | 网络上下行质量，基于上下行网络的丢包率和抖动计算，探测结果主要反映上行网络的状态

## reportRtcStats()


void reportRtcStats([ReportRtcStats](../members/members.md#reportrtcstats) stats)


**说明**

当前通话统计回调。 该回调在通话中每两秒触发一次。


**参数**

变量名 | 描述
:--- | :---
stats | 当前状态

