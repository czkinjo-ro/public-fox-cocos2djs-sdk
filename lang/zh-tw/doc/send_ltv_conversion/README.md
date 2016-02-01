## sendLtvConversion的詳細

利用sendLtvConversion方法，能夠計測廣告流入別的消費金額和加入會員數等。為了計測，須在任意地點添加进行LTV成果通信的代码。

在成果到達後執行的程式中加入SDK的處理程式。譬如說，會員登錄和APP內消費後的消費計測，是將LTV計測處理記述在登錄、消費處理實行後的回調方法內。

如果成果發生在APP內部，請如同以下記述在成果處理裡面。
在JavaScript裡書寫LTV成果計測代碼

添加成果通知的代碼

	cc.FoxPlugin.sendLtv(成果地点ID);

> 成果地點ID(必須)：請輸入由管理員所告知的數值。

在APP內部的成果裡能夠包含廣告主終端ID（會員ID等），以此為基準進行成果計測。如果想要添加廣告主終端ID到LTV成果裡，請按下面那樣來記述。
	cc.FoxPlugin.sendLtv(成果地点ID, "広告主端末ID");

> 成果地點ID(必須)：請輸入由管理員所告知的數值。廣告主終端ID（任意）：廣告主管理的唯一識別子（會員ID等）。能指定的值是64文字以內的半角數字。
APP內計測時，可以把參數作為可選項來設定。

	cc.FoxPlugin.addParameter("參數名", "值");

能指定的參數如下。

|參數名|概要|
|:------|:------|
|_sku|Stock Keeping Unit(商品管理代號SKU)<br>（最大32位半角英文數字）<br>在商品的庫存管理的時候請使用|
|_price|Price<br>（整数値　日圓）<br>管理銷售金額時請使用。|
|_currency|Currency<br>（3位半角英文的貨幣代碼）<br>按不同幣種統計消費金額時請使用。<br>沒有設定貨幣時，Price會默認按JPY（日圓）來處理|
|也可以任意添加參數|FoxPlugin::addParameter(“參數名”, “値”);<br>※1 如果設定了相同的參數名，後者有效。<br>※2 請不要在參數名的開頭使用下劃線（"_"）。<br>※3 不能使用半角英文數字以外的字符。|

在_currency裡用[ISO 4217](http://ja.wikipedia.org/wiki/ISO_4217)定義的貨幣代碼來指定。

設定範例：

	cc.FoxPlugin.addParameter("_sku", “ABC1234”);	cc.FoxPlugin.addParameter("_price", “2000”);
	cc.FoxPlugin.addParameter("_currency", “JPY”);	cc.FoxPlugin.addParameter(“my_param”, “ABC”);	cc.FoxPlugin.sendLtv(70, “Taro”);
