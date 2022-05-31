# EnterConfig


**说明**

不使用多引擎token网关初始化引擎配置


## roomId


**说明**

房间ID(可选, 但需要调用 joinChannelWithRealToken 进房间)


## uid


**说明**

用户uid (必须)


## engineType


**说明**

引擎类型(必须)


## appId


**说明**

应用的appid(必须)


## planId


**说明**

课程Id(可选)


## token


**说明**

鉴权token (不开启鉴权可传空)


# RTCRole


**说明**

角色枚举类


## RTCRoleBroadcaster


**说明**

主播身份


## RTCRoleAudience


**说明**

观众身份


# RTCUserBusinessType


**说明**

用户业务类型


## RTCUserBusinessTypeStudent


**说明**

学生


## RTCUserBusinessTypeTeacher


**说明**

老师


## RTCUserBusinessTypeTutor


**说明**

辅导


# RTCEngineErrorCode


**说明**

错误码


## RTCEngineErrorCodeInvalidToken


**说明**

token无效


## RTCEngineErrorCodeTokenExpired


**说明**

token过期


## RTCEngineErrorCodesAudioError


**说明**

声音错误


## RTCEngineErrorCodeStartCamera


**说明**

启动摄像头失败


## RTCEngineErrorCodeStartVideoRender


**说明**

渲染失败


## RTCEngineErrorCodeNoServerTime


**说明**

服务器时间失败


## RTCEngineErrorCodeSEIFail


**说明**

SEI错误


## RTC_ERR_PUBLISH_FAILED


**说明**

推流失败


## RTC_ERR_REPUBLISH_FAILED


**说明**

重新推流失败


## RTC_ERR_SUBSCRIBE_FAILED


**说明**

订阅失败


## RTC_ERR_RESUBSCRIBE_FAILED


**说明**

重新订阅失败


## RTC_ERR_AUDIOTRACKOVERFLOW


**说明**

audiotrack开辟失败


## RTC_ERR_ROLE_FAILED


**说明**

设置角色失败回调


# EngineType


**说明**

引擎类型


## Agora


**说明**

声网


## Tencent


**说明**

腾讯


## OMNI


**说明**

自研


# RTCFeature


**说明**

支持的功能


## FeatureAudioBeauty


**说明**

美声


# RTC_LASTMILE_QUALITY


**说明**

质量等级


## RTC_QUALITY_UNKNOWN


**说明**

未知


## RTC_QUALITY_EXCELLENT


**说明**

质量极好


## RTC_QUALITY_GOOD


**说明**

用户主观感觉和极好差不多，但码率可能略低于极好


## RTC_QUALITY_POOR


**说明**

用户主观感受有瑕疵但不影响沟通


## RTC_QUALITY_BAD


**说明**

勉强能沟通但不顺畅


## RTC_QUALITY_VBAD


**说明**

网络质量非常差，基本不能沟通


## RTC_QUALITY_DOWN


**说明**

完全无法沟通


## RTC_QUALITY_DETECTING


**说明**

SDK 正在探测网络质量


# RTC_ORIENTATION_MODE


**说明**

视频编码的方向模式


## RTC_ORIENTATION_MODE_ADAPTIVE


**说明**

（默认）该模式下 SDK 输出的视频方向与采集到的视频方向一致。接收端会根据收到的视频旋转信息对视频进行旋转。该模式适用于接收端可以调整视频方向的场景


## RTC_ORIENTATION_MODE_FIXED_LANDSCAPE


**说明**

该模式下 SDK 固定输出风景（横屏）模式的视频。如果采集到的视频是竖屏模式，则视频编码器会对其进行裁剪。该模式适用于当接收端无法调整视频方向时，如使用 CDN 推流场景下


## RTC_ORIENTATION_MODE_FIXED_PORTRAIT


**说明**

该模式下 SDK 固定输出人像（竖屏）模式的视频，如果采集到的视频是横屏模式，则视频编码器会对其进行裁剪。该模式适用于当接收端无法调整视频方向时，如使用 CDN 推流场景下


# RTCEngineLogLevel


**说明**

日志等级


## RTCENGINE_LOG_FILTER_DEBUG


**说明**

debug


## RTCENGINE_LOG_FILTER_INFO


**说明**

普通


## RTCENGINE_LOG_FILTER_WARNING


**说明**

警告


## RTCENGINE_LOG_FILTER_ERROR


**说明**

错误


## RTCENGINE_LOG_FILTER_CRITICAL


**说明**

紧急


## RTCENGINE_LOG_FILTER_OFF


**说明**

关闭


# RTCEngineVideoBitrate


**说明**

视频码率 单位(kbps)


## VIDEO_BITRATE_100


**说明**

码率100


## VIDEO_BITRATE_200


**说明**

码率200


## VIDEO_BITRATE_350


**说明**

码率350


## VIDEO_BITRATE_400


**说明**

码率400


## VIDEO_BITRATE_600


**说明**

码率600


## VIDEO_BITRATE_1000


**说明**

码率1000


# RTCVideoRenderMode


**说明**

渲染模式


## RTCVideoRenderModeHidden


**说明**

