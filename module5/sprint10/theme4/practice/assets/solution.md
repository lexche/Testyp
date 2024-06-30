Ссылка на файл с логами:  https://sysadmin.education-services.ru/downloads/nginx.log.tar.gz
Весит около 184 Мб, Гит, естественно, не пропускает.

Простой вариант, где ip-адрес и количество заходов:

```

# Открываем файл с логами
with open('log_file.log', 'r') as file:
    logs = file.readlines()

ip_addresses = {}

# Парсим файл с логами и считаем количество обращений от каждого IP-адреса
for log in logs:
    ip = log.split(' ')[0]
    if ip in ip_addresses:
        ip_addresses[ip] += 1
    else:
        ip_addresses[ip] = 1

# Создаем файл для записи результата
with open('ip_counts.txt', 'w') as result_file:
    for ip, count in ip_addresses.items():
        result_file.write(f'{ip}: {count}\n')
```

Вариант посложнее, где ip-адрес, ОС, количество заходов:

```
# Открываем лог файл
with open('nginx.log', 'r') as file:
    lines = file.readlines()

ip_counts = {}

# Обрабатываем каждую строку лога
for line in lines:
    ip = line.split()[0]
    ua = line.split('"')[5]
    os = ua.split('(')[1].split(';')[0]
    
    # Увеличиваем счетчик для IP-адреса
    if ip in ip_counts:
        ip_counts[ip][os] = ip_counts[ip].get(os, 0) + 1
    else:
        ip_counts[ip] = {os: 1}

# Записываем результаты в файл
with open('ip_counts.txt', 'w') as output:
    for ip, os_counts in ip_counts.items():
        output.write(f'{ip}:\n')
        for os, count in os_counts.items():
            output.write(f'  {os}: {count}\n')
```


Кусок из середины лог файла для проверки работоспособности скриптов студентов:

