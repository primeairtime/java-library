**PRIME AIRTIME**<br/>
**primeairtime pa = new primeairtime()**<br/>
>prime_setting.token = "#########";//**if use_token is set to true**\
>prime_setting.use_token = false; // **TRUE or FALSE**\
>prime_setting.username = "########@yahoo.com"; //**if use_token is set to false**\
>prime_setting.password = "#######"; //**if use_token is set to false**\
>prime_setting.enviroment = "test"; //**live**\


> pa.get_key();\
> pa.reauth_key();\
> pa.set_key();


**ACCOUNT STATUS**
>*pa.accounts();*\
>*pa.status();*<br/>

**BATCH OPERATION**
> pa.batch()\
> pa.batch("myfeff"); **method 1**\
> pa.id = "myfeff"; **method 2**\
> pa.batch();\
> pa.set_id("myfeff").batch(); **method 3**<br/><br/>

**VERIFY TRANSACTION**
>pa.set_ref("myfeff").log();<br/><br/>

**AIRTIME/DATA TOPUP**
>string[] mobile = {"2348183874966", "2348183874966"};////string[] mobile = {"2348183874966"};  //bulk \
>pa.topup(false).info(mobile); ** true airtime, false data** <br/><br/>


**BATCH TOPUP **
 ```
string requestBody = '{
  "numbers" : [
    {
      "msisdn" : "2348183874966",
      "product_id" : "MFIN-2-OR",
      "denomination" : 1
    },
    {
      "msisdn" : "2348183874966",
      "product_id": "MFIN-2-OR",
      "denomination" : 1
    }
  ]
}';
```

**SINGLE TOPUP**
```
string requestBody = '{
        "msisdn" : "2348183874966",
        "product_id": "MFIN-2-OR",
        "denomination" : 50,
        "send_sms" : false,
        "sms_text" : "",
        "customer_reference":"RE4534783248234"
    }';
```
>pa.topup(true).exec(requestBody);  **true airtime, false data**


**LIST ALL PRODUCT BY PAGE**
> string page = 1;
> pa.set_type("airtime").products(page);


**BILLS**
> pa.billpay(); -*** *Get Country List* ***
> pa.set_iso("NG").billpay(); -- **List of services in specified country **
> pa.set_iso("NG").set_service_id("electricity").billpay();  **List of products available for given service in country  **
> pa.set_service_id("dstv").set_product_id("BPD-NGCA-AQA").billpay(); **List of product options available for given service in country (multichoice) **
> pa.set_service_id("electricity").set_product_id("BPE-NGEK-OR").billpay("027140081201");  **VALIDATE Bills**</br>

**Perform Electricity topup**
```
string requestBody = "{\"meter\":\"027140081201\",\"prepaid\":true,\"denomination\":\"50\", \"product_id\":\"BPE-NGEK-OR\",\"customer_reference\":\"myreg\"}";
```
>pa.set_account("027140081201").set_service_id("electricity").set_product_id("BPE-NGEK-OR").billpay(requestBody);** PAY Bills**

**Perform DSTV/Internet/Misc topup**
```
string requestBody = "{\"meter\":\"10441003943\",\"prepaid\":false, \"customer_reference\":\"32983278JsDPO\"}";
```
>pa.set_account("10441003943").set_service_id("dstv").set_option("FTAE36").set_product_id("BPD-NGCA-AQA").billpay(requestBody); **PAY Bills**


** ELECTRICITY REQUEST BODY**
```
string requestBody = '{
    "meter":"54150205877",
    "prepaid":true,
    "denomination":"50",
    "product_id":"BPE-NGIK-OR",
    "customer_reference":"myref"
}';
```

**DSTV/INTERNET/MISC REQUEST BODY**
```
string requestBodyb = '{
    "meter":"10441003943",
    "prepaid":false,
    "product_id":"BPD-NGCA-AQA",
    "option":"FTAE36",
    "customer_reference":"myref"
}';
```
>pa.set_account("027140081201").set_service_id("electricity").billpay(requestBody); **Perform bill topup **




**BANK TRANSFER**
>pa.ft().access(); ** Check access**
>pa.ft().banks(); **list banks and sort code**
>pa.ft("6761025013").set_sort_code("000003").loogup();  **Account lookup**
```
string requestBody = '{
    "amount" : 500.50,
    "customer_reference" : "32983298JDPOKW"
}';
```
>pa.ft("0069317906").set_sort_code("000014").transfer(requestBody);**execute transfer**


```
string requestBody = '{
  "message" : "This is a test message from API"
}';
```
>pa.set_account("0069317906").sms(requestBody);**execute transfer**
