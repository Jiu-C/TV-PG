有缘人注意：本zip目前仅支持"影视","OK影视","EasyBox"使用，其他播放器或基于影视魔改的播放器使用本zip都会导致网盘内容无法播放。
* 本ZIP所加载的资源完全来自网上公开分享的内容，若有版权问题请联系相关网站删除，本ZIP只读取和播放网络公开资源，既不维护也不储存任何网络资源。

****************************************************************
*  把本zip文件解压缩到安卓设备的任意目录                       *
*  然后在播放器的点播接口设定中，指定到解压后目录中的jsm.json  *
****************************************************************

======================================================================================================================================================================
以下所有说明不看也可以正常使用本zip，只是给动手能力强的有缘人更多定制化的可能性。默认设置就可以欣赏绝大部分网络资源，只需要到“网盘及弹幕设置”中扫不同网盘的二维码即可。
======================================================================================================================================================================

提示1：发现影视壳并不能加载最新的jar，如果遇到jar表现异常，或者最新的jar承诺的功能改进没有实现，请清除播放壳app的缓存后强杀播放壳后再试，清除方法1：在壳app的设置里点击“缓存”，清除方法2：设备的应用管理中，清除壳app的数据及缓存。
提示2：迅雷云盘限制极为严格，不要尝试单账号多用户异地使用，或多线程使用，随时可能封号。
提示3：zip包内预置的aliproxy从jar内的assets改为zip内的aliproxy.gz，可以减少jar包对播放器内存的消耗，但因为aliproxy.gz的释出需要使用到壳上的proxy功能，所以如果播放设备安装了多个类似的播放器，可能导致aliproxy释放出错或运行出错。不要尝试在同一个播放设备上运行多个播放壳，也不要尝试把本jar加载到同一个播放设备的不同播放壳上。

可以通过配置中的“网盘及弹幕配置”的视频源来实现快捷方便的获取32位token及opentoken的功能。

复制lib/tokentemplate.json成为lib/tokenm.json，并填写必要的内容

tokenm.json格式说明：
{
"token":"这里填写阿里云盘的32位token，也可以不填写，在播放阿里云盘内容时会弹出窗口，点击QrCode，用阿里云盘app扫码",
"open_token":"这里填写通过alist或其他openapi提供方申请的aliyun openapi token",
"thread_limit":32, //这里是阿里云盘的GO代理的并发协程数或java代理的并发线程数
"is_vip":true, //是否是阿里云盘的VIP用户，设置为true后，使用vip_thread_limit设置的数值来并发加速
"vip_thread_limit":32, //这里是阿里云盘的转存原画并发线程数
"quark_thread_limit":32, //这里是夸克网盘GO代理的并发协程数或java代理的并发线程数，若遇到账号被限制并发数，请将此数值改为10
"quark_vip_thread_limit":32, //这里是夸克网盘设置quark_is_vip:true之后的并发线程数，若遇到账号被限制并发数，请将此数值改为10
"quark_is_vip":false, //本配置项已废弃
"quark_is_guest":false, //本项目设置为false表示是夸克的VIP或88VIP用户，使用更快的多线程加载方式，设置为false表示是纯免费的夸克用户，使用优化限速的多线程加载方式
"vod_flags":"4kz|auto", //这里是播放阿里云的画质选项，4kz代表转存GO原画,4ko代表转存Open原画,其他都代表预览画质,可选的预览画质包括qhd,fhd,hd,sd,ld，
"quark_flags":"4kz|auto", //这里是播放夸克网盘的画质选项，4kz代表转存原画（GO原画），其他都代表转码画质,可选的预览画质包括4k,2k,super,high,low,normal
"uc_thread_limit":0,
"uc_is_vip":false,
"uc_flags":"4kz|auto",
"uc_vip_thread_limit":0,
"thunder_thread_limit":0,
"thunder_is_vip":false,
"thunder_vip_thread_limit":0,
"thunder_flags":"4k|4kz|auto",
"aliproxy":"这里填写外部的加速代理，用于在盒子性能不够的情况下，使用外部的加速代理来加速播放，可以不填写",
"proxy":"这里填写用于科学上网的地址，连接openapi或某些资源站可能会需要用到，可以不填写",
"open_api_url":"https://api.xhofe.top/alist/ali_open/token", //这是alist的openapi接口地址，也可使用其他openapi提供商的地址。
"danmu":true,//是否全局开启阿里云盘所有csp的弹幕支持，聚合类CSP仍需单独设置，例如Wogg, Wobg
"quark_danmu":true,//是否全局开启夸克网盘的所有csp的弹幕支持, 聚合类CSP仍需单独设置，例如Wogg, Wobg
"quark_cookie":"这里填写通过https://pan.quark.cn网站获取到的cookie，会很长，全数填入即可。"
"uc_cookie":"这里填写通过https://drive.uc.cn网站登录获取的cookie",
"thunder_username":"这里填入用户名或手机号，如果是手机号，记得是类似'+86 139123457'这样的格式，+86后有空格才对",
"thunder_password":"密码",
"thunder_captchatoken":"首次使用迅雷网盘时，需要使用app弹出的登陆地址去接码登录，并获取captchaToken，具体方法参考alist网站的文档:https://alist.nn.ci/zh/guide/drivers/thunder.html",
"pikpak_username":"PikPak网盘的用户名",
"pikpak_password":"PikPak网盘的密码",
"pikpak_flags":"4k|auto",
"pikpak_thread_limit":2,
"pikpak_vip_thread_limit":2,
"pikpak_proxy":"用于科学上网连接PikPak网盘的代理服务器地址",
"pikpak_proxy_onlyapi":false
}