```
137.72.123.240 - - [20/Jun/2024:13:04:21 +0300] "PATCH /emulation/Intuitive/leading%20edge_instruction%20set-Centralized.jpg HTTP/1.1" 200 1520 "-" "Mozilla/5.0 (Macintosh; PPC Mac OS X 10_9_10 rv:2.0) Gecko/1941-18-10 Firefox/35.0"
90.198.174.0 - - [20/Jun/2024:13:04:21 +0300] "PUT /client-driven-Synchronised.png HTTP/1.1" 200 1426 "-" "Opera/10.54 (X11; Linux x86_64; en-US) Presto/2.10.319 Version/13.00"
84.124.11.149 - - [20/Jun/2024:13:04:21 +0300] "GET /Self-enabling-Realigned.htm HTTP/1.1" 200 1241 "-" "Mozilla/5.0 (Windows NT 5.1) AppleWebKit/5352 (KHTML, like Gecko) Chrome/37.0.811.0 Mobile Safari/5352"
237.85.139.245 - - [20/Jun/2024:13:04:21 +0300] "GET /knowledge%20user%20Networked_modular.svg HTTP/1.1" 500 73 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_8_8 rv:6.0; en-US) AppleWebKit/534.29.3 (KHTML, like Gecko) Version/5.1 Safari/534.29.3"
68.137.67.237 - - [20/Jun/2024:13:04:21 +0300] "GET /leverage%20core/value-added-bi-directional_middleware.php HTTP/1.1" 301 36 "-" "Mozilla/5.0 (Macintosh; PPC Mac OS X 10_6_10 rv:5.0; en-US) AppleWebKit/535.34.3 (KHTML, like Gecko) Version/6.1 Safari/535.34.3"
37.152.132.29 - - [20/Jun/2024:13:04:21 +0300] "GET /Total.jpg HTTP/1.1" 200 2423 "-" "Mozilla/5.0 (iPad; CPU OS 7_1_3 like Mac OS X; en-US) AppleWebKit/536.17.2 (KHTML, like Gecko) Version/4.0.5 Mobile/8B111 Safari/6536.17.2"
222.4.171.217 - - [20/Jun/2024:13:04:21 +0300] "GET /Streamlined-Synchronised-firmware.css HTTP/1.1" 200 2785 "-" "Mozilla/5.0 (Macintosh; PPC Mac OS X 10_8_1) AppleWebKit/5352 (KHTML, like Gecko) Chrome/36.0.821.0 Mobile Safari/5352"
249.197.108.241 - - [20/Jun/2024:13:04:21 +0300] "GET /bifurcated_Optimized-internet%20solution/intermediate-ability.htm HTTP/1.1" 301 95 "-" "Mozilla/5.0 (Macintosh; PPC Mac OS X 10_5_6) AppleWebKit/5341 (KHTML, like Gecko) Chrome/36.0.802.0 Mobile Safari/5341"
209.66.221.80 - - [20/Jun/2024:13:04:21 +0300] "GET /attitude-national.hmtl HTTP/1.1" 200 2343 "-" "Mozilla/5.0 (Windows NT 5.2) AppleWebKit/5330 (KHTML, like Gecko) Chrome/37.0.801.0 Mobile Safari/5330"
50.228.220.30 - - [20/Jun/2024:13:04:21 +0300] "PUT /uniform.gif HTTP/1.1" 200 2810 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.01) AppleWebKit/534.5.6 (KHTML, like Gecko) Version/5.0 Safari/534.5.6"
187.60.223.43 - - [20/Jun/2024:13:04:21 +0300] "POST /ability-workforce%20Assimilated.htm HTTP/1.1" 200 1141 "-" "Mozilla/5.0 (X11; Linux i686) AppleWebKit/5311 (KHTML, like Gecko) Chrome/38.0.827.0 Mobile Safari/5311"
9.54.216.156 - - [20/Jun/2024:13:04:21 +0300] "GET /User-centric_initiative-info-mediaries.htm HTTP/1.1" 200 1693 "-" "Mozilla/5.0 (Windows NT 5.1) AppleWebKit/5322 (KHTML, like Gecko) Chrome/40.0.874.0 Mobile Safari/5322"
117.112.104.8 - - [20/Jun/2024:13:04:21 +0300] "GET /Stand-alone_leading%20edge-solution-oriented%20Persevering_static.css HTTP/1.1" 200 1940 "-" "Opera/10.89 (Windows 98; Win 9x 4.90; en-US) Presto/2.11.314 Version/11.00"
61.202.47.235 - - [20/Jun/2024:13:04:21 +0300] "HEAD /Profit-focused_capacity.svg HTTP/1.1" 200 1251 "-" "Mozilla/5.0 (Windows 98; Win 9x 4.90) AppleWebKit/5311 (KHTML, like Gecko) Chrome/40.0.839.0 Mobile Safari/5311"
83.174.83.243 - - [20/Jun/2024:13:04:21 +0300] "GET /benchmark.js HTTP/1.1" 200 2551 "-" "Mozilla/5.0 (X11; Linux x86_64; rv:5.0) Gecko/1919-18-08 Firefox/35.0"
18.242.227.170 - - [20/Jun/2024:13:04:21 +0300] "GET /Mandatory.svg HTTP/1.1" 200 1085 "-" "Mozilla/5.0 (Macintosh; U; PPC Mac OS X 10_9_0) AppleWebKit/5332 (KHTML, like Gecko) Chrome/40.0.863.0 Mobile Safari/5332"
125.108.27.240 - - [20/Jun/2024:13:04:21 +0300] "GET /encompassing/User-friendly%20transitional.svg HTTP/1.1" 200 993 "-" "Mozilla/5.0 (X11; Linux i686; rv:8.0) Gecko/1959-14-11 Firefox/35.0"
128.218.212.59 - - [20/Jun/2024:13:04:21 +0300] "GET /system%20engine%20Function-based/contextually-based/strategy.php HTTP/1.1" 200 3037 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_5_4 rv:6.0; en-US) AppleWebKit/536.45.6 (KHTML, like Gecko) Version/6.2 Safari/536.45.6"
84.229.179.25 - - [20/Jun/2024:13:04:21 +0300] "GET /optimizing.htm HTTP/1.1" 200 2617 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/5322 (KHTML, like Gecko) Chrome/39.0.853.0 Mobile Safari/5322"
141.238.32.188 - - [20/Jun/2024:13:04:21 +0300] "GET /content-based_Centralized-background/composite.svg HTTP/1.1" 200 1351 "-" "Mozilla/5.0 (Macintosh; PPC Mac OS X 10_8_2) AppleWebKit/5341 (KHTML, like Gecko) Chrome/36.0.843.0 Mobile Safari/5341"
151.214.159.178 - - [20/Jun/2024:13:04:21 +0300] "GET /eco-centric/Managed_24/7.js HTTP/1.1" 500 40 "-" "Mozilla/5.0 (Windows 95) AppleWebKit/5322 (KHTML, like Gecko) Chrome/37.0.813.0 Mobile Safari/5322"
206.44.203.1 - - [20/Jun/2024:13:04:21 +0300] "PATCH /Down-sized_neural-net_Ergonomic.gif HTTP/1.1" 200 1089 "-" "Mozilla/5.0 (Windows; U; Windows 95) AppleWebKit/535.47.2 (KHTML, like Gecko) Version/6.2 Safari/535.47.2"
227.165.81.201 - - [20/Jun/2024:13:04:21 +0300] "POST /coherent%20Switchable-explicit/3rd%20generation/zero%20defect.htm HTTP/1.1" 200 1172 "-" "Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10_9_3) AppleWebKit/5320 (KHTML, like Gecko) Chrome/40.0.888.0 Mobile Safari/5320"
161.44.118.80 - - [20/Jun/2024:13:04:21 +0300] "GET /Implemented-Robust/analyzer%20dedicated/encompassing.js HTTP/1.1" 400 109 "-" "Mozilla/5.0 (Windows; U; Windows NT 4.0) AppleWebKit/533.26.3 (KHTML, like Gecko) Version/4.1 Safari/533.26.3"
218.0.168.129 - - [20/Jun/2024:13:04:21 +0300] "GET /matrix/Exclusive-mobile_Down-sized.png HTTP/1.1" 200 1052 "-" "Mozilla/5.0 (Macintosh; U; PPC Mac OS X 10_7_4) AppleWebKit/5352 (KHTML, like Gecko) Chrome/40.0.874.0 Mobile Safari/5352"
167.241.121.77 - - [20/Jun/2024:13:04:21 +0300] "GET /bifurcated-6th%20generation/local%20area%20network/explicit.svg HTTP/1.1" 200 3043 "-" "Mozilla/5.0 (Windows 98; en-US; rv:1.9.1.20) Gecko/1918-06-01 Firefox/35.0"
123.228.3.101 - - [20/Jun/2024:13:04:21 +0300] "POST /dynamic-Diverse/Progressive/Triple-buffered.png HTTP/1.1" 200 2748 "-" "Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10_8_8 rv:7.0; en-US) AppleWebKit/536.18.6 (KHTML, like Gecko) Version/5.1 Safari/536.18.6"
204.12.173.120 - - [20/Jun/2024:13:04:21 +0300] "POST /bottom-line/Open-source.htm HTTP/1.1" 301 118 "-" "Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10_6_9 rv:6.0; en-US) AppleWebKit/534.16.1 (KHTML, like Gecko) Version/6.0 Safari/534.16.1"
160.75.246.53 - - [20/Jun/2024:13:04:21 +0300] "GET /Customizable/Visionary/Diverse.htm HTTP/1.1" 200 863 "-" "Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10_6_1) AppleWebKit/5351 (KHTML, like Gecko) Chrome/36.0.810.0 Mobile Safari/5351"
47.244.202.180 - - [20/Jun/2024:13:04:21 +0300] "GET /fault-tolerant-high-level.gif HTTP/1.1" 200 2309 "-" "Mozilla/5.0 (Windows NT 6.0; en-US; rv:1.9.1.20) Gecko/1947-23-11 Firefox/35.0"
186.81.239.166 - - [20/Jun/2024:13:04:21 +0300] "GET /cohesive-exuding-middleware.gif HTTP/1.1" 200 1508 "-" "Mozilla/5.0 (Windows CE) AppleWebKit/5340 (KHTML, like Gecko) Chrome/39.0.841.0 Mobile Safari/5340"
215.19.225.11 - - [20/Jun/2024:13:04:21 +0300] "GET /Horizontal/De-engineered/bandwidth-monitored.jpg HTTP/1.1" 200 994 "-" "Opera/10.21 (Macintosh; Intel Mac OS X 10_8_1; en-US) Presto/2.13.206 Version/13.00"
205.75.223.26 - - [20/Jun/2024:13:04:21 +0300] "GET /tangible/data-warehouse.htm HTTP/1.1" 200 1019 "-" "Mozilla/5.0 (Windows 98) AppleWebKit/5342 (KHTML, like Gecko) Chrome/36.0.869.0 Mobile Safari/5342"
23.55.24.119 - - [20/Jun/2024:13:04:21 +0300] "PUT /throughput.php HTTP/1.1" 200 1721 "-" "Opera/9.28 (Windows NT 6.1; en-US) Presto/2.11.316 Version/10.00"
72.78.101.96 - - [20/Jun/2024:13:04:21 +0300] "GET /synergy/structure.jpg HTTP/1.1" 200 2310 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/5352 (KHTML, like Gecko) Chrome/36.0.843.0 Mobile Safari/5352"
73.21.10.188 - - [20/Jun/2024:13:04:21 +0300] "GET /exuding%20cohesive.png HTTP/1.1" 200 1802 "-" "Mozilla/5.0 (Windows NT 4.0) AppleWebKit/5322 (KHTML, like Gecko) Chrome/38.0.849.0 Mobile Safari/5322"
86.203.151.165 - - [20/Jun/2024:13:04:21 +0300] "GET /data-warehouse.js HTTP/1.1" 200 2672 "-" "Mozilla/5.0 (Windows NT 6.0) AppleWebKit/5310 (KHTML, like Gecko) Chrome/38.0.863.0 Mobile Safari/5310"
91.215.251.247 - - [20/Jun/2024:13:04:21 +0300] "GET /access/Sharable-Horizontal.png HTTP/1.1" 200 2945 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_1 rv:7.0) Gecko/1903-27-04 Firefox/36.0"
7.97.71.217 - - [20/Jun/2024:13:04:21 +0300] "HEAD /Profit-focused/full-range-secondary/budgetary%20management_Reactive.hmtl HTTP/1.1" 200 1626 "-" "Mozilla/5.0 (X11; Linux x86_64; rv:7.0) Gecko/1925-15-11 Firefox/35.0"
208.69.32.4 - - [20/Jun/2024:13:04:21 +0300] "GET /implementation-Triple-buffered-tangible-systemic/standardization.svg HTTP/1.1" 200 947 "-" "Mozilla/5.0 (Windows 95) AppleWebKit/5322 (KHTML, like Gecko) Chrome/40.0.845.0 Mobile Safari/5322"
174.199.24.238 - - [20/Jun/2024:13:04:21 +0300] "GET /Multi-tiered-function-non-volatile.php HTTP/1.1" 301 43 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.2) AppleWebKit/532.1.2 (KHTML, like Gecko) Version/4.2 Safari/532.1.2"
31.103.23.111 - - [20/Jun/2024:13:04:21 +0300] "GET /task-force_Synergized/tangible_national_toolset.svg HTTP/1.1" 200 1039 "-" "Mozilla/5.0 (Windows CE) AppleWebKit/5330 (KHTML, like Gecko) Chrome/38.0.801.0 Mobile Safari/5330"
28.194.71.98 - - [20/Jun/2024:13:04:21 +0300] "PUT /local-Focused/artificial%20intelligence-Exclusive.png HTTP/1.1" 200 840 "-" "Mozilla/5.0 (Windows NT 6.1; en-US; rv:1.9.1.20) Gecko/2007-01-09 Firefox/37.0"
47.60.246.77 - - [20/Jun/2024:13:04:21 +0300] "PATCH /hardware/encompassing_secondary_Decentralized.htm HTTP/1.1" 200 2031 "-" "Opera/10.27 (Windows 95; en-US) Presto/2.13.280 Version/11.00"
187.152.218.97 - - [20/Jun/2024:13:04:21 +0300] "POST /Versatile.js HTTP/1.1" 500 118 "-" "Mozilla/5.0 (Macintosh; PPC Mac OS X 10_6_0) AppleWebKit/5351 (KHTML, like Gecko) Chrome/40.0.833.0 Mobile Safari/5351"
42.4.163.251 - - [20/Jun/2024:13:04:21 +0300] "DELETE /solution.css HTTP/1.1" 200 2487 "-" "Mozilla/5.0 (X11; Linux i686) AppleWebKit/5340 (KHTML, like Gecko) Chrome/36.0.874.0 Mobile Safari/5340"
195.10.86.63 - - [20/Jun/2024:13:04:21 +0300] "GET /frame_radical%20knowledge%20base.gif HTTP/1.1" 200 2417 "-" "Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10_8_9 rv:2.0) Gecko/1932-05-11 Firefox/37.0"
48.4.168.38 - - [20/Jun/2024:13:04:21 +0300] "GET /ability/protocol-multi-state-holistic-Proactive.jpg HTTP/1.1" 200 1165 "-" "Mozilla/5.0 (X11; Linux x86_64; rv:7.0) Gecko/1990-06-04 Firefox/36.0"
230.219.161.209 - - [20/Jun/2024:13:04:21 +0300] "POST /multi-tasking/stable%20asymmetric.hmtl HTTP/1.1" 200 2819 "-" "Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10_5_7) AppleWebKit/5320 (KHTML, like Gecko) Chrome/40.0.849.0 Mobile Safari/5320"
253.67.142.124 - - [20/Jun/2024:13:04:21 +0300] "GET /Self-enabling/attitude-oriented/ability-hub-Enterprise-wide.htm HTTP/1.1" 500 51 "-" "Mozilla/5.0 (iPhone; CPU iPhone OS 7_0_1 like Mac OS X; en-US) AppleWebKit/536.3.4 (KHTML, like Gecko) Version/4.0.5 Mobile/8B118 Safari/6536.3.4"
92.164.109.1 - - [20/Jun/2024:13:04:21 +0300] "PUT /contingency-matrix.png HTTP/1.1" 200 2503 "-" "Mozilla/5.0 (Macintosh; U; PPC Mac OS X 10_7_10 rv:5.0; en-US) AppleWebKit/536.4.3 (KHTML, like Gecko) Version/5.1 Safari/536.4.3"
35.78.164.189 - - [20/Jun/2024:13:04:21 +0300] "PATCH /moratorium_fresh-thinking.svg HTTP/1.1" 200 3050 "-" "Opera/10.37 (Windows NT 5.01; en-US) Presto/2.11.178 Version/12.00"
98.22.38.122 - - [20/Jun/2024:13:04:21 +0300] "GET /full-range%20Focused.png HTTP/1.1" 200 2965 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/5311 (KHTML, like Gecko) Chrome/37.0.803.0 Mobile Safari/5311"
221.65.137.234 - - [20/Jun/2024:13:04:21 +0300] "POST /3rd%20generation/monitoring/full-range%20Team-oriented/Graphic%20Interface.svg HTTP/1.1" 200 2347 "-" "Mozilla/5.0 (Macintosh; PPC Mac OS X 10_6_8 rv:7.0) Gecko/1953-08-11 Firefox/36.0"
102.160.42.105 - - [20/Jun/2024:13:04:21 +0300] "GET /moderator/portal/object-oriented_Monitored.svg HTTP/1.1" 302 68 "-" "Mozilla/5.0 (X11; Linux x86_64; rv:5.0) Gecko/1975-17-05 Firefox/36.0"
39.209.123.118 - - [20/Jun/2024:13:04:21 +0300] "POST /non-volatile.svg HTTP/1.1" 200 1719 "-" "Mozilla/5.0 (Windows NT 5.1) AppleWebKit/5330 (KHTML, like Gecko) Chrome/39.0.817.0 Mobile Safari/5330"
6.251.76.144 - - [20/Jun/2024:13:04:21 +0300] "GET /service-desk.png HTTP/1.1" 302 78 "-" "Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10_9_1) AppleWebKit/5311 (KHTML, like Gecko) Chrome/37.0.871.0 Mobile Safari/5311"
100.131.145.229 - - [20/Jun/2024:13:04:21 +0300] "GET /projection_Progressive/instruction%20set/mobile_structure.jpg HTTP/1.1" 200 2977 "-" "Mozilla/5.0 (Macintosh; PPC Mac OS X 10_7_4) AppleWebKit/5340 (KHTML, like Gecko) Chrome/40.0.808.0 Mobile Safari/5340"
141.149.227.165 - - [20/Jun/2024:13:04:21 +0300] "PUT /Reverse-engineered/background-Graphical%20User%20Interface/De-engineered.php HTTP/1.1" 200 1063 "-" "Mozilla/5.0 (Windows CE; en-US; rv:1.9.1.20) Gecko/2007-23-03 Firefox/36.0"
53.21.22.189 - - [20/Jun/2024:13:04:21 +0300] "GET /Synchronised/Centralized.htm HTTP/1.1" 200 1970 "-" "Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10_9_2) AppleWebKit/5310 (KHTML, like Gecko) Chrome/39.0.876.0 Mobile Safari/5310"
140.7.186.28 - - [20/Jun/2024:13:04:21 +0300] "GET /grid-enabled/Balanced/methodology.htm HTTP/1.1" 400 71 "-" "Mozilla/5.0 (Macintosh; PPC Mac OS X 10_6_3) AppleWebKit/5341 (KHTML, like Gecko) Chrome/37.0.838.0 Mobile Safari/5341"
220.86.33.30 - - [20/Jun/2024:13:04:21 +0300] "PUT /Customizable/radical%20contextually-based-Distributed.jpg HTTP/1.1" 200 1257 "-" "Mozilla/5.0 (Windows NT 5.2) AppleWebKit/5342 (KHTML, like Gecko) Chrome/39.0.826.0 Mobile Safari/5342"
232.77.4.15 - - [20/Jun/2024:13:04:21 +0300] "POST /circuit/Automated-system%20engine_contingency.php HTTP/1.1" 200 2583 "-" "Opera/8.40 (Macintosh; U; PPC Mac OS X 10_9_5; en-US) Presto/2.13.225 Version/12.00"
123.172.138.96 - - [20/Jun/2024:13:04:21 +0300] "GET /Advanced-contextually-based/methodology/secondary%20stable.htm HTTP/1.1" 500 68 "-" "Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10_5_5 rv:5.0) Gecko/2006-08-11 Firefox/37.0"
6.172.49.122 - - [20/Jun/2024:13:04:21 +0300] "DELETE /value-added%20Open-architected_Realigned/Reduced/software.js HTTP/1.1" 200 1548 "-" "Mozilla/5.0 (Macintosh; PPC Mac OS X 10_8_3) AppleWebKit/5361 (KHTML, like Gecko) Chrome/40.0.813.0 Mobile Safari/5361"
175.58.162.88 - - [20/Jun/2024:13:04:21 +0300] "GET /complexity/tertiary-fault-tolerant.hmtl HTTP/1.1" 200 1179 "-" "Mozilla/5.0 (Macintosh; U; PPC Mac OS X 10_7_3 rv:7.0; en-US) AppleWebKit/535.22.1 (KHTML, like Gecko) Version/4.2 Safari/535.22.1"
24.151.169.96 - - [20/Jun/2024:13:04:21 +0300] "GET /tertiary.css HTTP/1.1" 200 2769 "-" "Opera/8.35 (X11; Linux i686; en-US) Presto/2.13.204 Version/13.00"
170.40.189.153 - - [20/Jun/2024:13:04:21 +0300] "GET /support/functionalities/5th%20generation_firmware.png HTTP/1.1" 200 1718 "-" "Mozilla/5.0 (Macintosh; U; PPC Mac OS X 10_6_1 rv:2.0) Gecko/1931-17-09 Firefox/37.0"
143.225.107.178 - - [20/Jun/2024:13:04:21 +0300] "PUT /Optional/Public-key/optimizing.htm HTTP/1.1" 200 1885 "-" "Mozilla/5.0 (X11; Linux x86_64; rv:7.0) Gecko/1979-23-11 Firefox/35.0"
183.97.165.190 - - [20/Jun/2024:13:04:21 +0300] "DELETE /secured%20line-fault-tolerant-capacity.gif HTTP/1.1" 302 96 "-" "Mozilla/5.0 (Macintosh; U; PPC Mac OS X 10_7_2 rv:2.0) Gecko/1904-22-07 Firefox/35.0"
```
