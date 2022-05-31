# 核心方法


名称 | 描述
:--- | :---
[RTCEngine()](./RTCEngine/RTCEngine.md#rtcengine) | 引擎创建
[initWithToken()](./RTCEngine/RTCEngine.md#initwithtoken) | 初始化token接口
[init()](./RTCEngine/RTCEngine.md#init) | 引擎初始化
[setRole()](./RTCEngine/RTCEngine.md#setrole) | 设置直播场景下的用户角色
[joinRoom()](./RTCEngine/RTCEngine.md#joinroom) | 加入频道。
[leaveRoom()](./RTCEngine/RTCEngine.md#leaveroom) | 离开频道。
[destory()](./RTCEngine/RTCEngine.md#destory) | 销毁 RtcEngine 实例。
[getConnectionState()](./RTCEngine/RTCEngine.md#getconnectionstate) | 获取连接状态
[switchChannelWithRealToken()](./RTCEngine/RTCEngine.md#switchchannelwithrealtoken) | 快速切换直播频道

# 核心事件


名称 | 描述
:--- | :---
[onLeaveChannel()](./EngineCallback/EngineCallback.md#onleavechannel) | 用户离开房间成功
[localUserJoindWithUid()](./EngineCallback/EngineCallback.md#localuserjoindwithuid) | 加入频道回调。
[remoteUserJoinWitnUid()](./EngineCallback/EngineCallback.md#remoteuserjoinwitnuid) | 远端用户（通信场景）/主播（直播场景）加入当前频道回调。
[didOfflineOfUid()](./EngineCallback/EngineCallback.md#didofflineofuid) | 远端用户（通信场景）/主播（直播场景）离开当前频道回调。
[didOccurError()](./EngineCallback/EngineCallback.md#didoccurerror) | 发生错误回调。
[connectionChangedToState()](./EngineCallback/EngineCallback.md#connectionchangedtostate) | 网络连接状态已改变回调。

# 音频管理


名称 | 描述
:--- | :---
[enableLocalAudio()](./RTCEngine/RTCEngine.md#enablelocalaudio) | 开启/关闭本地音频采集。
[muteLocalAudio()](./RTCEngine/RTCEngine.md#mutelocalaudio) | 取消或恢复发布本地音频流。
[muteRemoteAudio()](./RTCEngine/RTCEngine.md#muteremoteaudio) | 取消或恢复订阅指定远端用户的音频流。
[muteAllRemoteAudio()](./RTCEngine/RTCEngine.md#muteallremoteaudio) | 取消或恢复订阅所有远端用户的音频流。
[muteAudio()](./RTCEngine/RTCEngine.md#muteaudio) | 停止/恢复发送本地音频流,取消或恢复发布本地音频流。
[setDefaultMuteAllRemoteAudioStreams()](./RTCEngine/RTCEngine.md#setdefaultmuteallremoteaudiostreams) | 设置是否默认接收音频流。 - 后续通过 mute false打开
[setRemoteMixedVolume()](./RTCEngine/RTCEngine.md#setremotemixedvolume) | 调节本地播放的所有远端用户信号音量。

# 视频管理


名称 | 描述
:--- | :---
[enableVideo()](./RTCEngine/RTCEngine.md#enablevideo) | 启用视频模块。
[enableLocalVideo()](./RTCEngine/RTCEngine.md#enablelocalvideo) | 开启/关闭本地视频采集。
[muteLocalVideo()](./RTCEngine/RTCEngine.md#mutelocalvideo) | 取消或恢复发布本地视频流。
[muteRemoteVideo()](./RTCEngine/RTCEngine.md#muteremotevideo) | 取消或恢复订阅指定远端用户的视频流。
[muteAllRemoteVideo()](./RTCEngine/RTCEngine.md#muteallremotevideo) | 取消或恢复订阅所有远端用户的视频流。
[setLocalRenderMode()](./RTCEngine/RTCEngine.md#setlocalrendermode) | 设置本地视频显示模式。
[setRemoteRenderMode()](./RTCEngine/RTCEngine.md#setremoterendermode) | 设置远端渲染方式
[setRemoteRenderMode()](./RTCEngine/RTCEngine.md#setremoterendermode) | 设置远端视频显示模式。
[createRendererView()](./RTCEngine/RTCEngine.md#createrendererview) | 创建 RendererView。
[startPreview()](./RTCEngine/RTCEngine.md#startpreview) | 开启视频预览。
[stopPreview()](./RTCEngine/RTCEngine.md#stoppreview) | 停止本地视频预览。
[muteVideo()](./RTCEngine/RTCEngine.md#mutevideo) | 停止/恢复发送本地视频流,取消或恢复发布本地视频流。
[setDefaultMuteAllRemoteVideoStreams()](./RTCEngine/RTCEngine.md#setdefaultmuteallremotevideostreams) | 设置是否默认接收视频流。 - 后续通过 mute false打开
[createTextureView()](./RTCEngine/RTCEngine.md#createtextureview) | 该方法创建 TextureView，适用于需要对视频画面进行缩放、旋转和平移的场景，如屏幕共享

# 本地媒体事件


名称 | 描述
:--- | :---
[onLocalVideoStateChanged()](./EngineCallback/EngineCallback.md#onlocalvideostatechanged) | 本地视频状态改变回调
[onLocalAudioStateChanged()](./EngineCallback/EngineCallback.md#onlocalaudiostatechanged) | 本地音频状态改变回调
[onPublishVideoStateChanged()](./EngineCallback/EngineCallback.md#onpublishvideostatechanged) | 发布视频状态变化回调
[onPublishAudioStateChanged()](./EngineCallback/EngineCallback.md#onpublishaudiostatechanged) | 发布音频状态变化回调

# 远端媒体事件


名称 | 描述
:--- | :---
[onSubscribeVideoStateChanged()](./EngineCallback/EngineCallback.md#onsubscribevideostatechanged) | 订阅视频状态通知回调
[onSubscribeAudioStateChanged()](./EngineCallback/EngineCallback.md#onsubscribeaudiostatechanged) | 订阅音频状态通知回调
[remotefirstVideoRecvWithUid()](./EngineCallback/EngineCallback.md#remotefirstvideorecvwithuid) | 已完成远端视频首帧解码回调。
[remotefirstAudioRecvWithUid()](./EngineCallback/EngineCallback.md#remotefirstaudiorecvwithuid) | 已接收远端音频首帧回调。
[didAudioMuted()](./EngineCallback/EngineCallback.md#didaudiomuted) | 远端用户停止/恢复发送音频流回调。
[didVideoMuted()](./EngineCallback/EngineCallback.md#didvideomuted) | 远端用户取消或恢复发布视频流回调。

# 数据统计事件


名称 | 描述
:--- | :---
[onLocalVideoStats()](./EngineCallback/EngineCallback.md#onlocalvideostats) | 本地视频状态回调
[onLocalAudioStats()](./EngineCallback/EngineCallback.md#onlocalaudiostats) | 本地音频状态回调
[onRemoteVideoStats()](./EngineCallback/EngineCallback.md#onremotevideostats) | 远端视频状态回调
[onRemoteAudioStats()](./EngineCallback/EngineCallback.md#onremoteaudiostats) | 远端音频状态回调
[reportRtcStats()](./EngineCallback/EngineCallback.md#reportrtcstats) | 当前通话统计回调。 该回调在通话中每两秒触发一次。

# 音乐播放


名称 | 描述
:--- | :---
[startPlayMusic()](./RTCEngine/RTCEngine.md#startplaymusic) | 播放本地音乐
[startPlayMusic()](./RTCEngine/RTCEngine.md#startplaymusic) | 开始播放音乐文件，该方法支持将本地或在线音乐文件和麦克风采集的音频进行混音或替换
[stopPlayMusic()](./RTCEngine/RTCEngine.md#stopplaymusic) | 停止播放音乐文件及混音。
[pauseAudioMusic()](./RTCEngine/RTCEngine.md#pauseaudiomusic) | 暂停播放音乐文件及混音。
[resumeAudioMusic()](./RTCEngine/RTCEngine.md#resumeaudiomusic) | 恢复播放音乐文件及混音。
[getAudioMusicDuration()](./RTCEngine/RTCEngine.md#getaudiomusicduration) | 获取音乐文件的时长。
[getAudioMusicCurrentPosition()](./RTCEngine/RTCEngine.md#getaudiomusiccurrentposition) | 获取音乐文件的播放进度。
[setAudioMusicPosition()](./RTCEngine/RTCEngine.md#setaudiomusicposition) | 设置音乐文件的播放位置。
[playMusicVolume()](./RTCEngine/RTCEngine.md#playmusicvolume) | 调节音乐文件的播放音量。

# 旁路转推


名称 | 描述
:--- | :---
[addPublishStreamUrl()](./RTCEngine/RTCEngine.md#addpublishstreamurl) | 推流到CDN,增加旁路推流地址
[removePublishStreamUrl()](./RTCEngine/RTCEngine.md#removepublishstreamurl) | 移除CDN推流，删除旁路推流地址
[setRtmpConfig()](./RTCEngine/RTCEngine.md#setrtmpconfig) | 设置rmpt配置，该方法用于旁路推流的视图布局及音频设置等。

# 跨频道媒体流转发


名称 | 描述
:--- | :---
[startChannelMediaRelay()](./RTCEngine/RTCEngine.md#startchannelmediarelay) | 开始跨房间转推流
[stopChannelMediaRelay()](./RTCEngine/RTCEngine.md#stopchannelmediarelay) | 停止跨房间转推流
[updateChannelMediaRelay()](./RTCEngine/RTCEngine.md#updatechannelmediarelay) | 更新转推流信息

# 事件监听


名称 | 描述
:--- | :---
[setRtcEngineEventListener()](./RTCEngine/RTCEngine.md#setrtcengineeventlistener) | 设置engine事件监听
[setRtcEngineEventObserver()](./RTCEngine/RTCEngine.md#setrtcengineeventobserver) | 设置补充回调
[setAudioObserver()](./RTCEngine/RTCEngine.md#setaudioobserver) | 设置混音后音视频裸数据回调
[setMediaVideoProcessListener()](./RTCEngine/RTCEngine.md#setmediavideoprocesslistener) | 设置视频采集/播放回调

