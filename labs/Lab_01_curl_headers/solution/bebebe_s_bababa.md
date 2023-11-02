# Лабораторная работа 1

Скрипт: `curl <ссылка> -I -k -L -v`

`-I` - флаг, который позволяет отобразить только заголовки без тела ответа  
`-L` - флаг который позволяет автоматически следовать перенаправлениям  
`-v` - флаг, который позволяет увидеть как заголовки запроса так и заголовки ответа   
`-k` - флаг, который позволяет использовать небезопасное соединение  

__из инструкции к curl:__
```
-I, --head               Show document info only  
-L, --location           Follow redirects  
-v, --verbose            Make the operation more talkative
-k, --insecure           Allow insecure server connections
```
---

### __[‍🎓 РГУПС](https://www.rgups.ru)__

```
*   Trying 80.72.224.90:80...
* Connected to rgups.ru (80.72.224.90) port 80 (#0)
> HEAD / HTTP/1.1
> Host: rgups.ru                         //"Заголовок Host содержит имя домена, для которого предназначен запрос и, опционально, номер порта."
> User-Agent: curl/8.0.1                 //"агент" с которого отправлен запрос (типа браузер)
> Accept: */*                            //тип принимаемого контента
>
< HTTP/1.1 301 Moved Permanently        //используемый протокол и код ответа                 
HTTP/1.1 301 Moved Permanently                                                               
< Server: nginx/1.19.1                  //"Заголовок сервера описывает программное обеспечение, используемое исходным сервером, который обработал запрос, то есть сервером, сгенерировавшим ответ."
< Date: Sun, 29 Oct 2023 00:45:58 GMT   //Время запроса (pog)
< Content-Type: text/html               //Тип контента (pog)
< Content-Length: 169                   //"Заголовок Content-Length указывает размер отправленного получателю тела объекта в байтах."
< Connection: keep-alive                //"Заголовок Connection определяет, остаётся ли сетевое соединение активным после завершения текущей транзакции (запроса). Если в запросе отправлено значение keep-alive, то соединение остаётся и не завершается, позволяя выполнять последующие запросы на тот же сервер."  
< Location: https://rgups.ru/           //очевидно, адрес сайта 

<
* Connection #0 to host rgups.ru left intact
* Clear auth, redirects to port from 80 to 443
* Issue another request to this URL: 'https://rgups.ru/'        //вторая попытка т.к. сайт переехал
*   Trying 80.72.224.90:443...
* Connected to rgups.ru (80.72.224.90) port 443 (#1)        
* schannel: disabled automatic use of client certificate
* ALPN: offers http/1.1
* ALPN: server accepted http/1.1
* using HTTP/1.1
> HEAD / HTTP/1.1
> Host: rgups.ru
> User-Agent: curl/8.0.1
> Accept: */*
>
< HTTP/1.1 200 OK
< Server: nginx/1.19.1
< Date: Sun, 29 Oct 2023 00:45:58 GMT
< Content-Type: text/html; charset=utf-8
< Connection: keep-alive
< X-Powered-By: ProcessWire CMS                                                             //"заголовок сообщает о технологиях, используемых на стороне сервера"
< Set-Cookie: wire=4af0045b6c0754b57e3c3d221fc8db4d; path=/; HttpOnly; SameSite=Lax         //"HTTP заголовок Set-Cookie используется для отправки cookies с сервера на агент пользователя/"           
< Expires: Thu, 19 Nov 1981 08:52:00 GMT          ?????                                     //"Заголовок Expires содержит дату/время, по истечении которой ответ сервера считается устаревшим."
< Cache-Control: no-store, no-cache, must-revalidate                                        //"Общий заголовок Cache-Control используется для задания инструкций кеширования как для запросов, так и для ответов. Инструкции кеширования однонаправленные: заданная инструкция в запросе не подразумевает, что такая же инструкция будет указана в ответе"
< Pragma: no-cache                                                                          //"Общий заголовок Pragma HTTP / 1.0 - это заголовок, зависящий от реализации, который может иметь различные эффекты в цепочке запрос-ответ. Он используется для обратной совместимости с кешами HTTP / 1.0, где заголовок Cache-Control HTTP / 1.1 ещё не присутствует."
```

