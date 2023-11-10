# Customize_MediaInfo_Output
Customize MediaInfo Output, My MediaInfo Template
自定义MediaInfo输出，我的MediaInfo模板

MediaInfo介绍略过，想必各位影音迷都已了解
如果以“Text/文本”格式输出视频信息，那真是一大堆文本，很难阅读，其实我们也只关注几个点而已
例如：视频编码、HDR、大小、时长、音轨、字幕等等

下边是我的自定义模板，将我关注的信息点都涵盖进来了

★General★
Filename.......: Mission.Impossible.II.2000.BluRay.2160p.x265.10bit.HDR.3Audio.mUHD-FRDS
Container......: Matroska
Duration.......: 02:03:35.742
Size...........: 30.3 GiB
★Video★
Codec..........: HEVC Main 10@L5.1@High 10 bits
Scan type......: 
HDR format.....: 
Color primaries: BT.2020
Resolution.....: 3840x1636
Aspect ratio...: 2.35:1
Bit rate.......: 26.5 Mb/s
Frame rate.....: 23.976 (24000/1001) FPS
★Audio★
Format.........: MLP FBA / Dolby TrueHD
Channels.......: 6 channels
Bit rate.......: 3 490 kb/s
Language.......: English 英语THD
★Audio★
Format.........: AC-3 / Dolby Digital
Channels.......: 6 channels
Bit rate.......: 640 kb/s
Language.......: English 英语AC3
★Audio★
Format.........: DTS XLL / DTS-HD Master Audio
Channels.......: 6 channels
Bit rate.......: 4 330 kb/s
Language.......: Chinese 上译国语DTSHD
★Subtitle★
Language.......: #1 PGS Chinese 蓝光原盘简中
Language.......: #2 PGS Chinese 国配简中
Language.......: #3 PGS Chinese 简英双语
Language.......: #4 PGS English 英文


MediaInfo 的自定义模板存储在 C:\Users\[你的用户名]]\AppData\Roaming\MediaInfo\Plugin\Custom 或安装路径，比如：C:\Program Files\MediaInfo\Plugin\Custom 根目录中，格式是.csv，实际只需要用文本编辑器打开就能阅读编辑。

以下是我的.csv文本内容，阁下只需要粘贴进记事本，保存至上述路径，将文件扩展名设置成.csv即可在MediaInfo的自定义模板中调用

General;"★General★\r\nFilename.......: %FileName%
Container......: %Format%
Duration.......: %Duration/String3%
Size...........: %FileSize/String%
"
Video;"★Video★\r\nCodec..........: %Format/String% %Format_Profile% %BitDepth/String%
Scan type......: %ScanType/String%
HDR format.....: %HDR_Format/String%
Color primaries: %colour_primaries%
Resolution.....: %Width%x%Height%
Aspect ratio...: %DisplayAspectRatio/String%
Bit rate.......: %BitRate/String%
Frame rate.....: %FrameRate/String%
"
Audio;"★Audio★\r\nFormat.........: %Format/String% / %Format_Commercial_IfAny%
Channels.......: %Channel(s)/String%
Bit rate.......: %BitRate/String%
Language.......: %Language/String1% %Title%
"
Text;Language.......: #%StreamKindPos% %Format% %Language/String% %Title%\r\n
Chapters
File_Begin
File_End
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

相信阁下注意到，上述的音轨和字幕中，语言出现了两次，这是因为，语言的标签和音轨、字幕的标题都填写了语言，阁下可以将 %Title% 参数删除
