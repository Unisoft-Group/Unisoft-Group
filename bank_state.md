<p align="center">
    <a href="https://github.com/Unisoft-Group/Unisoft-Group" target="_blank">
        <img src="assets/image/bank.png" height="100px">
    </a>
    <h1 align="center">Bank State</h1>
    <h4 align="center">Version 1.0</h4>
    <br>
</p>


Branch
------------
 - 00996 - Tashkent Branch



REQUEST
------------

All you need send get **request** url below

      https://core.unired.uz/api/open/bank/state
    
You will get **response** either **result** or **error**

--------------------------------------------------------------

INFO: We added for specific date getting result of Bank State 
YOu can use this functionality sending GET request with body below

- `"date"` - specific date in format DD/MM/YYYY

```metadata json
{
    "date":"01/11/2021"
}
    
```  
WARNING: In response we return reponse body with result (object) including only 

 - code,
 ```metadata json
 "code": {
            "local": "02000",
            "branch": "00996"
        }
```  
      
 - state objects. 

```metadata json
  "state": {
            "code": "O",
            "message": "открыт"
        }
```

! Please ignore 
  - date 
  - time_stamp objects

--------------------------------------------------------------

### Result

```metadata json
{
    "jsonrpc": "2.0",
    "id": 1619427500,
    "status": true,
    "origin": "bank.state",
    "result": {
        "code": {
            "local": "02000",
            "branch": "00996"
        },
        "state": {
            "code": "O",
            "message": "открыт"
        },
        "date": {
            "open": "2021-04-26 11:18:20",
            "close": null
        },
        "time_stamp": {
            "created_at": "2021-04-26T06:18:20.000000Z",
            "updated_at": "2021-04-26T06:18:20.000000Z"
        }
    },
    "host": {
        "host": "UniSoft",
        "time_stamp": "2021-04-26 13:58:20"
    }
}
```      
**Result:**

 - `"id"` - as jsonrpc 2.0 
 - `"status"` - true 
 - `"origin"` - in which response returned
 - `"result"` - data object about bank state
 

- `"code"` - code information in object 
  ```metadata json
     "code": {
            "local": "02000",
            "branch": "00996"
        }
  
 - `"local"` - 
 - `"branch"` - 
  
 
 - `"state"` - state information in object
 ```metadata json
      "state": {
            "code": "O",
            "message": "открыт"
        }
```
 - `"code"` -  
 - `"message"` - 




 
 - `"date"` - holds information about open and close date Universalbank JSC
  ```metadata json
         "date": {
            "open": "2021-04-26 11:18:20",
            "close": null
        },
 ```
 - `"open"` - 
 - `"close"` - if it is null branch is ACTIVE


- `"time_stamp"` - state information in object
 ```metadata json
      "time_stamp": {
            "created_at": "2021-04-26T06:18:20.000000Z",
            "updated_at": "2021-04-26T06:18:20.000000Z"
        }
```
- `"created_at"` -
- `"updated_at"` -


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
 
 
 Last update: 26/04/2021 by "Unisoft"

 Authors: Muzaffar Makhkamov & Botir Ro'zikulov 

