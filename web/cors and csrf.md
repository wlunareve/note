# CORS and CSRF

## CORS 跨來源資源共用

為了讓跨站得以實現，不是防賊
但又為了怕被 call 爆，所以要限制指定的 host

瀏覽器本身自動會去分簡單請求跟預檢請求 <br>
簡單請求可以直接跨網域　<br>
預檢請求沒辦法跨網域 <br>主要就是會看後端傳來的 Access-Control-Allow-Origin，來判斷是否可以發出請求 

```
Access-Control-Allow-Origin: http://remotehost.com

後端寫上 api 所允許的 method
Access-Control-Allow-Methods: GET, POST, PUT

前端有特殊 header 時，後端必須加
Access-Control-Allow-Headers: X-Custom-Header 
```


## CSRF 跨站請求偽造

是為了防止你登入A網站時 跑到惡意網站B，利用你的身分去對A網站做出請求 <br>
我們做為A網站，以 django 的做法是，登入A網站時給 csrftoken ， 在A網站底下操作所提出的請求，都會夾帶這個 csrftoken，
後端由此判斷這是正常使用 A 網站所提出的請求，而不是惡意網站冒用的