隐藏,裁剪


## RTCVideoRenderModeFit


**说明**

适应,留黑边


# RTCAudioMode


**说明**

声音模式


## Mode_Default


**说明**

恢复音频路由为默认


## Mode_Call


**说明**

通话模式


## Mode_Music


**说明**

音乐模式


# RawAudioFrameOpMode


**说明**

裸数据使用模式


## MODE_READ_ONLY


**说明**

只读


## MODE_WRITE_ONLY


**说明**

只写


## MODE_READ_WRITE


**说明**

读写


# RTCVideoFrameRate


**说明**

视频帧率


## FRAME_RATE_FPS_1


**说明**

1fps


## FRAME_RATE_FPS_7


**说明**

7fps


## FRAME_RATE_FPS_10


**说明**

10fps


## FRAME_RATE_FPS_15


**说明**

15fps


## FRAME_RATE_FPS_24


**说明**

24fps


## FRAME_RATE_FPS_30


**说明**

30fps


# RTCAppState


**说明**

app当前状态


## APP_STATE_FOREGROUND


**说明**

前台


## APP_STATE_BACKGROUND


**说明**

后台


# RTCPushRtmpState


**说明**

Rtmp推流状态


## IDlE


**说明**

未开始或停止推流


## CONNECTING


**说明**

正在连接


## RUNNING


**说明**

推流正在进行


## RECOVERING


**说明**

正在恢复推流。




 当 CDN 出现异常，或推流短暂中断时，SDK 会自动尝试恢复推流，并返回该状态。如成功恢复推流，则进入状态

## FAIL


**说明**

失败


# RTCPlayMusicState


**说明**

Music播放状态


## PLAY


**说明**

播放音乐文件


## PAUSED


**说明**

音乐文件暂停播放


## STOPPED


**说明**

音乐文件停止播放


## ERROR


**说明**

音乐文件播放失败


# RTCRtmpErrorCode


**说明**

RTMP错误码


## RTCRtmpErrorCodeTimeOut


**说明**

删除并重新添加


## RTCRtmpErrorCodeCDNError


**说明**

删除并重新添加（建议更换cdn地址）


## RTCRtmpErrorCodeServerError


**说明**

删除并重新添加


# RTCCreateEngineErrorReason


**说明**

引擎创建失败原因


## RTCCreateEngineErrorUnSupport


**说明**

不支持的引擎类型


# RTCStreamFallbackOption


**说明**

流模式操作


## RTCStreamTypeDisable


**说明**

下行网络较弱时，不对音视频流作回退处理，但不能保证音视频流的质量


## RTCStreamTypeLow


**说明**

（默认）下行网络较弱时只接收视频小流。


## RTCStreamTypeAudio


**说明**

下行网络较弱时，先尝试只接收视频小流；如果网络环境无法显示视频，则再回退到只接收远端订阅的音频流


# RTCStreamApplyStreamType


**说明**

流类型


## RTCStreamApplyStreamTypeHigh


**说明**

设置为大流


## RTCStreamApplyStreamTypeLow


**说明**

设置为小流


## RTCStreamApplyStreamTypeAudio


**说明**

设置为只拉声音


# RTCCameraPosition


**说明**

相机位置


## RTCCameraPositionFront


**说明**

前置


## RTCCameraPositionBack


**说明**

后置


# RTCConnectionChangedReason


**说明**

连接状态改变原因


# RTCChannelMediaInfo


**说明**

跨房间拉流 媒体配置类


# RTCChannelMediaRelayConfiguration


**说明**

跨房间拉流 配置


## setSrcChannelInfo()