>если использовать разные имена хостов, то нам ответят что сайт переехал на бебебе_с_бабаба. Поэтому используем флаг -L чтобы нас автоматически перенаправляло куда надо. Но, чтобы сократить код ответа (и сэкономить свое время и время преподавтеля), я буду обращаться сразу к правильному домену

### __[Github](https://github.com/)__

```
> HEAD / HTTP/1.1
> Host: hithub.com
> User-Agent: curl/8.0.1
> Accept: */*
>
< HTTP/1.1 200 OK
HTTP/1.1 200 OK
< Date: Sun, 29 Oct 2023 12:22:11 GMT
< Content-Type: text/html; charset=windows-1251
< Connection: keep-alive
< Last-Modified: Sun, 27 Aug 2006 20:00:00 GMT              //"Заголовок Last-Modified в ответе HTTP содержит дату и время, в которую, по мнению удалённого сервера, запрашиваемый ресурс был изменён"
< Cache-Control: max-age=0, private, proxy-revalidate
< Expires: Sun, 27 Aug 2006 20:10:00 GMT
< CF-Cache-Status: DYNAMIC                                  //"устанавливается Cloudflare CDN, указывает статус запроса к кэшу."
< Report-To: {"endpoints":[{"url":"https:\/\/a.nel.cloudflare.com\/report\/v3?s=p6Q3sqBaA5n3%2F%2BuAOBJGZGRR8O%2FGtBTkeog5KtBo4t9ah4VlwwADSUU%2BJOe7t6m00Uzl0NxzY2FI26RGhVrXygpC0l8aDtuB0b%2FOMJdUfS3Qsy57mW%2FJcT%2Fz3VVc"}],"group":"cf-nel","max_age":604800}
< NEL: {"success_fraction":0,"report_to":"cf-nel","max_age":604800}      //Заголовок ответа HTTP NEL используется для настройки ведения журнала сетевых запросов.
< Server: cloudflare
< CF-RAY: 81db61f2b8ab3491-WAW                              //"Это UID, который может использоваться оператором веб-сайта (и службой поддержки Cloudflare) для потенциальной отладки проблем."
< alt-svc: h3=":443"; ma=86400                              //"HTTP-заголовок Alt-Svc позволяет серверу указывать, что другое сетевое местоположение ("альтернативная служба") может рассматриваться как авторитетное для этого источника при выполнении будущих запросов."
```

### __[🚝 РЖД](https://www.rzd.ru/)__

>Чтобы этот "интересный" хост не заблокировал нам доступ надо его обмануть:
`curl https://www.rzd.ru -I -k -L -v --User-agent "Yandex"`

```
> HEAD / HTTP/1.1
> Host: www.rzd.ru
> User-Agent: Yandex
> Accept: */*
>
< HTTP/1.1 200
HTTP/1.1 200
< Content-Type: text/html;charset=utf-8
< Content-Length: 206338
< Connection: keep-alive
< Date: Sun, 29 Oct 2023 12:52:12 GMT
< Vary: Accept-Encoding                                 //"Заголовок ответа Vary определяет, как сопоставить будущие заголовки запроса, чтобы решить, можно ли использовать кешированный ответ, а не запрашивать новый с исходного сервера."
< X-UCM-Pod-Name: inex-ucm-bc445bf7f-d854g              //какая-то фигня которую используют всего 7 доменов в мире
< Strict-Transport-Security: max-age=15724800; includeSubDomains        //"заголовок ответа, позволяющий web-сайтам уведомить браузер о том, что доступ к ним должен быть осуществлён только посредством HTTPS вместо HTTP."
< Via: nginx2                                           //"Заголовок Via добавляется прокси-серверами, как прямыми, так и обратными, и может отображаться в заголовках запроса или ответа." 
< X-Frame-Options: sameorigin                           //"позволяет снизить уязвимость вашего сайта для кликджекинг - атак. Этот заголовок служит инструкцией для браузера не загружать вашу страницу в frame/iframe"
< Set-Cookie: session-cookie=179295162b3f217857f4932e18991a24469829f4efeaef1d910f8b54a339f56020795966f92513ae43d512bce4604840; Max-Age=86400; Path=/; secure
< X-XSS-Protection: 1; mode=block                       //"это особенность Internet Explorer, Chrome и Safari, которая останавливает загрузку страниц при обнаружении XSS атаки."
```

