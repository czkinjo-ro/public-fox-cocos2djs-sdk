## sendConversion的詳細

利用`sendConversion:`方法能夠進行Install計測。如果使用Cookie計測手法，外部瀏覽器將被啟動。這個時候，可以把外部瀏覽器的跳轉目的地用字符串形式指定到`sendConversion:`的參數裡。

編輯項目的源代碼，對於APP啟動時調用畫面的`AppDelegate:applicationDidFinishLaunching:`方法等，請按下面那样来安装在APP啟動時肯定處理的地方。

> 【注意事项】
沒有特別的理由請將`sendConversion`安裝在APP啟動時調用的`AppDelegate:applicationDidFinishLaunching`方法裡。安裝在別的地點可能無法正確計測安裝數。
在沒有安裝`AppDelegate:applicationDidFinishLaunching`的狀態下投放安裝成果型廣告的時候，請一定事先通知廣告代理店或者媒體負責人。不能正常計測的狀態下投放安裝成果型廣告，可能被要求支付超過計測安裝數的廣告費用。


包含頭文件

	#include "Cocos2dxFox.h"

添加成果通知的代碼

	FoxPlugin::sendConversion(“default”);

通常在sendConversion的參數裡像上面那樣輸入@"default"。默認是顯示準備好的標準頁面，可以在FOX管理畫面裡任意設定跳轉目標頁面的URL。

想要跳轉至特定URL，或者想用APP動態生成URL的時候，請設定URL字符串。

	FoxPlugin::sendConversion(“http://yourhost.com/yourpage.html”);

可以在sendConversion方法的第二個參數裡傳遞廣告主終端ID。比如，如果想用APP起動時生成的UUID和初次啟動的成果綁定到一起做管理，可以利用這個方法。

	FoxPlugin::sendConversion("default", "your unique id");

> 作為剛啟動後的處理需要實際安裝`sendConversion`，像登錄ID這樣的用戶行為相伴的值無法通過參數傳遞。
