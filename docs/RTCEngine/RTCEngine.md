# RTCEngine


**说明**

RtcEngine 类包含应用程序调用的主要方法。


## RTCEngine()


public RTCEngine(Context context, [IRtcEngineEventListener](../EngineCallback/EngineCallback.md#irtcengineeventlistener) listener)


**说明**

引擎创建


**参数**

变量名 | 描述
:--- | :---
context | 上下文
listener | engine事件监听接口

## setAppState()


public void setAppState([RTCAppState](../members/members.md#rtcappstate) state)


**说明**

当前App或设置的Activity 处于前台还是后台


**参数**

变量名 | 描述
:--- | :---
state | 当前状态

## setRtcEngineEventListener()


public void setRtcEngineEventListener([IRtcEngineEventListener](../EngineCallback/EngineCallback.md#irtcengineeventlistener) listener)


**说明**

设置engine事件监听


**参数**

变量名 | 描述
:--- | :---
listener | engine事件监听接口

## setRtcEngineEventObserver()


public void setRtcEngineEventObserver([RtcEngineEventObserver](../EngineCallback/EngineCallback.md#rtcengineeventobserver) observer)


**说明**

设置补充回调


**参数**

变量名 | 描述
:--- | :---
observer | 设置补充回调

## setAudioObserver()


public void setAudioObserver([RTCEngine.IRTCAudioObserver](../EngineCallback/EngineCallback.md#irtcaudioobserver) observer)


**说明**

设置混音后音视频裸数据回调


**参数**

变量名 | 描述
:--- | :---
observer | 

## setMediaVideoProcessListener()


public void setMediaVideoProcessListener([IRTCMediaVideoProcess](../EngineCallback/EngineCallback.md#irtcmediavideoprocess) listener)


**说明**

设置视频采集/播放回调


**参数**

变量名 | 描述
:--- | :---
listener | 视频裸数据监听

## setMediaVideoProcessOptions()


public int setMediaVideoProcessOptions(boolean needJavaLocalVideoData, boolean needJavaRemoteVideoData)


**说明**

设置视频采集/播放回调的参数


**参数**

变量名 | 描述
:--- | :---
needJavaLocalVideoData | 是否需要本地Java层视频数据  默认 true
needJavaRemoteVideoData | 是否需要远端 java层视频数据 默认 true

## setMediaAudioProcessListener()


public void setMediaAudioProcessListener([IRTCMediaAudioProcess](../EngineCallback/EngineCallback.md#irtcmediaaudioprocess) listener)


**说明**

设置音频采集/播放回调


**参数**

变量名 | 描述
:--- | :---
listener | 音频裸数据回调

## initWithToken()


public int initWithToken(String token)


**说明**

初始化token接口


**参数**

变量名 | 描述
:--- | :---
token | 从业务服务器下发走网关的token

**返回**

 0 代表成功，其他代表失败


## init()


public int init([EnterConfig](../members/members.md#enterconfig) config)


**说明**

引擎初始化


**参数**

变量名 | 描述
:--- | :---
config | 初始化参数配置

**返回**

 0 代表成功，其他代表失败


## setRole()


public int setRole([RTCRole](../members/members.md#rtcrole) role)


**说明**

设置直播场景下的用户角色


 调用 setRole(BROADCASTING) 后，SDK 在Engine 会默认设置用户角色为主播, 在Channel为观众，你可以调用 setRole 设置用户角色为主播。

**参数**

变量名 | 描述
:--- | :---
role | RTCRoleBroadcaster:主播<br>RTCRoleAudience:观众

>  该方法在加入频道前后均可调用(需要引擎初始化)。


**返回**

 0 代表成功，其他代表失败


## setBusinessUserRole()


public int setBusinessUserRole([RTCUserBusinessType](../members/members.md#rtcuserbusinesstype) role)


**说明**

设置用户业务角色


**参数**

变量名 | 描述
:--- | :---
role | EUSERBUSINESSTYPE_STUDENT:学生  EUSERBUSINESSTYPE_TEACHER:老师 EUSERBUSINESSTYPE_TUTOR:辅导老师

**返回**

 0 代表成功，其他代表失败


## setRtcEngineLog()


public int setRtcEngineLog(String fileFullPath, [RTCEngineLogLevel](../members/members.md#rtcengineloglevel) level)


**说明**

设置日志输出等级。


 该方法设置 SDK 的日志输出等级。不同的等级可以单独或组合使用。<br>
日志级别顺序依次为 OFF、CRITICAL、ERROR、WARNING、INFO 和 DEBUG。选择一个级别，你就可以看到在该级别之前所有级别的日志信息。 例如，你选择 WARNING 级别，就可以看到在 CRITICAL、ERROR 和 WARNING 级别上的所有日志信息。

**参数**

变量名 | 描述
:--- | :---
fileFullPath | 日志路径
level | 日志等级

**返回**

 0 代表成功，其他代表失败


## setRecordingAudioParameters()


public int setRecordingAudioParameters(int sample, int channel)


**说明**

设置采集的音频格式。


 该方法设置 onRecordFrame 回调数据的格式。 该方法需要在加入频道前调用。

**参数**

变量名 | 描述
:--- | :---
sample | 中返回数据的采样率，可设置为 8000，16000，32000，44100 或 48000。
channel | 返回数据的通道数，可设置为：<br>1: 单声道。<br>2: 双声道。

**返回**

 0 代表成功，其他代表失败


## enableLastmileProbeTest()


public void enableLastmileProbeTest()


**说明**

启用网络探测


**回调**

```java
 void onOnceLastMileQuality(RTC_LASTMILE_QUALITY lastmileQuality);
```


## disableLastmileProbeTest()


public void disableLastmileProbeTest()


**说明**

关闭网络测试。


## joinRoom()


public int joinRoom()


**说明**

加入频道。


 该方法让用户加入通话频道，在同一个频道内的用户可以互相通话，多个用户加入同一个频道，可以群聊。使用不同 App ID 的 App 是不能互通的。如果已在通话中，用户必须调用 leaveChannel 退出当前通话，才能进入下一个频道。<br>
成功调用该方加入频道后，本地会触发 localUserJoindWithUid 回调；通信场景下的用户和直播场景下的主播加入频道后，远端会触发 localUserJoindWithUid 回调。<br>
在网络状况不理想的情况下，客户端可能会与 服务器失去连接；SDK 会自动尝试重连，重连成功后，本地会触发 localUserJoindWithUid 回调。<br>
用户成功加入（切换）频道后，默认订阅频道内所有其他用户的音频流和视频流，因此产生用量并影响计费。如果想取消订阅，可以通过调用相应的 mute 方法实现。

**返回**

 0：调用成功


**回调**

```java
 IRtcEngineEventListener:: void localUserJoindWithUid(long uid);
```


## leaveRoom()


public void leaveRoom()


**说明**

离开频道。


 离开频道，即挂断或退出通话。<br>
调用 joinRoom 后，必须调用 leaveRoom 结束通话，否则无法开始下一次通话。<br>
不管当前是否在通话中，都可以调用 leaveRoom，没有副作用。<br>
该方法会把会话相关的所有资源释放掉。该方法是异步操作，调用返回时并没有真正退出频道。<br>
成功调用该方法离开频道后，本地会触发 didOfflineOfUid 回调；通信场景下的用户和直播场景下的主播离开频道后，远端会触发 didOfflineOfUid 回调。

>  如果你调用了 leaveChannel 后立即调用 destroy 方法，SDK 将无法触发 onLeaveChannel 回调。<br>
如果你在旁路推流过程中调用了 leaveChannel 方法， SDK 将自动调用 removePublishStreamUrl 方法。


**回调**

```java
 IRtcEngineEventListener:: void didOfflineOfUid(long uid);
```


## destroy()


public void destroy()


**说明**

销毁 RtcEngine 实例。


 该方法释放 Agora SDK 使用的所有资源。有些 app 只在用户需要时才进行实时音视频通信，不需要时则将资源释放出来用于其他操作，该方法适用于此类情况。调用 destroy 方法后，你将无法再使用 SDK 的其它方法和回调。如需再次使用实时音视频通信功能，你必须重新调用 create 方法创建一个新的 RtcEngine 实例。

>  该方法为同步调用，需要等待 RtcEngine 实例资源释放后才能执行其他操作，所以我们建议在子线程中调用该方法，避免主线程阻塞。此外，我们不建议在 SDK 的回调中调用 destroy，否则由于 SDK 要等待回调返回才能回收相关的对象资源，会造成死锁。<br>
如需在销毁后再次创建 RtcEngine 实例，需要等待 destroy 方法执行结束后再创建实例。


## enableVideo()


public void enableVideo()


**说明**

启用视频模块。


 该方法用于打开视频模式。可以在加入频道前或者通话中调用，在加入频道前调用，则自动开启视频模式，在通话中调用则由音频模式切换为视频模式。调用 disableVideo 方法可关闭视频模式。

## enableLocalVideo()


public void enableLocalVideo(boolean enable)


**说明**

开启/关闭本地视频采集。


 该方法禁用或重新启用本地视频采集。不影响接收远端视频。<br>
调用 enableVideo 后，本地视频即默认开启。 你可以调用 enableLocalVideo(false) 关闭本地视频采集。关闭后如果想重新开启，则可调用 enableLocalVideo(true)。

**参数**

变量名 | 描述
:--- | :---
enable | 是否启用本地视频：<br>true: 开启本地视频采集和渲染（默认）<br>false: 关闭使用本地摄像头设备。关闭后，远端用户会接收不到本地用户的视频流；但本地用户依然可以接收远端用户的视频流。设置为 false 时，该方法不需要本地有摄像头。

>  该方法设置的是内部引擎为启用或禁用状态，在 leaveRoom 后仍然有效。


## enableLocalAudio()


public void enableLocalAudio(boolean enable)


**说明**

开启/关闭本地音频采集。


 当 app 加入频道时，它的语音功能默认是开启的。该方法可以关闭或重新开启本地语音，即停止或重新开始本地音频采集。<br>
该方法不影响接收远端音频流，enableLocalAudio(false) 适用于只听不发的用户场景。

**参数**

变量名 | 描述
:--- | :---
enable | 是否开启本地语音。<br>true:（默认）重新开启本地语音，即开启本地语音采集。<br>false: 关闭本地语音，即停止本地语音采集。

>  该方法在加入频道前后均可调用。在加入频道前调用只能设置设备状态，在加入频道后才会立即生效。


## muteLocalVideo()


public int muteLocalVideo(boolean muted)


**说明**

取消或恢复发布本地视频流。


 成功调用该方法后，远端会触发 didVideoMuted 回调。<br>
同一时间，本地的音视频流只能发布到一个频道。如果你创建了多个频道，请确保你只在一个频道中调用 muteLocalVideo(false)， 否则方法会调用失败并返回 -5 (ERR_REFUSED)。

**参数**

变量名 | 描述
:--- | :---
muted | 是否取消发布本地视频流。

>  该方法不会改变视频采集设备的使用状态。<br>
该方法的调用是否生效受 joinRoom 和 setClientRole 方法的影响，


**回调**

```java
 IRtcEngineEventListener:: void didVideoMuted(long uid, boolean muted);
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
 IRtcEngineEventListener:: void didAudioMuted(long uid, boolean muted);
```


## muteRemoteVideo()


public void muteRemoteVideo(long uid, boolean muted)


**说明**

取消或恢复订阅指定远端用户的视频流。


 该方法需要在加入频道后调用。

**参数**

变量名 | 描述
:--- | :---
uid | 用户ID
muted | 是否取消订阅指定远端用户的视频流。<br>true: 取消订阅。<br>false: （默认）订阅。

## muteRemoteAudio()


public void muteRemoteAudio(long uid, boolean muted)


**说明**

取消或恢复订阅指定远端用户的音频流。


 该方法需要在加入频道后调用。

**参数**

变量名 | 描述
:--- | :---
uid | 用户ID
muted | 是否取消订阅指定远端用户的音频流。<br>true：取消订阅。<br>false：（默认）订阅。

## muteAllRemoteVideo()


public void muteAllRemoteVideo(boolean muted)


**说明**

取消或恢复订阅所有远端用户的视频流。


 成功调用该方法后，本地用户会取消或恢复订阅所有远端用户的视频流，包括在调用该方法后加入频道的用户的视频流。

**参数**

变量名 | 描述
:--- | :---
muted | 是否取消订阅所有远端用户的视频流。<br>true: 取消订阅。<br>false:（默认）订阅。

>  该方法需要在加入频道后调用。


## muteAllRemoteAudio()


public void muteAllRemoteAudio(boolean muted)


**说明**

取消或恢复订阅所有远端用户的音频流。


 成功调用该方法后，本地用户会取消或恢复订阅所有远端用户的音频流，包括在调用该方法后加入频道的用户的音频流。

**参数**

变量名 | 描述
:--- | :---
muted | 是否取消订阅所有远端用户的音频流。<br>true: 取消订阅。<br>false:（默认）订阅。

## setupLocalVideo()


public int setupLocalVideo(View view)


**说明**

初始化本地视图。


 该方法初始化本地视图并设置本地用户视频显示信息，只影响本地用户看到的视频画面，不影响本地发布视频。 调用该方法绑定本地视频流的显示视窗（View），并设置本地用户视图的渲染模式和镜像模式。

**参数**

变量名 | 描述
:--- | :---
view | 本地视图

**返回**

 0 代表成功，其他代表失败


## setLocalRenderMode()


public void setLocalRenderMode([RTCVideoRenderMode](../members/members.md#rtcvideorendermode) mode)


**说明**

设置本地视频显示模式。


 该方法设置本地视频显示模式。App 可以多次调用此方法更改显示模式。

**参数**

变量名 | 描述
:--- | :---
mode | RTCVideoRenderModeHidden:填充<br>RTCVideoRenderModeFit:留黑边

## setupRemoteVideo()


public void setupRemoteVideo(View view, long uid)


**说明**

初始化远端用户视图。


 该方法绑定远端用户和显示视图，并设置远端用户视图在本地显示时的渲染模式和镜像模式，只影响本地用户看到的视频画面。

**参数**

变量名 | 描述
:--- | :---
view | 视图
uid | 用户ID

## setRemoteRenderMode()


public void setRemoteRenderMode(long uid, [RTCVideoRenderMode](../members/members.md#rtcvideorendermode) mode)


**说明**

设置远端渲染方式


**参数**

变量名 | 描述
:--- | :---
uid | 远端用户 ID
mode | RTCVideoRenderModeHidden:填充<br>RTCVideoRenderModeFit:留黑边

## setRemoteRenderMode()


public void setRemoteRenderMode(long uid, [RTCVideoRenderMode](../members/members.md#rtcvideorendermode) mode, int mirrorMode)


**说明**

设置远端视频显示模式。


**参数**

变量名 | 描述
:--- | :---
uid | 远端用户 ID
mode | 视频显示模式
mirrorMode | 镜像模式

## createRendererView()


public SurfaceView createRendererView()


**说明**

创建 RendererView。


 该方法创建视频 RendererView，返回 SurfaceView 的类型。View 的操作和布局由 app 管理， Agora SDK 在 app 提供的 View 上进行渲染。显示视频视图必须调用该方法，而不是直接调用 SurfaceView。<br>
如果你需要使用 SurfaceView，请调用本方法；如果你需要使用 TextureView，请调用 CreateTextureView 方法。

**返回**

 SurfaceView


## startPreview()


public void startPreview()


**说明**

开启视频预览。


 该方法用于在进入频道前启动本地视频预览。调用该 API 前，必须：<br>
调用 enableVideo 开启视频功能。<br>
调用 setupLocalVideo 设置预览窗口及属性。

## stopPreview()


public void stopPreview()


**说明**

停止本地视频预览。


 调用 startPreview 后，如果你想关闭本地视频预览，请调用 stopPreview。

>  请在加入频道前或离开频道后调用该方法。


## switchCamera()


public void switchCamera()


**说明**

切换前置/后置摄像头。


 该方法需要在相机启动（如通过调用 startPreview 或 joinroom 实现）后调用。

## setCameraPosition()


public int setCameraPosition(int position)


**说明**

设置摄像头方向


**参数**

变量名 | 描述
:--- | :---
position | RTCCameraPosition 0:前置  1: 后置

**返回**

 0 正确


## getCameraPosition()


public int getCameraPosition()


**说明**

获取摄像头方向


**返回**

 0:前置<br>
1: 后置<br>
<0: 错误


## setMirror()


public void setMirror(boolean isMirror)


**说明**

设置本地镜像


**参数**

变量名 | 描述
:--- | :---
isMirror | true/false

## setRemoteMirror()


public void setRemoteMirror(boolean isMirror)


**说明**

设置远端镜像


**参数**

变量名 | 描述
:--- | :---
isMirror | true/false

## setVideoEncoderConfiguration()


public void setVideoEncoderConfiguration(int width, int height, [RTCEngineVideoBitrate](../members/members.md#rtcenginevideobitrate) bitrate, [RTC_ORIENTATION_MODE](../members/members.md#rtc-orientation-mode) orientationMode)


**说明**

设置视频编码配置


 该方法设置视频编码属性。每个属性对应一套视频参数，如分辨率、帧率、码率、视频方向等。 所有设置的参数均为理想情况下的最大值。当视频引擎因网络环境等原因无法达到设置的分辨率、帧率或码率的最大值时，会取最接近最大值的那个值。<br>
如果用户加入频道后不需要重新设置视频编码属性，

**参数**

变量名 | 描述
:--- | :---
width | 视频宽度
height | 视频高度
bitrate | 视频码率
orientationMode | 视频编码的方向模式

## setVideoEncoderConfiguration()


public void setVideoEncoderConfiguration(int width, int height, int fps, int bitrate, [RTC_ORIENTATION_MODE](../members/members.md#rtc-orientation-mode) orientationMode)


**说明**

设置视频编码属性。


 该方法设置视频编码属性。每个属性对应一套视频参数，如分辨率、帧率、码率、视频方向等。 所有设置的参数均为理想情况下的最大值。当视频引擎因网络环境等原因无法达到设置的分辨率、帧率或码率的最大值时，会取最接近最大值的那个值。<br>
如果用户加入频道后不需要重新设置视频编码属性，

**参数**

变量名 | 描述
:--- | :---
width | 视频宽度
height | 视频高度
fps | 视频帧率
bitrate | 视频码率
orientationMode | 视频编码的方向模式

## setAudioEncoderConfiguration()


public int setAudioEncoderConfiguration(int bitrate, int processmode)


**说明**

设置音频编码配置


**参数**

变量名 | 描述
:--- | :---
bitrate | 音频码率
processmode | 模式

**返回**

 0 代表成功，其他代表失败


## muteVideo()


public void muteVideo(boolean muting)


**说明**

停止/恢复发送本地视频流,取消或恢复发布本地视频流。


 成功调用该方法后，远端会触发 didVideoMuted 回调。<br>
同一时间，本地的音视频流只能发布到一个频道。如果你创建了多个频道，请确保你只在一个频道中调用 muteLocalVideo(false)， 否则方法会调用失败并返回 -5 (ERR_REFUSED)。

**参数**

变量名 | 描述
:--- | :---
muting | 是否取消发布本地视频流。<br>true：取消发布。<br>false：发布。

>  该方法不会改变视频采集设备的使用状态。<br>
该方法的调用是否生效受 joinRoom 和 setClientRole 方法的影响


**回调**

```java
 IRtcEngineEventListener:: void didVideoMuted(long uid, boolean muted);
```


## muteAudio()


public void muteAudio(boolean muting)


**说明**

停止/恢复发送本地音频流,取消或恢复发布本地音频流。


 成功调用该方法后，远端会触发 didAudioMuted 回调。<br>
同一时间，本地的音视频流只能发布到一个频道。如果你创建了多个频道，请确保你只在一个频道中调用 muteLocalVideo(false)，否则方法会调用失败并返回 -5 (ERR_REFUSED)。

**参数**

变量名 | 描述
:--- | :---
muting | 是否取消发布本地音频流。<br>true：取消发布。<br>false：发布。

>  该方法不会改变音频采集设备的使用状态。<br>
该方法的调用是否生效受 joinroom 和 setClientRole 方法的影响


**回调**

```java
 IRtcEngineEventListener:: void didAudioMuted(long uid, boolean muted);
```


## enableExternalVideo()


public void enableExternalVideo(boolean enable)


**说明**

配置外部视频源。


 该方法需要在加入频道前调用。

**参数**

变量名 | 描述
:--- | :---
enable | 是否使用外部视频源：<br>true：使用外部视频源<br>false：不使用外部视频源（默认）

## sendCustomVideoData()


public boolean sendCustomVideoData(byte buffer, int format, int w, int h, int rotation)


**说明**

传入外部视频数据,推送外部视频帧。


 请确保在你调用本方法前已调用 enableExternalVideo，并将参数 pushMode 设为 true，不然调用本方法后会一直报错。 该方法需要在加入频道后调用。

**参数**

变量名 | 描述
:--- | :---
buffer | yuv裸数据
format | 数据格式
w | 宽度
h | 高度
rotation | 旋转角度

**返回**

 true/false


## enableExternalAudio()


public void enableExternalAudio(boolean enable, int sampleRate, int channels)


**说明**

是否启用外部音频采集，设置外部音频采集参数


 请在 joinRoom 和 startPreview 前调用该方法。

**参数**

变量名 | 描述
:--- | :---
enable | 是否开启外部音频采集。<br>true: 开启外部音频采集。<br>false: （默认）关闭外部音频采集。
sampleRate | 外部音频源的采样率（Hz），可设置为 8000，16000，32000，44100 或 48000。
channels | 外部音频源的通道数，可设置为：<br>1: 单声道。<br>2: 双声道。

## sendCustomPCMData()


public void sendCustomPCMData(byte pcmBuffer)


**说明**

推送外部音频帧。


 该方法需要在加入频道后调用。

**参数**

变量名 | 描述
:--- | :---
pcmBuffer | pcm裸数据

## setRemoteVolume()


public void setRemoteVolume(long uid, int volume)


**说明**

设置远端用户音量


**参数**

变量名 | 描述
:--- | :---
uid | 用户ID
volume | 音量值

## getSdkVersion()


public String getSdkVersion()


**说明**

获取SDK版本号


**返回**

 版本号


## setTimestamp()


public int setTimestamp(long timestamp)


**说明**

设置SEI


**参数**

变量名 | 描述
:--- | :---
timestamp | SEI时间戳

**返回**

 0 代表成功，其他代表失败


## sendStreamMessage()


public int sendStreamMessage(long timestamp, byte data)


**说明**

发送数据流。


 该方法发送数据流消息到频道内所有用户。SDK 对该方法的实现进行了如下限制：频道内每秒最多能发送 30 个包，且每个包最大为 1 KB。 每个客户端每秒最多能发送 6 KB 数据。频道内每人最多能同时有 5 个数据通道。<br>
请确保在调用该方法前，已调用 createDataStream 创建了数据通道。<br>
该方法仅适用于通信场景以及直播场景下的主播用户。

**参数**

变量名 | 描述
:--- | :---
timestamp | 时间戳
data | 待发送的数据

**返回**

 0 代表成功，其他代表失败


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


## addPublishStreamUrl()


public int addPublishStreamUrl(String url, boolean needTranscode)


**说明**

推流到CDN,增加旁路推流地址


 调用该方法后，你可以向 CDN 推送 RTMP 或 RTMPS 协议的媒体流。SDK 会在本地触发 onRtmpStreamingStateChanged 回调，报告增加旁路推流地址的状态。

**参数**

变量名 | 描述
:--- | :---
url | CDN 推流地址，格式为 RTMP 或 RTMPS。该字符长度不能超过 1024 字节。url 不支持中文等特殊字符。
needTranscode | 是否转码。<br>true：转码。转码是指在旁路推流时对音视频流进行转码处理后，再推送到其他 CDN 服务器。多适用于频道内有多个主播，需要进行混流、合图的场景。<br>false：不转码。

**返回**

 0 代表成功，其他代表失败


**回调**

```java
 RtcEngineEventObserver::  public void onRtmpStreamingStateChanged(String url, int state, int errCode)
```


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


**回调**

```java
 RtcEngineEventObserver::  public void onRtmpStreamingStateChanged(String url, int state, int errCode)
```


## setRtmpConfig()


public int setRtmpConfig([RTCRtmpConfig](../members/members.md#rtcrtmpconfig) config)


**说明**

设置rmpt配置，该方法用于旁路推流的视图布局及音频设置等。


 请确保已开通旁路推流的功能。<br>
该方法仅适用于直播场景下的主播用户。

**参数**

变量名 | 描述
:--- | :---
config | 推流配置

**返回**

 0 代表成功，其他代表失败


## startPlayMusic()


public int startPlayMusic(String filePath)


**说明**

播放本地音乐


**参数**

变量名 | 描述
:--- | :---
filePath | 文件地址

**返回**

 0 代表成功，其他代表失败


## startPlayMusic()


public int startPlayMusic(String filePath, boolean loopback, boolean replace, int cycle)


**说明**

开始播放音乐文件，该方法支持将本地或在线音乐文件和麦克风采集的音频进行混音或替换


 如需调用该方法，请确保使用 Android 4.2 或以上设备，且 API Level ≥ 16。<br>
如果播放的是在线音乐文件，Agora 建议不要使用重定向地址。重定向地址在某些机型上可能会出现无法打开的情况。<br>
如果在模拟器上使用该 API，暂时只支持存放在 /sdcard/ 中的 mp3 文件。<br>
该方法需要在加入频道后调用。如需多次调用，请确保调用间隔大于 500 ms。<br>
如果本地音乐文件不存在、文件格式不支持或无法访问在线音乐文件 URL，则 SDK 会报告 WARN_AUDIO_MIXING_OPEN_ERROR(701)。<br>
为避免阻塞，该方法由同步调用改为异步调用。

**参数**

变量名 | 描述
:--- | :---
filePath | 文件路径，需精确到文件名及后缀。 支持在线文件的 URL 地址，本地文件的 URI 地址、绝对路径或以 /assets/ 开头的路径。 Note 通过绝对路径访问本地文件可能会遇到权限问题， 推荐使用 URI 地址访问本地文件。
loopback | true：只有本地可以听到混音或替换后的音频流  false：本地和对方都可以听到混音或替换后的音频流
replace | true：只推动设置的本地音频文件或者线上音频文件，不传输麦克风收录的音频 false：音频文件内容将会和麦克风采集的音频流进行混音
cycle | 音频文件循环播放的次数：<br>≥ 0: 播放次数。例如，0 表示不播放；1 表示播放 1 次。<br>-1：无限循环。

**返回**

 0 代表成功，其他代表失败


## stopPlayMusic()


public int stopPlayMusic()


**说明**

停止播放音乐文件及混音。


 该方法停止播放伴奏。请在频道内调用该方法。

**返回**

 0 代表成功，其他代表失败


## pauseAudioMusic()


public int pauseAudioMusic()


**说明**

暂停播放音乐文件及混音。


 该方法暂停播放伴奏。请在频道内调用该方法。

**返回**

 0 代表成功，其他代表失败


## resumeAudioMusic()


public int resumeAudioMusic()


**说明**

恢复播放音乐文件及混音。


 该方法恢复混音，继续播放伴奏。请在频道内调用该方法。

**返回**

 0 代表成功，其他代表失败


## getAudioMusicDuration()


public int getAudioMusicDuration()


**说明**

获取音乐文件的时长。


 该方法获取音乐文件时长，单位为毫秒。请在频道内调用该方法。如果返回值 < 0，表明调用失败。

**返回**

 0 代表成功，其他代表失败


## getAudioMusicCurrentPosition()


public int getAudioMusicCurrentPosition()


**说明**

获取音乐文件的播放进度。


 该方法获取当前伴奏播放进度，单位为毫秒。<br>
如需多次调用，请确保调用间隔大于 500 ms。

**返回**

 0 代表成功，其他代表失败


## setAudioMusicPosition()


public int setAudioMusicPosition(int pos)


**说明**

设置音乐文件的播放位置。


 该方法可以设置音频文件的播放位置，这样你可以根据实际情况播放文件，而不是非得从头到尾播放一个文件。单位ms

**参数**

变量名 | 描述
:--- | :---
pos | 整数。进度条位置，单位为毫秒。

**返回**

 0 代表成功，其他代表失败


## playMusicVolume()


public int playMusicVolume(int volume)


**说明**

调节音乐文件的播放音量。


 该方法调节混音里伴奏在本端和远端播放的音量大小。

**参数**

变量名 | 描述
:--- | :---
volume | 伴奏音量范围为 0~100。默认 100 为原始文件音量。

**返回**

 0 代表成功，其他代表失败


## setParams()


public int setParams(String config)


**说明**

私有参数设置接口


**参数**

变量名 | 描述
:--- | :---
config | 具体的私有参数字符串

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


## enableContentInspect()


public int enableContentInspect(boolean enable, int timeInterval)


**说明**

是否开启鉴黄功能
开启视频内容审核后，SDK 会根据你在 ContentInspectConfig 中设置的内容审核模块类型和频率对本地用户发送的视频进行截图、审核和上传。 审核完成后，Agora 内容审核服务器会以 HTTPS 请求的形式，向你的服务器发送审核结果，并将所有截图发送至你指定的第三方云存储。
如果你将 ContentInspectConfig 中的 type 设置为 CONTENT_INSPECT_TYPE_MODERATION，即鉴黄，审核完成后，SDK 会触发 onContentInspectResult 回调，报告鉴黄结果。


**参数**

变量名 | 描述
:--- | :---
enable | 设置是否开启内容审核：<br>true：开启。<br>false：关闭。
timeInterval | 每次截图时间间隔 - 秒

**返回**

 0 代表成功，其他代表失败


## contentInspectExtra()


public int contentInspectExtra(String arguments, [InspectMode](../members/members.md#inspectmode) modes)


**说明**

截图参数


**参数**

变量名 | 描述
:--- | :---
arguments | 透穿外部参数
modes | 鉴黄模式和发送间隔

**返回**

 0 代表成功，其他代表失败


## setAVSyncSource()


public int setAVSyncSource(long uid)


**说明**

关键角色同步去房间号，设置发流端音画同步。


 同一用户可能使用两个设备分别发送音频流和视频流，为保证接收端听到和看到的音频和视频的时间同步性， 你可以在视频发送端调用该方法，并传入音频发送端的频道名、用户 ID。SDK 会以发送的音频流的时间戳为基准进行自动调节 发送的视频流，以保证即使在两个发送端的上行网络情况不一致（如分别使用 Wi-Fi 和 4G 网络）的情况下， 也能让接收到的音视频具有时间同步性。

**参数**

变量名 | 描述
:--- | :---
uid | 用户ID

**返回**

 0 代表成功，其他代表失败


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


## setAudioMode()


public int setAudioMode([RTCAudioMode](../members/members.md#rtcaudiomode) mode)


**说明**

设置音频模式


**参数**

变量名 | 描述
:--- | :---
mode | 声音模式 0：恢复音频路由为默认  1：通话模式  2：音乐模式

**返回**

 0 代表成功，其他代表失败


## setServerAddress()


public int setServerAddress(String ip, int port)


**说明**

调试用 - 设置调试地址


**参数**

变量名 | 描述
:--- | :---
ip | IP地址
port | 端口号

**返回**

 0 代表成功，其他代表失败


## setPlaybackAudioFrameParameters()


public int setPlaybackAudioFrameParameters(int sampleRate, int channel, [RawAudioFrameOpMode](../members/members.md#rawaudioframeopmode) mode, int samplesPerCall)


**说明**

设置播放的声音格式。


 该方法需要在加入频道前调用。

**参数**

变量名 | 描述
:--- | :---
sampleRate | 数据的采样率，可设置为 8000，16000，32000，44100 或 48000。
channel | 可设置为：1: 单声道。2: 双声道。
mode | (0)：只读模式，用户仅从 AudioFrame 获取原始音频数据，不作任何修改。例如，如果用户通过 Agora SDK 采集数据，自己进行 RTMP/RTMPS 推流，则可以选择该模式。<br>(1)：只写模式，用户替换 AudioFrame 中的数据。例如，如果用户自行采集数据，可选择该模式。<br>(2)：读写模式，用户从 AudioFrame 获取数据、修改。例如，如果用户自己有音效处理模块，且想要根据实际需要对数据进行后处理 (例如变声)，则可以选择该模式。
samplesPerCall | 采样点数，如 RTMP/RTMPS 推流应用中通常为 1024

**返回**

 0 成功


## startChannelMediaRelay()


public int startChannelMediaRelay([RTCEngine.RTCChannelMediaRelayConfiguration](../members/members.md#rtcchannelmediarelayconfiguration) channelMediaRelayConfiguration)


**说明**

开始跨房间转推流


**参数**

变量名 | 描述
:--- | :---
channelMediaRelayConfiguration | 跨房间转推配置类

**返回**

 0 成功


## stopChannelMediaRelay()


public int stopChannelMediaRelay()


**说明**

停止跨房间转推流


**返回**

 0 成功


## updateChannelMediaRelay()


public int updateChannelMediaRelay([RTCEngine.RTCChannelMediaRelayConfiguration](../members/members.md#rtcchannelmediarelayconfiguration) channelMediaRelayConfiguration)


**说明**

更新转推流信息


**参数**

变量名 | 描述
:--- | :---
channelMediaRelayConfiguration | 更新跨房间转推配置

**返回**

 0 正确


## checkFeatureSupport()


public int checkFeatureSupport([RTCFeature](../members/members.md#rtcfeature) feature)


**说明**

引擎是否支持某种能力


**参数**

变量名 | 描述
:--- | :---
feature | 要获取的能力类型

**返回**

 返回值: 1: 支持  0: 不支持   负数:错误


## pushExternalAudioFrame()


public int pushExternalAudioFrame(byte data, long timestamp, int sampleRate, int channels, int bytesPerSample, int sourceId)


**说明**

传入数据进入发送或播放


**参数**

变量名 | 描述
:--- | :---
data | 数据
timestamp | 时间戳
sampleRate | 采样率
channels | 通道数
bytesPerSample | 每个采样点占多少字节, 通常为2
sourceId | 0: 音频不发送到远端 1: 发送到远端 进行3A处理. 2: 发送到远端不进行3A处理

**返回**




## setExternalAudioSourceVolume()


public int setExternalAudioSourceVolume(int sourceId, int volume)


**说明**

设置传入数据的音量


**参数**

变量名 | 描述
:--- | :---
sourceId | 0: 音频不发送到远端 1: 发送到远端 进行3A处理. 2: 发送到远端不进行3A处理
volume | 音量 [0, 100]

**返回**




## setRemoteSubscribeFallbackOption()


public int setRemoteSubscribeFallbackOption(int option)


**说明**

设置弱网条件下订阅的音视频流回退选项。网络不理想的环境下，直播音视频的质量都会下降。


 使用该接口并将 option 设置为 STREAM_FALLBACK_OPTION_VIDEO_STREAM_LOW(1) 或者 STREAM_FALLBACK_OPTION_AUDIO_ONLY(2) 后，SDK 会在下行弱网且音视频质量严重受影响时， 将视频流切换为小流，或关断视频流，从而保证或提高音频质量。同时 SDK 会持续监控网络质量，并在网络质量改善时恢复音视频流。<br>
该方法需要在加入频道前调用。

**参数**

变量名 | 描述
:--- | :---
option | 远端订阅流回退处理选项：<br>(0)：下行网络较弱时，不对音视频流作回退处理，但不能保证音视频流的质量<br>(1)：（默认）下行网络较弱时只接收视频小流。该选项只对该方法有效，对 setLocalPublishFallbackOption 方法无效<br>(2)：下行网络较弱时，先尝试只接收视频小流；如果网络环境无法显示视频，则再回退到只接收远端订阅的音频流

**返回**

 0 代表成功，其他代表失败


## applyRemoteStreamSubscribeAdvice()


public int applyRemoteStreamSubscribeAdvice(long uid, int streamType)


**说明**

设置目标拉流的流类型


**参数**

变量名 | 描述
:--- | :---
uid | 目标用户id
streamType | 流类型 0: 大流  1: 小流   2: 音频

**返回**

 0 代表成功，其他代表失败


## setRemoteMixedVolume()


public int setRemoteMixedVolume(int volume)


**说明**

调节本地播放的所有远端用户信号音量。


 该方法调节的是本地播放的所有远端用户混音后的音量。

**参数**

变量名 | 描述
:--- | :---
volume | 播放音量。取值范围为 [0,400]，其中：<br>0: 静音<br>100:（默认）原始音量<br>400: 原始音量的 4 倍（自带溢出保护）

**返回**

 0 代表成功，其他代表失败


## takeLocalViewSnapshot()


public int takeLocalViewSnapshot()


**说明**

获取近端截图


 该方法用于对指定用户的视频流进行截图，生成一张 JPG 格式的图片，并保存至指定的路径。<br>
该方法是异步操作，调用返回时 SDK 并没有真正获取截图。

**返回**

 0 代表成功，其他代表失败


## takeRemoteViewSnapshot()


public int takeRemoteViewSnapshot(long uid)


**说明**

获取拉流视频截图。


 该方法用于对指定用户的视频流进行截图，生成一张 JPG 格式的图片，并保存至指定的路径。<br>
该方法是异步操作，调用返回时 SDK 并没有真正获取截图。

**参数**

变量名 | 描述
:--- | :---
uid | 用户id

>  该方法需要在加入频道后调用。<br>
如果用户的视频经过前处理，例如，添加了水印或美颜，生成的截图会包含前处理效果。


**返回**

 0 代表成功，其他代表失败


## setupLocalVideo()


public int setupLocalVideo(TextureView view)


**说明**

初始化本地视图。


 该方法初始化本地视图并设置本地用户视频显示信息，只影响本地用户看到的视频画面，不影响本地发布视频。 调用该方法绑定本地视频流的显示视窗（View），并设置本地用户视图的渲染模式和镜像模式。

**参数**

变量名 | 描述
:--- | :---
view | 本地视图view

>  请在主线程调用该方法。<br>
如果你希望在通话中更新本地用户视图的渲染或镜像模式，请使用 setLocalRenderMode 方法。


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


## setPreviewResolution()


public int setPreviewResolution(int width, int height)


**说明**

设置预览分辨率


 一般的视频通话或直播中，默认由 SDK 自动控制摄像头的输出参数。在如下特殊场景中，默认的参数通常无法满足需求，或可能引起设备性能问题，我们推荐调用该接口设置摄像头的采集配置

**参数**

变量名 | 描述
:--- | :---
width | 宽度
height | 高度

**返回**

 0 代表成功，其他代表失败


## setLibraryLoadPath()


public static int setLibraryLoadPath(String path)


**说明**

外部设置需要离线加载SO的路径.


 正常情况下业务需要知道他使用的SDK, 是带分离式SO的.可以提前设置, 但如果没有设置,<br>
initWithToken 会返回负数, 提醒用户设置.

**参数**

变量名 | 描述
:--- | :---
path | 需要设置的路径, 业务要注意当前使用的架构 以确认要传入 v7a的路径还是 arm64

**返回**

 0 设置成功


## getConnectionState()


public int getConnectionState()


**说明**

获取连接状态


**返回**

 当前的网络连接状态：<br>
CONNECTION_STATE_DISCONNECTED(1): 网络连接断开。<br>
CONNECTION_STATE_CONNECTING(2): 建立网络连接中。<br>
CONNECTION_STATE_CONNECTED(3): 网络已连接。<br>
CONNECTION_STATE_RECONNECTING(4): 重新建立网络连接中。<br>
CONNECTION_STATE_FAILED(5): 网络连接失败。


## setAudioProfile()


public int setAudioProfile(int profile, int scenario)


**说明**

设置音频编码配置


 该方法需要在 joinChannel 之前设置好，joinChannel 后设置不生效。<br>
通信和直播场景下，音质（码率）会有网络自适应的调整，通过该方法设置的是一个最高码率。<br>
在有高音质需求的场景（例如音乐教学场景）中，建议将 profile 设置为 4，Scenario 设置为 3。

**参数**

变量名 | 描述
:--- | :---
profile | 设置采样率，码率，编码模式和声道数
scenario | 设置音频应用场景 不同的音频场景下，设备的音量类型不同

**返回**

 0(ERR_OK): 方法调用成功。<br>
< 0: 方法调用失败。


## disableVideo()


public int disableVideo()


**说明**

关闭视频模块。
该方法用于关闭视频。可以在加入频道前或者通话中调用，在加入频道前调用，则自动开启纯音频模式，在通话中调用则由视频模式切换为纯音频频模式。调用 enableVideo 方法可开启视频模式。


**返回**

 0(ERR_OK): 方法调用成功。<br>
< 0: 方法调用失败。


## createTextureView()


public TextureView createTextureView()


**说明**

该方法创建 TextureView，适用于需要对视频画面进行缩放、旋转和平移的场景，如屏幕共享


 推荐你在视频通话和直播场景使用 SurfaceView，在需要对视频画面进行缩放、旋转和平移的场景（如屏幕共享场景）使用 TextureView。

>  请在主线程调用该方法。


**返回**

 TextureView


## getErrorDes()


public String getErrorDes(int errorCode)


**说明**

获取错误描述


**参数**

变量名 | 描述
:--- | :---
errorCode | 具体的错误码

**返回**

 对应的错误描述


## switchChannelWithRealToken()


public int switchChannelWithRealToken(String token, String channelName)


**说明**

快速切换直播频道


 当直播频道中的观众想从一个频道切换到另一个频道时，可以调用该方法，实现快速切换。<br>
成功调用该方切换频道后，本地会先收到离开原频道的回调 onLeaveChannel，再收到成功加入新频道的回调 localUserJoindWithUid。<br>
用户成功加入（切换）频道后，默认订阅频道内所有其他用户的音频流和视频流，因此产生用量并影响计费。如果想取消订阅，可以通过调用相应的 mute 方法实现。

**参数**

变量名 | 描述
:--- | :---
token | 在 app 服务端生成的用于鉴权的 Token
channelName | 标识频道的频道名，最大不超过 64 字节。以下为支持的字符集范围（共 89 个字符）：<br>26 个小写英文字母 a-z<br>26 个大写英文字母 A-Z<br>10 个数字 0-9<br>空格<br>"!", "#", "$", "%", "&", "(", ")", "+", "-", ":", ";", "<", "=", ".", ">", "?", "@", "[", "]", "^", "_", " {", "}", "|", "~", ","

>  该方法仅适用直播频道中的观众用户。


**返回**

 0(ERR_OK): 方法调用成功。<br>
< 0: 方法调用失败。<br>
-1(ERR_FAILED): 一般性的错误（未明确归类）。<br>
-2(ERR_INVALID_ARGUMENT): 参数无效。<br>
-5(ERR_REFUSED): 调用被拒绝。可能因为用户角色不是观众。<br>
-7(ERR_NOT_INITIALIZED): SDK 尚未初始化。<br>
-102(ERR_INVALID_CHANNEL_NAME): 频道名无效。请更换有效的频道名。<br>
-113(ERR_NOT_IN_CHANNEL): 用户不在频道内。