### __[🕸 Яндекс](https://yandex.ru/)__

```
> HEAD /?yredirect=true HTTP/1.1
> Host: dzen.ru
> User-Agent: curl/8.0.1
> Accept: */*
>
* schannel: failed to decrypt data, need more data
< HTTP/1.1 200 Ok
< Cache-Control: no-cache, no-store, max-age=0, must-revalidate
< Content-Security-Policy: frame-ancestors sq2.go.mail.ru metrika.yandex.ru webvisor.com; report-uri https://csp.yandex.net/csp?from=zen_old&project=zen&yandex_login=&yandexuid=1475247101698585024&requestid=3798293929.228.1698585024113.67442&page=site_desktop;
            //"позволяет администраторам веб-сайта управлять ресурсами, которые пользовательскому агенту разрешено загружать для данной страницы."
< Content-Security-Policy-Report-Only: default-src 'none'; connect-src 'self' an.yandex.ru strm.yandex.ru *.strm.yandex.net mc.yandex.ru yandex.st yastatic.net matchid.adfox.yandex.ru adfox.yandex.ru ads.adfox.ru ads6.adfox.ru jstracer.yandex.ru yastat.net yandex.ru awaps.yandex.net awaps.yandex.ru verify.yandex.ru *.verify.yandex.ru favicon.yandex.net pixel.adsafeprotected.com tps.doubleverify.com ad.adriver.ru amc.yandex.ru *.tunneler-si.dzen.ru *.tun.si.dzen.ru http-check-headers.yandex.ru mc.yandex.az mc.yandex.by mc.yandex.co.il mc.yandex.com mc.yandex.com.am mc.yandex.com.ge mc.yandex.com.tr mc.yandex.ee mc.yandex.fr mc.yandex.kg mc.yandex.kz mc.yandex.lt mc.yandex.lv mc.yandex.md mc.yandex.tj mc.yandex.tm mc.yandex.ua mc.yandex.uz mc.admetrica.ru yandexmetrica.com yandexmetrica.com:29009 yandexmetrica.com:30102 forms-ext-api.yandex.ru strm.yandex.net *.strm.yandex.ru *.cdn.ngenix.net zen-rc3.yandex.ru frontend.vh.yandex.ru https://vh.test.yandex.ru/live/ wss://push.yandex.ru api.passport.yandex.ru api.passport-test.yandex.ru suggest-maps.yandex.ru/suggest-geo vk.ru static.dzeninfra.ru avatars.dzeninfra.ru cdn.dzen.ru video.dzen.ru log.dzen.ru playlog.dzen.ru cdn.dzeninfra.ru *.cdn.dzeninfra.ru *.extcdn.dzeninfra.ru *.hot-video.dzeninfra.ru cold-video.dzeninfra.ru *.cold-video.dzeninfra.ru s3.dzeninfra.ru *.s3.dzeninfra.ru *.ms.dzen.ru notify.dzen.ru clck.dzen.ru static-mon.yandex.net cloud-api.yandex.ru yandex.ru dzen.ru *.adlooxtracking.com *.adlooxtracking.ru *.adsafeprotected.com *.doubleverify.com *.moatads.com *.serving-sys.com *.serving-sys.ru *.mail.ru *.mradx.net *.imgsmail.ru *.criteo.com *.criteo.net *.mycdn.me *.vkuser.net; frame-src awaps.yandex.net yandexadexchange.net *.yandexadexchange.net yastatic.net *.yandex.ru banners.adfox.ru yastat.net yandex.ru storage.mds.yandex.net *.tunneler-si.dzen.ru *.tun.si.dzen.ru http-check-headers.yandex.ru blob: mc.yandex.ru mc.yandex.md zenadservices.net sso.passport.yandex.ru id.vk.com *.dzen.ru sso.dzen.ru static.dzeninfra.ru suggest.dzen.ru 'self' yandex.ru *.mail.ru *.mradx.net *.imgsmail.ru *.criteo.com *.criteo.net *.mycdn.me *.vkuser.net *.doubleverify.com *.doubleclick.net; img-src 'self' data: avatars-fast.yandex.net favicon.yandex.net an.yandex.ru banners.adfox.ru content.adfox.ru ads6.adfox.ru tns-counter.ru *.tns-counter.ru s3.mds.yandex.net ads.adfox.ru amc.yandex.ru mc.admetrica.ru wcm-ru.frontend.weborama.fr wcm.solution.weborama.fr ad.adriver.ru bs.serving-sys.com ad.doubleclick.net counter.yadro.ru gdeby.hit.gemius.pl mc.yandex.ru verify.yandex.ru *.verify.yandex.ru yastatic.net yastat.net avatars.mds.yandex.net yandex.ru px.moatads.com awaps.yandex.net awaps.yandex.ru gdero.hit.gemius.pl pixel.adlooxtracking.com tps.doubleverify.com impression.appsflyer.com rgi.io track.rutarget.ru ssl.hurra.com pixel.adsafeprotected.com storage.mds.yandex.net *.tunneler-si.dzen.ru *.tun.si.dzen.ru http-check-headers.yandex.ru mc.yandex.az mc.yandex.by mc.yandex.co.il mc.yandex.com mc.yandex.com.am mc.yandex.com.ge mc.yandex.com.tr mc.yandex.ee mc.yandex.fr mc.yandex.kg mc.yandex.kz mc.yandex.lt mc.yandex.lv mc.yandex.md mc.yandex.tj mc.yandex.tm mc.yandex.ua mc.yandex.uz mc.webvisor.org *.mediascope.mc.yandex.ru avatars.mdst.yandex.net zen.s3.yandex.net strm.yandex.ru strm.yandex.net sso.passport.yandex.ru dzen.ru avatars.dzeninfra.ru static.dzeninfra.ru cdn.dzen.ru video.dzen.ru log.dzen.ru playlog.dzen.ru s3.dzeninfra.ru *.ms.dzen.ru *.s3.dzeninfra.ru *.zen.yandex.com *.m-counter.ru www.m-counter.ru www.tns-counter.ru *.mail.ru *.mradx.net *.imgsmail.ru *.criteo.com *.criteo.net *.mycdn.me *.vkuser.net *.doubleverify.com *.adsafeprotected.com *.serving-sys.com *.serving-sys.ru *.weborama.fr *.weborama-tech.ru *.hit.gemius.pl consentmanager.mgr.consensu.org cdn.consentmanager.mgr.consensu.org *.adlooxtracking.com *.adlooxtracking.ru vk.com vk.ru *.userapi.com *.vk.com *.vk.ru; media-src *.yandex.net strm.yandex.ru *.strm.yandex.ru yandex.ru yandex.st yastatic.net banners.adfox.ru content.adfox.ru data: yastat.net *.mycdn.me *.vkuser.net *.tunneler-si.dzen.ru *.tun.si.dzen.ru http-check-headers.yandex.ru blob: *.strm.yandex.net *.cdn.ngenix.net cdn.dzen.ru video.dzen.ru *.cdn.dzeninfra.ru *.extcdn.dzeninfra.ru *.hot-video.dzeninfra.ru cold-video.dzeninfra.ru *.cold-video.dzeninfra.ru *.s3.dzeninfra.ru *.mail.ru *.mradx.net *.imgsmail.ru *.criteo.com *.criteo.net; script-src 'unsafe-inline' 'unsafe-eval' an.yandex.ru yandex.st yastatic.net mc.yandex.ru banners.adfox.ru ads.adfox.ru ads6.adfox.ru yastat.net yandex.ru z.moatads.com storage.mds.yandex.net *.tunneler-si.dzen.ru *.tun.si.dzen.ru http-check-headers.yandex.ru mc.yandex.az mc.yandex.by mc.yandex.co.il mc.yandex.com mc.yandex.com.am mc.yandex.com.ge mc.yandex.com.tr mc.yandex.ee mc.yandex.fr mc.yandex.kg mc.yandex.kz mc.yandex.lt mc.yandex.lv mc.yandex.md mc.yandex.tj mc.yandex.tm mc.yandex.ua mc.yandex.uz chat.s3.yandex.net sso.dzen.ru sso.passport.yandex.ru static.dzeninfra.ru 'self' *.zen.yandex.com dzen.ru *.mail.ru *.mradx.net *.imgsmail.ru *.criteo.com *.criteo.net *.mycdn.me *.vkuser.net *.adlooxtracking.com *.adlooxtracking.ru *.adsafeprotected.com *.doubleverify.com *.moatads.com *.dvtps.com *.doubleclick.net *.serving-sys.ru *.userapi.com vk.com vk.ru *.vk.com *.vk.ru; style-src 'unsafe-inline' 'unsafe-eval' yandex.st yastatic.net banners.adfox.ru content.adfox.ru yastat.net *.tunneler-si.dzen.ru *.tun.si.dzen.ru http-check-headers.yandex.ru yandex.ru static.dzeninfra.ru 'self' *.zen.yandex.com dzen.ru *.mail.ru *.mradx.net *.imgsmail.ru *.criteo.com *.criteo.net *.mycdn.me *.vkuser.net; font-src 'self' data: an.yandex.ru yastatic.net yastat.net *.tunneler-si.dzen.ru *.tun.si.dzen.ru http-check-headers.yandex.ru static.dzeninfra.ru *.mail.ru *.mradx.net *.imgsmail.ru *.criteo.com *.criteo.net *.mycdn.me *.vkuser.net fonts.gstatic.com; child-src blob: mc.yandex.ru; manifest-src *.dzen.ru/manifest.webmanifest 'self'; report-uri https://csp.yandex.net/csp?from=zen_old&project=zen&yandex_login=&yandexuid=1475247101698585024&requestid=3798293929.228.1698585024113.67442&page=site_desktop; 
                    //"позволяет веб-разработчикам экспериментировать с политиками, отслеживая (но не применяя) их эффекты."
                    //твой заголовок такой большой, сводный response))
< Content-Type: text/html; charset=utf-8
< Set-Cookie: _yasc=PFTC+lnqtALQ8uAiKILh5pyfq7kT3DQkxMKi3+BP/xTwQgRxSWD9JKIghFRcOz37; domain=.dzen.ru; path=/; expires=Wed, 26 Oct 2033 13:10:24 GMT; secure
< X-Content-Type-Options: nosniff   //"является маркером, используемым сервером для указания того, что типы MIME, объявленные в заголовках Content-Type, должны соблюдаться и не изменяться."
< X-Requestid: 3798293929.228.1698585024113.67442       //"Идея X-Request-ID заключается в том, что клиент может создать некоторый случайный идентификатор и передать его серверу. Затем сервер включает этот идентификатор в каждую созданную им инструкцию журнала. Если клиент получает сообщение об ошибке, он может включить идентификатор в отчет об ошибке, позволяя оператору сервера просматривать соответствующие записи журнала (без необходимости полагаться на временные метки, IP-адреса и т.д.)."
< X-XSS-Protection: 1; mode=block
< X-Yandex-Req-Id: 1698585024077385-923239515142792856800178-production-app-host-sas-zen-503
```

