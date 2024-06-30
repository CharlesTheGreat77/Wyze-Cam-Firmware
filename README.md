# Wyze-Cam-Firmware
Wyze Cam Pan Firmware sniffed from OTA for Reverse Engineering
![WyzeCamPan](https://github.com/CharlesTheGreat77/Wyze-Cam-Firmware/assets/27988707/322ffb1d-f218-48ee-9762-c9fe77255e2a)


<details>
  <summary>HTTP Requests Inspection</summary>
  ## Get device info
  
  ```
  POST /app/v2/device/get_device_Info HTTP/2
  Host: api.wyzecam.com
  Accept: */*
  Content-Type: application/json
  Content-Length: 1270
  Appinfo: wyze_ios_2.50.7.10
  Env: prod
  User-Agent: wyze_ios/2.50.7 (10) (iPhone 14; iOS 17.2; Scale/3.0; Height/2532.0; Width/1170.0) // scale, height, and width in user-agent 🤔 interesting way of gettings things done
  Accept-Language: en-US
  Accept-Encoding: gzip, deflate, br
  Appversion: 2.50.7.10
  {
    "device_mac":"",
    "app_version":"2.50.7.10",
    "app_ver":"com.hualai.WyzeCam___2.50.7.10",
    "phone_system_type":"1",
    "ts":1719731406281,
    "sc":"9f275790cab94a72bd206c8876429f3c",
    "phone_id":"2FD276BF-4EBC-4FE5-BD31-3477726E7229",
    "sv":"c86fa16fc99d4d6580f82ef3b942e586",
    "device_model":"WYZECP1_JEF",
    "access_token":"",
    "app_name":"com.hualai.WyzeCam"
  }
  ```

  ## Data Plan request decoded
  ```
  POST /v1/batch HTTP/2
  Host: wyze.dataplane.rudderstack.com
  Accept: */*
  Content-Type: application/json
  Anonymousid: <base64>
  Content-Length: 614
  Accept-Encoding: gzip, deflate, br
  Content-Encoding: gzip
  User-Agent: Wyze/10 CFNetwork/1490.0.4 Darwin/23.2.0
  Accept-Language: en-US,en;q=0.9
  Authorization: Basic <base64>
  
  {
  "sentAt": "2024-06-30T07:10:10.693Z",
  "batch": [
    {
      "messageId": "aef58133-5c85-4f19-ace5-b115cf2a7ad7",
      "anonymousId": "",
      "userId": "",
      "channel": "mobile",
      "event": "App Product Screen Viewed RS",
      "context": {
        "screen": {
          "density": 3,
          "width": 390,
          "height": 844
        },
        "os": {
          "name": "iOS",
          "version": "17.2"
        },
        "locale": "en-US",
        "app": {
          "version": "2.50.7",
          "namespace": "com.hualai.WyzeCam",
          "name": "Wyze",
          "build": "10"
        },
        "device": {
          "id": "2fd276bf-4ebc-4fe5-bd31-3477726e7229",
          "manufacturer": "Apple",
          "model": "iPhone14,7",
          "name": "iPhone",
          "type": "iOS",
          "attTrackingStatus": 0
        },
        "traits": {
          "anonymousId": "",
          "email": "",
          "userId": ""
        },
        "library": {
          "name": "rudder-ios-library",
          "version": "1.26.3"
        },
        "timezone": "America/Los_Angeles",
        "network": {
          "cellular": false,
          "wifi": true
        }
      },
      "originalTimestamp": "2024-06-30T07:10:09.915Z",
      "properties": {
        "device_models": "WYZECP1_JEF"
      },
      "type": "track",
      "integrations": {
        "All": true
      },
      "sentAt": "2024-06-30T07:10:10.693Z"
      }
    ]
  }
  ```
  ## API Data?? TBD
  ```
  POST /api/v3/data HTTP/2
  Host: sdk.iad-03.braze.com
  Content-Type: application/json
  X-Braze-Req-Attempt: 1
  Accept: */*
  X-Braze-Datarequest: true
  X-Braze-Feedrequest: true
  X-Braze-Triggersrequest: true
  Accept-Language: en-US,en;q=0.9
  Accept-Encoding: gzip, deflate, br
  Content-Length: 645
  X-Braze-Last-Req-Ms-Ago: 159988
  User-Agent: Wyze/10 CFNetwork/1490.0.4 Darwin/23.2.0
  X-Braze-Api-Key: 
  
  {
    "api_key": "",
    "app_version": "2.50.7",
    "app_version_code": "2.50.7.0",
    "device_id": "9192383D-4C6E-454E-B486-72872414E7B3",
    "events": [
      {
        "data": {
          "d": 158
        },
        "name": "se",
        "session_id": "",
        "time": 1719731493.32,
        "user_id": ""
      },
      {
        "name": "ss",
        "session_id": "",
        "time": 1719731493.322,
        "user_id": ""
      }
    ],
    "respond_with": {
      "config": {
        "config_time": 1719721308
      },
      "feed": true,
      "triggers": true,
      "user_id": ""
    },
    "sdk_metadata": [
      "manu"
    ],
    "sdk_version": "7.5.0",
    "time": 1719731493.3283901
  }
  ```

  ## credit card sync
  ```
  POST /api/v3/content_cards/sync HTTP/2
  Host: sdk.iad-03.braze.com
  Content-Type: application/json
  X-Braze-Req-Attempt: 1
  Accept: */*
  X-Braze-Datarequest: true
  Braze-Sync-Retry-Count: 0
  Accept-Language: en-US,en;q=0.9
  Accept-Encoding: gzip, deflate, br
  Content-Length: 293
  X-Braze-Last-Req-Ms-Ago: 159987
  User-Agent: Wyze/10 CFNetwork/1490.0.4 Darwin/23.2.0
  X-Braze-Contentcardsrequest: true
  X-Braze-Api-Key: 
  
  {
    "api_key": "",
    "app_version": "2.50.7",
    "app_version_code": "2.50.7.0",
    "device_id": "",
    "last_card_updated_at": 0,
    "last_full_sync_at": 0,
    "sdk_version": "7.5.0",
    "time": 1719731493.328456,
    "user_id": ""
  }
  ```
  ## Device property list
  
  ```
  POST /app/v2/device/get_property_list HTTP/2
  Host: api.wyzecam.com
  Accept: */*
  Content-Type: application/json
  Content-Length: 1343
  Appinfo: wyze_ios_2.50.7.10
  Env: prod
  User-Agent: wyze_ios/2.50.7 (10) (iPhone 14; iOS 17.2; Scale/3.0; Height/2532.0; Width/1170.0)
  Accept-Language: en-US
  Accept-Encoding: gzip, deflate, br
  Appversion: 2.50.7.10
  
  {
  "phone_id": "2FD276BF-4EBC-4FE5-BD31-3477726E7229",
  "access_token": "",
  "target_pid_list": [
    "P1",
    "P1047",
    "P1048",
    "P1018",
    "P1019",
    "P1022",
    "P1020"
  ],
  "app_name": "com.hualai.WyzeCam",
  "app_version": "2.50.7.10",
  "sc": "9f275790cab94a72bd206c8876429f3c",
  "sv": "f6d62611aab94638af312546a510aae3",
  "device_mac": "",
  "app_ver": "com.hualai.WyzeCam___2.50.7.10",
  "phone_system_type": "1",
  "ts": 1719731516356,
  "device_model": "WYZECP1_JEF"
  }
  ```
  ## device actions/functions 🎯
  ```
  GET /wyzeapp/cre/rule-template/collection?nonce=1719731581127&policyAttribute=&scope=APP HTTP/2
  Host: wyze-re-rule-svc.wyzecam.com
  Content-Type: application/json
  Appid: 9319141212m2ik
  Appinfo: wyze_ios_2.50.7.10
  Accept: */*
  Appversion: 2.50.7.10
  Requestid: 
  Isnewdelayarguments: 1
  Accept-Language: en-US
  Accept-Encoding: gzip, deflate, br
  User-Agent: wyze_ios/2.50.7 (10) (iPhone 14; iOS 17.2; Scale/3.0; Height/2532.0; Width/1170.0)
  Signature2: 
  Env: prod
  Phoneid: 2FD276BF-4EBC-4FE5-BD31-3477726E7229
  Access_token:
  ```

  - Don't know how to actually call these things though (response is huge)

  ## Rule Search ?? might be able to add something to the json request 🤷‍♂️
  ```
  POST /wyzeapp/cre/rules/search HTTP/2
  Host: wyze-re-rule-svc.wyzecam.com
  Content-Type: application/json
  Appid: 9319141212m2ik
  Appinfo: wyze_ios_2.50.7.10
  Accept: */*
  Appversion: 2.50.7.10
  Requestid: 2058c580fa1de1f29bbe87a4f5cdd965
  Isnewdelayarguments: 1
  Accept-Language: en-US
  Accept-Encoding: gzip, deflate, br
  Content-Length: 86
  User-Agent: wyze_ios/2.50.7 (10) (iPhone 14; iOS 17.2; Scale/3.0; Height/2532.0; Width/1170.0)
  Signature2: be021808f83d6406e0393e6e88da4c54
  Env: prod
  Phoneid: 2FD276BF-4EBC-4FE5-BD31-3477726E7229
  Access_token:

  {"nonce":"1719731581127",
    "deviceId":"","type":"",
    "secondScopes":[
      ""
    ],
    "scopes":[
      "APP"
    ]
  }
  ```

  ## Get events (in jpg format).. can't find vids!
  ```
  POST /app/v2/device/get_event_page_list HTTP/1.1
  Host: service-event.wyze.com
  Content-Type: application/json
  Appinfo: wyze_ios_2.50.7.10
  Accept: */*
  Appversion: 2.50.7.10
  Accept-Encoding: gzip, deflate, br
  Accept-Language: en-US
  Content-Length: 1480
  User-Agent: wyze_ios/2.50.7 (10) (iPhone 14; iOS 17.2; Scale/3.0; Height/2532.0; Width/1170.0)
  Env: prod
  Connection: keep-alive
  
  {
    "access_token": "",
    "event_type": "",
    "order_by": 2,
    "count": 100,
    "app_version": "2.50.7.10",
    "app_name": "com.hualai.WyzeCam",
    "event_value_list": [
      "1",
      "3",
      "6",
      "7",
      "12",
      "13",
      "2",
      "5",
      "4",
      "10"
    ],
    "sc": "9f275790cab94a72bd206c8876429f3c",
    "device_mac_list": [
      ""
    ],
    "event_tag_list": [
      "101",
      "102",
      "103",
      "104"
    ],
    "page_token": "",
    "sv": "bdcb412e230049c0be0916e75022d3f3",
    "end_time": 1719731583957,
    "device_mac": "",
    "phone_system_type": "1",
    "app_ver": "com.hualai.WyzeCam___2.50.7.10",
    "ts": 1719731583959,
    "begin_time": 1719648000000
  }
  ```
  ## Event insight
  ```
  GET /v1/event-insight/device-stats/count?devicemac_list=&nonce=1719732254368 HTTP/1.1
  Host: ai-event-insight-api-v2.wyzecam.com
  Appid: 9319141212m2ik
  Content-Type: application/json
  Appinfo: wyze_ios_2.50.7.10
  Clientver: 2
  Phone_id: 2FD276BF-4EBC-4FE5-BD31-3477726E7229
  Timestamp: 1719732254369
  Accept: */*
  Appversion: 2.50.7.10
  Requestid: 
  Accept-Language: en-US
  Accept-Encoding: gzip, deflate, br
  Access-Token: 
  User-Agent: Wyze/10 CFNetwork/1490.0.4 Darwin/23.2.0
  Signature2: 
  Env: prod
  Connection: keep-alive
  ```
   - specify mac address of device in url

  ## Query Shop
  
  ```
  POST /api/2024-01/graphql HTTP/2
  Host: wyzecom.myshopify.com
  Content-Type: application/json
  Accept: application/json
  Sec-Fetch-Site: cross-site
  X-Sdk-Variant: javascript
  Accept-Language: *
  X-Shopify-Storefront-Access-Token: 
  Sec-Fetch-Mode: cors
  Accept-Encoding: gzip, deflate, br
  Origin: https://app-shop-prod.wyze.com
  User-Agent: Mozilla/5.0 (iPhone; CPU iPhone OS 17_2 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Mobile/15E148
  Referer: https://app-shop-prod.wyze.com/
  X-Sdk-Version: 2.22.0
  Content-Length: 1875
  Sec-Fetch-Dest: empty
  
  {"query":"query ($handle:String!,$productsFirst:Int!,$productSortKey:ProductCollectionSortKeys!,$productsReverse:Boolean!)  { collection (handle: $handle) { id,handle,description,descriptionHtml,updatedAt,title,metafields (identifiers: [{namespace: \"global\" key: \"title_tag\"} {namespace: \"appshop\" key: \"time_limit\"} {namespace: \"appshop\" key: \"count_down\"}]) { id,key,type,value,namespace },image { id,src: originalSrc,altText },... on Collection { id,products (first: $productsFirst sortKey: $productSortKey reverse: $productsReverse) { pageInfo { hasNextPage,hasPreviousPage },edges { cursor,node { id,tags,availableForSale,createdAt,updatedAt,descriptionHtml,description,handle,productType,title,vendor,publishedAt,priceRange { maxVariantPrice { amount,currencyCode },minVariantPrice { amount,currencyCode } },compareAtPriceRange { maxVariantPrice { amount,currencyCode },minVariantPrice { amount,currencyCode } },collections (first: 30) { pageInfo { hasNextPage,hasPreviousPage },edges { cursor,node { id,handle } } },metafields (identifiers: [{namespace: \"appshop\" key: \"highlight_image\"} {namespace: \"merchandising\" key: \"subtitle\"}]) { id,key,value,namespace },images (first: 250) { pageInfo { hasNextPage,hasPreviousPage },edges { cursor,node { id,src,altText,width,height } } },variants (first: 30) { pageInfo { hasNextPage,hasPreviousPage },edges { cursor,node { id,title,price { amount,currencyCode },available: availableForSale,sku,quantityAvailable,compareAtPrice { amount,currencyCode },image { id,src: originalSrc,altText,width,height },metafields (identifiers: [{namespace: \"accentuate\" key: \"unavailable_for_sale\"} {namespace: \"merchandising\" key: \"hide\"}]) { id,key,value,namespace } } } } } } } } } }","variables":{"handle":"app-smart-cameras","productsFirst":250,"productSortKey":"COLLECTION_DEFAULT","productsReverse":false}}
  ```

  # identity?? TBD
  ```
  POST /v1/identify HTTP/2
  Host: wyze.dataplane.rudderstack.com
  Content-Type: application/json
  Anonymousid: 
  Accept: */*
  Authorization: Basic 
  Sec-Fetch-Site: cross-site
  Accept-Language: en-US,en;q=0.9
  Accept-Encoding: gzip, deflate, br
  Sec-Fetch-Mode: cors
  Origin: https://app-shop-prod.wyze.com
  Content-Length: 1766
  User-Agent: Mozilla/5.0 (iPhone; CPU iPhone OS 17_2 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Mobile/15E148
  Referer: https://app-shop-prod.wyze.com/
  Sec-Fetch-Dest: empty
  
  {"channel":"web","context":{"app":{"name":"RudderLabs JavaScript SDK","namespace":"com.rudderlabs.javascript","version":"2.48.9"},"traits":{"is_membership":false,"nickname":""},"library":{"name":"RudderLabs JavaScript SDK","version":"2.48.9"},"userAgent":"Mozilla/5.0 (iPhone; CPU iPhone OS 17_2 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Mobile/15E148","os":{"name":"","version":""},"locale":"en-US","screen":{"density":3,"width":390,"height":844,"innerWidth":390,"innerHeight":753},"timezone":"GMT-0700","sessionId":1719732156816,"sessionStart":true,"campaign":{},"page":{"path":"/product-list-by-category.html","referrer":"$direct","referring_domain":"","search":"?category=1&&appinfo=wyze_ios_2.50.7&user_id=&nickname=&env=prod&ismember=0&phoneid=2FD276BF-4EBC-4FE5-BD31-3477726E7229&isShowButton=1","title":"App shop","url":"https://app-shop-prod.wyze.com/product-list-by-category.html?category=1&&appinfo=wyze_ios_2.50.7&user_id=&nickname=&env=prod&ismember=0&phoneid=2FD276BF-4EBC-4FE5-BD31-3477726E7229&isShowButton=1","tab_url":"https://app-shop-prod.wyze.com/product-list-by-category.html?category=1&&appinfo=wyze_ios_2.50.7&user_id=&nickname=&env=prod&ismember=0&phoneid=2FD276BF-4EBC-4FE5-BD31-3477726E7229&isShowButton=1","initial_referrer":"$direct","initial_referring_domain":""}},"type":"identify","messageId":"46213000-99e7-474e-8558-edb9e29e78c7","originalTimestamp":"2024-06-30T07:22:37.212Z","anonymousId":"","userId":"","integrations":{"All":true},"sentAt":"2024-06-30T07:22:37.217Z"}
  ```
  ## Account info
  ```
  GET /get_user_account_info?nonce=1719732253806 HTTP/2
  Host: wyze-membership-service-v2.wyzecam.com
  Phone_id: 2FD276BF-4EBC-4FE5-BD31-3477726E7229
  Content-Type: application/json
  Appid: 9319141212m2ik
  Clientver: 2
  Appinfo: wyze_ios_2.50.7.10
  Accept: */*
  Appversion: 2.50.7.10
  Requestid: 
  Accept-Language: en-US
  Accept-Encoding: gzip, deflate, br
  User-Agent: Wyze/10 CFNetwork/1490.0.4 Darwin/23.2.0
  Signature2: 
  Env: prod
  Access_token: 
  ```
