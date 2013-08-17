==已知bugs==

暂无


MoeUpload

=========
MediaWIKI插件，现在用于萌娘百科

适用版本为MediaWIKI1.20+ （1.21未测试，不保证可用）

使用方法:

LocalSettings.php 加入

require_once( "$IP/extensions/MoeUpload/MoeUpload.php" );

==
===插件加速优化===


由于这个插件本身写的相当简单，并没有使用mediawiki自带的resourceloader功能进行JS和css合并。

如果你对网站加载速度有强迫症一般的要求，想要减少由额外两个http请求造成的0.2s左右的延迟

你可以将MoeUpload.js和MoeUpload.css两个文件内的内容复制到MediaWiki:Common.css 和 MediaWiki:Common.js这两个页面里。

然后删除MoeUpload.php里的
function onBeforePageDisplay( &$out, &$skin ) {
  global $wgScriptPath;
	$path = "$wgScriptPath/extensions/MoeUpload/MoeUpload.js";
	$out->addScriptFile( $path );
	return true;
}