###  __[🐍 Python](https://www.python.org/)__

```
> HEAD / HTTP/1.1
> Host: www.python.org
> User-Agent: curl/8.0.1
> Accept: */*
>
< HTTP/1.1 200 OK
< Connection: keep-alive
< Content-Length: 50401
< Server: nginx
< Content-Type: text/html; charset=utf-8
< X-Frame-Options: SAMEORIGIN
< Via: 1.1 vegur, 1.1 varnish, 1.1 varnish
< Accept-Ranges: bytes                                  //"это маркер, который использует сервер, чтобы уведомить клиента о поддержке "запросов по кускам". Его значение указывает единицу измерения, которая может быть использована для определения диапазона чтения."
< Date: Sun, 29 Oct 2023 13:26:27 GMT
< Age: 445                                              //"содержит время в секундах, в течение которого объект находился в кэше прокси-сервера."
< X-Served-By: cache-iad-kiad7000025-IAD, cache-fra-eddf8230125-FRA  //"заголовок x-served-by указывает, из какой точки присутствия был получен запрос."
< X-Cache: HIT, HIT                                     //означает, что ваш запрос был обработан CDN, а не исходными серверами
< X-Cache-Hits: 1, 2                                    //"Список, указывающий количество обращений к кэшу в каждом узле."
< X-Timer: S1698585987.197253,VS0,VE0                   //"Информация о времени получения ответа."
< Vary: Cookie
< Strict-Transport-Security: max-age=63072000; includeSubDomains; preload
```
### __[Saint 🌠 GIT](https://git-scm.com/)__

