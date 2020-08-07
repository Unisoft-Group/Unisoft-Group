<p align="center">
    <a href="https://github.com/Unisoft-Group/Unisoft-Group" target="_blank">
        <img src="assets/image/exchange.png" height="100px">
    </a>
    <h1 align="center">Exchange rate</h1>
    <h4 align="center">Version 1.0</h4>
    <br>
</p>


Currencies available
------------
 - USD - US Dollar
 - EUR - Euro
 - GBP - Pound Sterling
 - CHF - Swiss Franc
 - JPY - Japan Yen
 - RUB - Russian Ruble


REQUEST
------------

All you need send get **request** url below

      https://core.unired.uz/api/open/rate
    
You will get **response** either **result** or **error**

### Result

```metadata json
     {
         "jsonrpc": "2.0",
         "id": 123456789,
         "status": true,
         "origin": "exchange.rate",
         "result": [
             {
                 "code": "840",
                 "code_name": "USD",
                 "rate": {
                     "cb": "10209.86",
                     "buy": "10210",
                     "sell": "10250"
                 },
                 "diff": {
                     "cb": null,
                     "buy": null,
                     "sell": null
                 },
                 "last_update": {
                     "cb": "04.08.2020",
                     "ub": "04.08.2020"
                 },
                 "name": {
                     "uz": "AQSH dollari",
                     "uz_cr": "АҚШ доллари",
                     "ru": "Доллар США",
                     "en": "US Dollar"
                 }
             }
    
             }
         ],
         "host": {
             "host": "UniSoft",
             "time_stamp": "2020-08-08 00:00:01"
         }
     }
```      
**Result:**

 - `"id"` - as jsonrpc 2.0 
 - `"status"` - true 
 - `"origin"` - in which response returned
 - `"result"` - data object about exchange rate for currency
 - `"code"` - currency code 
 - `"code_name"` - currency code name in abr.
  
 
 - `"rate"` - rate information in object
 ```metadata json
      "rate": {
           "cb": "10209.86",
           "buy": "10210",
           "sell": "10250"
       }
```
 - `"cb"` - Currency value from Central Bank of Uzbekistan 
 - `"buy"` - Currency value of buy price in Universalbank JSC
 - `"sell"` - Currency value of sell price in Universalbank JSC


 - `"diff"` - difference of 2 value such as last update of exchange rate. If values in object `cb` and `ub` "-" decrease, "+" for increase else "0" no any change 
  ```metadata json
      "diff": {
            "cb": null,
            "buy": null,
            "sell": null
        }
 ```
 - `"cb"` - Difference of currency value from Central Bank of Uzbekistan
 - `"buy"` - Difference of currency in buy price of Universalbank JSC
 - `"sell"` - Difference of currency in sell price of Universalbank JSC
 
 
 - `"last_update"` - holds information about last updated date in CBU or Universalbank JSC
  ```metadata json
        "last_update": {
            "cb": "04.08.2020",
            "ub": "04.08.2020"
         }
 ```
 - `"cb"` - updated date from CBU in format `dd-mm-yy`
 - `"ub"` - updated date from Universalbank JSC in format `dd-mm-yy`
 
 
 - `"name"` - object contains currency full name in different languages
  ```metadata json
        "name": {
             "uz": "AQSH dollari",
             "uz_cr": "АҚШ доллари",
             "ru": "Доллар США",
             "en": "US Dollar"
          }
 ```
 - `"uz"` - Uzbek 
 - `"uz_cr"` - Uzbek cyrillic
 - `"ru"` - Russian 
 - `"en"` - English
 
 
 - `"host"` - Data provider info 
  ```metadata json
        "host": {
             "host": "UniSoft",
             "time_stamp": "2020-08-08 00:00:01"
         }
 ```
 - `"host"` - Host name
 - `"time_stamp"` - Time stamp of response that data retrieved from host in format `yy-mm-dd h:i:s`





Error
-------------
If response returns **error** you may get in such format below

```metadata json
    {
        "jsonrpc": "2.0",
        "status": false,
        "origin": "connection",
        "error": {
            "code": 500,
            "message": {
                "uz": "Servis vaqtinchalik mavjud emas",
                "ru": "Сервис временно недоступен",
                "en": "The service is temporarily unavailable"
            }
        },
        "id": null,
        "host": {
            "host": "UniSoft",
            "time_stamp": "2020-08-08 00:00:01"
        }
    }    
```    

 - `"id"` - as jsonrpc 2.0 
 - `"status"` - false 
 - `"origin"` - in which response returned
 
 
 - `"error"` - data object about detailed information
 ```metadata json
      "code": 500,
              "message": {
                  "uz": "Servis vaqtinchalik mavjud emas",
                  "ru": "Сервис временно недоступен",
                  "en": "The service is temporarily unavailable"
              }
```
- `"code"` - error code
 - `"message"` - data object about detailed information
    - `"uz"` - Uzbek 
    - `"ru"` - Russian 
    - `"en"` - English
 
 
 - `"host"` - Data provider info 
  ```metadata json
        "host": {
             "host": "UniSoft",
             "time_stamp": "2020-08-08 00:00:01"
         }
 ```
 - `"host"` - Host name
 - `"time_stamp"` - Time stamp of response that data retrieved from host in format `yy-mm-dd h:i:s`
 
 
 Last update: 08/07/2020 by "Unisoft"

