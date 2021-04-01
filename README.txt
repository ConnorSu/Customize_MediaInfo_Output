# Customize_MediaInfo_Output
Customize MediaInfo Output, My MediaInfo Template
自定义MediaInfo输出，我的MediaInfo模板

MediaInfo介绍略过，想必各位影音迷都已了解
如果以“Text/文本”格式输出视频信息，那真是一大堆文本，很难阅读，其实我们也只关注几个点而已
例如：视频编码、HDR、大小、时长、音轨、字幕等等

下边是我的自定义模板，将我关注的信息点都涵盖进来了

★General★
Filename.......: Godzilla.vs.Kong.2021.2160p.REPACK.HMAX.WEB-DL.DDP5.1.Atmos.HDR.HEVC-MZABI
Container......: Matroska
Duration.......: 1 h 53 min
Size...........: 14.8 GiB
★Video★
Codec..........: HEVC Main 10@L5@Main 10 bits
HDR............: SMPTE ST 2086, HDR10 compatible
Resolution.....: 3840x2160
Aspect ratio...: 16:9
Bit rate.......: 17.9 Mb/s
Frame rate.....: 23.976 (24000/1001) FPS
★Audio★
Format.........: E-AC-3 JOC Dolby Digital Plus with Dolby Atmos
Channels.......: 6 channels
Bit rate.......: 768 kb/s
Language.......: English English
★Subtitle★
Language.......: #1 UTF-8 English English
Language.......: #2 UTF-8 English English [SDH]
★Screenshots★

MediaInfo 的自定义模板存储在 C:\Users\[你的用户名]]\AppData\Roaming\MediaInfo\Plugin\Custom 根目录中，格式是.csv，实际只需要用文本编辑器打开就能阅读编辑。

以下是我的.csv文本内容，阁下只需要粘贴进记事本，保存至上述路径，将文件扩展名设置成.csv即可在MediaInfo的自定义模板中调用

General;"★General★\r\nFilename.......: %FileName%
Container......: %Format%
Duration.......: %Duration/String%
Size...........: %FileSize/String%
"
Video;"★Video★\r\nCodec..........: %Format/String% %Format_Profile% %BitDepth/String%
HDR............: %HDR_Format/String%
Resolution.....: %Width%x%Height%
Aspect ratio...: %DisplayAspectRatio/String%
Bit rate.......: %BitRate/String%
Frame rate.....: %FrameRate/String%
"
Audio;"★Audio★\r\nFormat.........: %Format/String% %Format_Commercial_IfAny%
Channels.......: %Channel(s)/String%
Bit rate.......: %BitRate/String%
Language.......: %Language/String1% %Title%
"
Text;Language.......: #%StreamKindPos% %Format% %Language/String% %Title%\r\n
Chapters
File_Begin
File_End;★Screenshots★
Page_Begin
Page_Middle
Page_End
General_Begin
General_End
Video_Begin
Video_Middle
Video_End
Audio_Begin
Audio_Middle
Audio_End
Text_Begin;★Subtitle★\r\n
Text_Middle
Text_End
Chapters_Begin
Chapters_Middle
Chapters_End