```
> HEAD / HTTP/1.1
> Host: git-scm.com
> User-Agent: curl/8.0.1
> Accept: */*
>
< HTTP/1.1 200 OK
< Date: Sun, 29 Oct 2023 13:40:09 GMT
< Content-Type: text/html; charset=utf-8
< Connection: keep-alive
< X-Frame-Options: SAMEORIGIN
< X-Xss-Protection: 1; mode=block
< X-Content-Type-Options: nosniff
< X-Download-Options: noopen
< X-Permitted-Cross-Domain-Policies: none
< Referrer-Policy: strict-origin-when-cross-origin      //"определяет, какой объем информации о реферере (отправляемой с заголовком Referer) следует включать в запросы"
< Cache-Control: public, max-age=14400
< Etag: W/"db69273d9410cbf4536e9d4b3a59685d"            //"является идентификатором специфической версии ресурса. Он позволяет более эффективно использовать кеш и сохраняет пропускную способность, позволяя серверу отправлять не весь ответ, если содержимое не изменилось."
< X-Request-Id: 64c0ae81-7d55-4798-a03e-5a0924ffcccd
< X-Runtime: 0.022433
< Via: 1.1 vegur
< CF-Cache-Status: HIT
< Age: 4410
< Server: cloudflare
< CF-RAY: 81dbd426cdb31616-DME
```

