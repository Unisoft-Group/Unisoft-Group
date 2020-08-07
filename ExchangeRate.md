<p align="center">
    <a href="https://gitlab.com/sanjaruzb/test" target="_blank">
        <img src="https://gitlab.com/sanjaruzb/test/-/raw/master/favicon.ico" height="100px">
    </a>
    <h1 align="center">Exchange rate</h1>
    <br>
</p>

version 1.


REQUEST
------------

All you need send get **request** url below

    https://core.unired.uz/api/open/rate
    
You will get **response** either **result**

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
    
If response returns **error**

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
    
Install DB for i18n

    php yii migrate --migrationPath=@yii/i18n/migrations/



CONFIGURATION
-------------

### Database

Edit the file `config/db.php` with real data, for example:

```php
return [
    'class' => 'yii\db\Connection',
    'dsn' => 'mysql:host=localhost;dbname=yii2basic',
    'username' => 'root',
    'password' => '1234',
    'charset' => 'utf8',
];
```

**NOTES:**
- Yii won't create the database for you, this has to be done manually before you can access it.
- Check and edit the other files in the `config/` directory to customize your application as required.
- Refer to the README in the `tests` directory for information specific to basic application tests.


TESTING
-------

Tests are located in `tests` directory. They are developed with [Codeception PHP Testing Framework](http://codeception.com/).
By default there are 3 test suites:

- `unit`
- `functional`
- `acceptance`

Tests can be executed by running

```
vendor/bin/codecept run
```

The command above will execute unit and functional tests. Unit tests are testing the system components, while functional
tests are for testing user interaction. Acceptance tests are disabled by default as they require additional setup since
they perform testing in real browser. 


### Running  acceptance tests

To execute acceptance tests do the following:  

1. Rename `tests/acceptance.suite.yml.example` to `tests/acceptance.suite.yml` to enable suite configuration

2. Replace `codeception/base` package in `composer.json` with `codeception/codeception` to install full featured
   version of Codeception

3. Update dependencies with Composer 

    ```
    composer update  
    ```

4. Download [Selenium Server](http://www.seleniumhq.org/download/) and launch it:

    ```
    java -jar ~/selenium-server-standalone-x.xx.x.jar
    ```

    In case of using Selenium Server 3.0 with Firefox browser since v48 or Google Chrome since v53 you must download [GeckoDriver](https://github.com/mozilla/geckodriver/releases) or [ChromeDriver](https://sites.google.com/a/chromium.org/chromedriver/downloads) and launch Selenium with it:

    ```
    # for Firefox
    java -jar -Dwebdriver.gecko.driver=~/geckodriver ~/selenium-server-standalone-3.xx.x.jar
    
    # for Google Chrome
    java -jar -Dwebdriver.chrome.driver=~/chromedriver ~/selenium-server-standalone-3.xx.x.jar
    ``` 
    
    As an alternative way you can use already configured Docker container with older versions of Selenium and Firefox:
    
    ```
    docker run --net=host selenium/standalone-firefox:2.53.0
    ```

5. (Optional) Create `yii2_basic_tests` database and update it by applying migrations if you have them.

   ```
   tests/bin/yii migrate
   ```

   The database configuration can be found at `config/test_db.php`.


6. Start web server:

    ```
    tests/bin/yii serve
    ```

7. Now you can run all available tests

   ```
   # run all available tests
   vendor/bin/codecept run

   # run acceptance tests
   vendor/bin/codecept run acceptance

   # run only unit and functional tests
   vendor/bin/codecept run unit,functional
   ```

### Code coverage support

By default, code coverage is disabled in `codeception.yml` configuration file, you should uncomment needed rows to be able
to collect code coverage. You can run your tests and collect coverage with the following command:

```
#collect coverage for all tests
vendor/bin/codecept run -- --coverage-html --coverage-xml

#collect coverage only for unit tests
vendor/bin/codecept run unit -- --coverage-html --coverage-xml

#collect coverage for unit and functional tests
vendor/bin/codecept run functional,unit -- --coverage-html --coverage-xml
```

You can see code coverage output under the `tests/_output` directory.
