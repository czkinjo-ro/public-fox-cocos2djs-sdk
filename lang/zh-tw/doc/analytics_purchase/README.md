# 依靠流量分析進行消費計測
能夠計測按廣告流入和自然流入的用戶進行的各自銷售額的計測。利用流量分析能夠進行含自然流入廣告在內的不同廣告的消費計測。為了進行依據流量分析的Event計測，請安裝下面的sendEvent方法。※如果希望只計測經由廣告流入的銷售額，可以靠LTV計測來實現，不需要安裝這個功能。<br>※如果是希望计测經由自然流入的銷售額，请安装这个功能。|參數|類型|最大長度|必須|概要|
|:---|:---:|:---:|:---:|:---|
|eventName|String|255|必須|設定能夠識別計測Event的任意名稱。<br>按Event單位來分組，能夠按各自Event進行匯總。|
|action|String|255|任意|設定屬於Event的Action名。可以自由設定。<br>指定各Event的數據範圍按各Action進行匯總。<br>如果不做特別指定，請設定為""。|
|label|String|255|任意|設定屬於Event的Label名。可以自由設定。<br>指定各Action的數據範圍按各Label進行匯總<br>如果不做特別指定，請設定為""。|
|orderID|String|255|任意|訂單號。如果不做特別指定，請設定為""。|
|sku|String|255|任意|商品代號sku。如果不做特別指定，請設定為""。|
|itemName|String|255|必須|商品名|
|price|double||必須|商品單價|
|quantity|int||必須|購入數量|
|currency|String||任意|指定貨幣代碼。如果不指定默認為"JPY"|
在JavaScript上按如下形式書寫
	cc.FoxPlugin.sendEvent(eventName, action, label, orderId, sku, itemName, price, quantity, currency);如果希望同時做LTV計測和消費計測，請在同一個地點安裝LTV和流量分析的各自計測處理。
下面給出了一個消費了9.99美元的計測安裝範例。

	// 依靠LTV計測進行消費計測	cc.FoxPlugin.addParameter("_price", “9.99”);	cc.FoxPlugin.addParameter("_currency", “USD”);	cc.FoxPlugin.sendLtv(成果地点ID);
	// 依靠流量分析進行消費計測
	cc.FoxPlugin.sendEvent(eventName, action, null, orderId, sku, itemName, 9.99, 1, "USD");