### __[🐵 Jetbrains](https://www.jetbrains.com/)__

```
> HEAD / HTTP/1.1
> Host: www.jetbrains.com
> User-Agent: curl/8.0.1
> Accept: */*
>
< HTTP/1.1 200 OK
HTTP/1.1 200 OK
< Content-Type: text/html; charset=utf-8
< Content-Length: 47748
< Connection: keep-alive
< Date: Sun, 29 Oct 2023 13:42:03 GMT
< Server: nginx
< X-Content-Type-Options: nosniff
< Referrer-Policy: same-origin
< Expires: Sun, 29 Oct 2023 13:42:03 GMT
< Cache-Control: max-age=0
< Pragma: no-cache
< X-Frame-Options: DENY
< X-Content-Type-Options: nosniff
< X-Xss-Protection: 1; mode=block
< Strict-Transport-Security: max-age=31536000;
< Vary: Accept-Encoding
< Via: 1.1 36168127cb283f921c7d9cd48f72214e.cloudfront.net (CloudFront)
< Alt-Svc: h3=":443"; ma=86400
< Age: 185
< Set-Cookie: cf_country-region=RU-ROS; Domain=jetbrains.com; Path=/; Secure
< X-Cache: Hit from cloudfront
< X-Amz-Cf-Pop: HEL50-C1                                                         //"Вероятно, это внутренний идентификатор местоположения сервера, который обслуживал ваш трафик"
< X-Amz-Cf-Id: oOUgTQRdcnm5EYdCmPB0707Qc7Kkzp4s5QxBi94sF289R80FxeU5dA==          //"идентификатор запроса для внутреннего устранения неполадок"
```

### __[💪 VSC](https://code.visualstudio.com/)__

```
> HEAD / HTTP/1.1
> Host: code.visualstudio.com
> User-Agent: curl/8.0.1
> Accept: */*
>
< HTTP/1.1 200 OK
< Date: Sun, 29 Oct 2023 13:55:10 GMT
< Content-Type: text/html; charset=utf-8
< Content-Length: 50360
< Connection: keep-alive
< ETag: W/"c4b8-p3Wo+AI6xUxvmXlpADJZiRFtDXY"
< Strict-Transport-Security: max-age=31536000; includeSubDomains
< Content-Security-Policy: frame-ancestors 'self'
< X-Frame-Options: SAMEORIGIN
< X-XSS-Protection: 1; mode=block
< X-Content-Type-Options: nosniff
< X-Powered-By: ASP.NET
< x-azure-ref: 20231029T135510Z-qcm2qfuc051w7cadx65axrsg400000000m50000000006bs9
< X-Cache: CONFIG_NOCACHE
< Accept-Ranges: bytes

```



~~Ничего не понял, но очень инетерсно~~
