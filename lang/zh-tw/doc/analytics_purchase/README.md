# 依靠流量分析進行消費計測

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


下面給出了一個消費了9.99美元的計測安裝範例。

	// 依靠LTV計測進行消費計測

	cc.FoxPlugin.sendEvent(eventName, action, null, orderId, sku, itemName, 9.99, 1, "USD");