public void setSrcChannelInfo([RTCChannelMediaInfo](../members/members.md#rtcchannelmediainfo) srcInfo)


**说明**

设置源频道信息


**参数**

变量名 | 描述
:--- | :---
srcInfo | 原房间配置

## setDestChannelInfo()


public void setDestChannelInfo([RTCChannelMediaInfo](../members/members.md#rtcchannelmediainfo) destInfo)


**说明**

设置目标频道信息


 如果你想将流转发到多个目标频道，可以多次调用该方法，设置多个频道的 ChannelMediaInfo。该方法支持最多设置 4 个目标频道。

**参数**

变量名 | 描述
:--- | :---
destInfo | 目的房间配置

# RTCRtmpConfig


**说明**

Rtmp 旁路推流配置


## audioChannel


**说明**

音频channel


## audioSampleRate


**说明**

采样率
32000, 44100, 48000


## width


**说明**

宽度


## height


**说明**

高度


## fps


**说明**

帧率


## gop


**说明**

gop大小


## videoBitrate


**说明**

码率
kbps


## backgroundImage


**说明**

底图


## backgroundColor


**说明**

底色


## users


**说明**

用户列表


# RTCRtmpBackGroundImage


**说明**

转推rtmp 背景图设置


## url


**说明**

直播视频上图片的 HTTP/HTTPS 地址，字符长度不得超过 1024 字节。


## x


**说明**

x坐标


## y


**说明**

y坐标


## width


**说明**

宽度


## height


**说明**

高度


# RTCRtmpUser


**说明**

Rtmp 旁路推流 User


## uid


**说明**

用户ID


## x


**说明**

开始坐标x


## y


**说明**

开始坐标y


## zorder


**说明**

层级


## width


**说明**




## height


**说明**




# RTCAudioStats


**说明**

音频状态


## uid


**说明**

用户ID


## networkTransportDelay


**说明**

端到端延迟


## jitterBufferDelay


**说明**

缓冲区大小


## audioLossRate


**说明**

音频丢包率


# ReportRtcStats


**说明**

发送状态统计


## txAudioBytes


**说明**

发送音频字节数，累计值


## txVideoBytes


**说明**

发送视频字节数，累计值


## rxAudioBytes


**说明**

接受音频字节数，累计值


## rxVideoBytes


**说明**

接受视频字节数，累计值


## txAudioKBitRate


**说明**

音频包的发送码率（kbps）,瞬时值


## rxAudioKBitRate


**说明**

音频接受码率（kbps）,瞬时值


## txVideoKBitRate


**说明**

视频发送码率（kbps）,瞬时值


## rxVideoKBitRate


**说明**

视频接受码率（kbps）,瞬时值


## gateWayRtt


**说明**

wifi下网关Rtt


## cpuTotalUsage


**说明**




## cpuAppUsage


**说明**




## txPacketsLostRate


**说明**

上行丢包率


## rxPacketsLostRate


**说明**

下行丢包率


## lastmileDelay


**说明**

最后一公里delay


# InspectMode


**说明**

鉴黄模型


## rate


**说明**






 1 代表 截一帧图就转发一帧给识别业务<br>
2 代表 每截两次图转发一帧给识别业务

## mode


**说明**

模式


# RTCVideoData


**说明**

裸数据回调的视频数据


## width


**说明**

宽度


## height


**说明**

高度


## yStride


**说明**

y跨距


## uStride


**说明**

u跨距


## vStride


**说明**

v跨距


## rotation


**说明**

偏移角度(0, 90, 180, 270)


## renderTimeMs


**说明**

时间戳


## data


**说明**

数据


# RTCAudioData


**说明**

裸数据回调的音频数据


## samples


**说明**

采样点个数


## bytesPerSample


**说明**

单采样点字节数


## channels


**说明**

通道数


## samplesPerSec


**说明**

每秒多少个采样点


## bufferLength


**说明**

数据长度


## renderTimeMs


**说明**

时间戳


## buffer


**说明**

数据


# RTCPlayBackAudioFrame


**说明**

混音后音频裸数据回调


## samples


**说明**

采样点个数


## bytesPerSample


**说明**

每采样点字节数


## channels


**说明**

通道数


## samplesPerSec


**说明**

每秒采样点个数


## bufferLength


**说明**

数据长度


## renderTimeMs


**说明**

时间戳


## buffer


**说明**

数据


# RemoteAudioStats


**说明**

远端音频状态


## uid


**说明**

用户ID


## quality


**说明**

质量


## audioLossRate


**说明**

音频丢包


## numChannels


**说明**

通道数


## receivedSampleRate


**说明**

接收采样率


## receivedBitrate


**说明**

接收码率


## audioFps


**说明**

每秒音频收包数


## avDiff


**说明**

音视频差


## rtt


**说明**

延迟


## RemoteAudioStats()


public RemoteAudioStats()


# LocalAudioStats


**说明**

本地音频状态


## numChannels


**说明**

通道数


## sentSampleRate


**说明**

发送采样率


## sentBitrate


**说明**

发送码率


## txPacketLossRate


**说明**

发送丢包


## audioFps


**说明**

音频帧率


## rtt


**说明**

延迟


## LocalAudioStats()


public LocalAudioStats()


# RemoteVideoStats


**说明**

远端视频数据


## uid


**说明**

用户ID


## delay


**说明**

延迟


## width


**说明**

宽度


## height


**说明**

高度


## receivedBitrate


**说明**

接受码率


## decoderOutputFrameRate


**说明**

解码帧率


## rendererOutputFrameRate


**说明**

渲染帧率


## packetLossRate


**说明**

丢包


## avDiff


**说明**

音视频差


## rtt


**说明**

延迟


# LocalVideoStats


**说明**

本地视频状态


## sentBitrate


**说明**

发送码率


## sentFrameRate


**说明**

发送帧率


## targetBitrate


**说明**

目标码率


## targetFrameRate


**说明**

目标帧率


## encodedBitrate


**说明**

编码码率


## encodedFrameWidth


**说明**

编码宽度


## encodedFrameHeight


**说明**

编码高度


## captureFrameRate


**说明**

采集帧率


## packetLossRate


**说明**

丢包


## rtt


**说明**

延迟


## LocalVideoStats()


public LocalVideoStats()


# RTCConnectionStateType


**说明**

连接状态改变类型


## RTCConnectionStateTypeDisconnected


**说明**

断开连接


## RTCConnectionStateTypeConnecting


**说明**

连接中


## RTCConnectionStateTypeConnected


**说明**

已连接


## RTCConnectionStateTypeReconnecting


**说明**

重连中


## RTCConnectionStateTypeFailed


**说明**

连接失败


