## Практическая работа. Написание скриптов на Python.

Пришло время попрактикковаться в прекрасном: написании скриптов на Python. 

Разберём реальный сценарий: у вас есть огромная "портянка" лога web-сервера, к которомуидёт 100500 обращений в минуту или около того. Вам постуил запрос от команды разработки, с просьбой предоставить статистику обращений к этому сервису.

Записи лог-файла имеют вид:

```

128.148.46.126 - - [20/Jun/2024:12:56:06 +0300] "GET /forecast-system%20engine_high-level.css HTTP/1.1" 200 1359 "-" "Mozilla/5.0 (Windows NT 5.0; en-US; rv:1.9.2.20) Gecko/1990-13-08 Firefox/37.0"
52.56.245.28 - - [20/Jun/2024:12:56:06 +0300] "GET /archive/optimizing_zero%20defect.jpg HTTP/1.1" 200 2551 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/5321 (KHTML, like Gecko) Chrome/40.0.848.0 Mobile Safari/5321"
122.100.81.4 - - [20/Jun/2024:12:56:06 +0300] "POST /internet%20solution-Monitored%20Graphical%20User%20Interface/client-driven.png HTTP/1.1" 400 88 "-" "Mozilla/5.0 (Macintosh; PPC Mac OS X 10_9_10 rv:6.0) Gecko/1957-01-07 Firefox/37.0"
236.162.72.4 - - [20/Jun/2024:12:56:06 +0300] "GET /Managed-motivating-migration.js HTTP/1.1" 200 1253 "-" "Mozilla/5.0 (Windows NT 6.2) AppleWebKit/5361 (KHTML, like Gecko) Chrome/39.0.874.0 Mobile Safari/5361"
222.71.149.234 - - [20/Jun/2024:12:56:06 +0300] "GET /Ameliorated/multi-state-Fully-configurable.svg HTTP/1.1" 200 1848 "-" "Mozilla/5.0 (Windows CE) AppleWebKit/5362 (KHTML, like Gecko) Chrome/39.0.860.0 Mobile Safari/5362"
153.172.20.53 - - [20/Jun/2024:12:56:06 +0300] "GET /object-oriented.hmtl HTTP/1.1" 200 2511 "-" "Mozilla/5.0 (X11; Linux i686; rv:6.0) Gecko/1902-21-08 Firefox/36.0"
218.233.62.252 - - [20/Jun/2024:12:56:06 +0300] "GET /exuding/Re-contextualized.gif HTTP/1.1" 200 1399 "-" "Mozilla/5.0 (Macintosh; U; PPC Mac OS X 10_9_4 rv:5.0) Gecko/1983-23-03 Firefox/36.0"
210.109.213.232 - - [20/Jun/2024:12:56:06 +0300] "GET /intermediate.gif HTTP/1.1" 400 39 "-" "Mozilla/5.0 (Macintosh; PPC Mac OS X 10_9_0) AppleWebKit/5352 (KHTML, like Gecko) Chrome/36.0.872.0 Mobile Safari/5352"
4.53.191.140 - - [20/Jun/2024:12:56:06 +0300] "DELETE /encompassing/Assimilated.htm HTTP/1.1" 200 2970 "-" "Opera/9.55 (Macintosh; U; PPC Mac OS X 10_9_2; en-US) Presto/2.9.189 Version/12.00"
4.146.11.59 - - [20/Jun/2024:12:56:06 +0300] "POST /installation.png HTTP/1.1" 200 2963 "-" "Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10_7_6) AppleWebKit/5322 (KHTML, like Gecko) Chrome/37.0.893.0 Mobile Safari/5322"
249.33.184.57 - - [20/Jun/2024:12:56:06 +0300] "GET /project.js HTTP/1.1" 200 1733 "-" "Opera/8.46 (Macintosh; U; Intel Mac OS X 10_5_1; en-US) Presto/2.10.282 Version/13.00"
149.51.195.206 - - [20/Jun/2024:12:56:06 +0300] "GET /conglomeration%20disintermediate-access.svg HTTP/1.1" 200 1444 "-" "Opera/10.44 (Windows NT 6.2; en-US) Presto/2.10.200 Version/11.00"
205.166.109.119 - - [20/Jun/2024:12:56:06 +0300] "GET /encoding%20bi-directional-24/7.jpg HTTP/1.1" 200 897 "-" "Opera/10.68 (X11; Linux x86_64; en-US) Presto/2.11.317 Version/13.00"
163.37.228.9 - - [20/Jun/2024:12:56:06 +0300] "DELETE /Multi-lateral%20intangible-Centralized.css HTTP/1.1" 200 2653 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1) AppleWebKit/536.16.1 (KHTML, like Gecko) Version/4.0 Safari/536.16.1"

```

Вам необходима с помощью Python-скрипта обработать лог файл и предоставить статистику в отдельном TXT-файле, которая будет содержать IP-адрес и количество обращений.

Например:

```
188.41.16.190: 1

```

Понимаем, что кому то из вас это покажется оскорбительно простым, поэтму давайте сделаем задание со звёздочкой, для тех "кто не прочь поразмять немного кости", дополним статистику ещё и операционной системой.

Например:

```
188.41.16.190: Macintosh: 1

```
Понимаю, что вам нетерпится приступить. В приложении вы найдёте архив: nginx.log.tar.gz. Скопируйте его на свои ВМ и разархивируйте. Например, с помощью команды: ```tar -xvzf nginx.log.tar.gz```. После распаковки вы получите гигабайт отборнейших логов, с которыми вам и предстоит порабтать.

На проверку необходимо сдать TXT-файл, в котором собрана статистика: IP-адрес: количество обращений или IP-адрес: ОС: количество обращений.
И текст Python -скрипта, который эту статистику собрал. Проверяющий будет "обрабатывать" с помощью вашего скрипта произвольный кусок лога из вложенного архива, если скрипт выдаст результат отвечающий критериям: IP-адрес: количество обращений или IP-адрес: ОС: количество обращений, то практическое задание считается выполненным. Удачи!
