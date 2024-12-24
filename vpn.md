
# Гайд по впн для самых маленьких
Инструкция будет обновляться по мере поступления новой информации/проблем у юзеров. 
Содержание:
1. [Покупка vps](#покупка-vps)
2. [Подключение к серверу](#подключение-к-серверу)
3. [Выбор протокола](#выбор-протокола)
	1. [AmneziaVPN](#amneziavpn)
	2. [Shadowsocks + cloak](#shadowsocks-cloak)
***


## Покупка vps
vps - virtual private server, удалённый сервер, предоставляемый неким провайдером. Стоят от 100 рублей в месяц до бесконечности, разница в ттх сервера, ограничениях трафика и т.д.
Купить сервер можно вообще где угодно, я рекомендую aeza.net, т.к. можно оплатить ру картами без костылей и стоит максимально подъёмно.
Инструкция по покупке сервера на aeza:
1. Регистрируемся на сайте ([тык](https://aeza.net/?ref=460622)) - реферальная ссылка. При регистрации по ней и оплате в течение суток будет скидка 15%. Можно зайти через гугл, не придётся запоминать ещё один пароль.
2. Заходим во вкладку "Виртуальный сервер" ([тык](https://my.aeza.net/order/vps)), выбираем название сервера. Влиять ни на что не будет, просто потом будет проще отличить один от другого если решите поднять несколько впнов. Я обзову свой "black-man". Далее выбираем локацию. От этого выбора будет зависеть цена услуги и айпи после впна, то есть реклама и всё что с ней связано. Тот самый дешёвый впс за сто тугриков в месяц находится в стране вольво, икеи и фрикаделек, поэтому тыкаем на швецию, выбираем самый дешёвый тариф.
!!! warning Важно!
    PROMO тариф ограничен по скорости и пропускает через себя только 100 Мбит/С. Если этого мало, стоит задуматься о более дорогом тарифе, но для большинства впнов на 1-2-3 пользователя скорее всего хватит и самого дешёвого.
3. ОС выбираем Ubuntu **20.04**, бэкапы отключаем, нам они не нужны.
4. Оплачиваем любым удобным способом, заходим в вкладку "Мои услуги" ([тык](https://my.aeza.net/services/727257)), ждём несколько минут пока накатится ОС и сервер просрётся, открываем панель управления сервером.
![](https://i.imgur.com/wpqLKoY.png)
5. Чтобы каждый раз не заходить на сайт советую сохранить ip адрес, и пароль в .txt документе на рабочем столе или в заметках на телефоне.


***


## Подключение к серверу
Это делать не обязательно если собираетесь ставить AmneziaVPN.
Теперь нам надо подключиться к серверу. Подключаться будем через ssh. С винды/линукса подключиться можно не скачивая ничего лишнего. На ведроид скачиваем приложение [ConnectBot](https://play.google.com/store/apps/details?id=org.connectbot) или любой другой ssh клиент.

1. Подключаемся к серверу через ssh
  1. На Windows/Linux открываем консоль и прописываем ```ssh root@айпи``` где айпи это ip адрес сервера из панели управления. Сервер запросит пароль для подключения, вставляем пароль из панели управления. Для безопасности он не отображается, но он там есть. Вставили нажатием правой кнопки мыши, тыкаем энтер, добро пожаловать на сервер.
  2. На ведроиде открываем приложение, тыкаем на плюсик, добавляем сервер. Поменять надо только первую строчку, туда вводим ```root@айпи```
![](https://i.imgur.com/WICXnKG.png)


***


## Выбор протокола
В старой версии документа (тык) рассматривалась установка shadowsocks и vless, инструкции по ним можно почитать по ссылке выше.
Кратко про те протоколы, которые рассматриваются сейчас:

AmneziaVPN - Приложение с полностью открытым исходным кодом для автоматической установки и настройки vpn сервера. Есть много разных протоколов, основной - AmneziaWG, вариация на тему вокруг стандартного Wireguard. Околонеблокируемый, недетектируемый и так далее. Оптимальный вариант для "настроил и забыл". Клиенты на все платформы, установка серверной части в два клика без входа в ssh.

Shadowsocks + cloak - версия протокола shadowsocks, в котором трафик обфусцируется и для провайдера/тспу всё выглядит так, будто вы открываете какой-нибудь разрешённый сайт. Должен быть undetectable, но некоторые провайдеры умудряются банить. Установка в два клика мышью, клиенты на любые платформы, установка клиентов заёбистая

Vless+reality - вернул по просьбам трудящихся


### AmneziaVPN
Целый комбайн для установки впн, клиент есть на любые девайсы, скачать можно на гитхабе ([тык](https://github.com/amnezia-vpn/amnezia-client/releases)). Скачиваем, запускаем, жмём Self-hosted VPN, в поля вбиваем айпишник сервера, имя пользователя (у нас root) и пароль от ssh, всё это можно получить в панели хостинга (в нашем случае aeza). Дальше программа сама всё настроит и установит.
Приложение предложит ответить, высокий ли у вас в стране уровень цензуры или выбрать протокол. Выбираем высокий, жмём дальше и ждём.
Как только вас пустит в приложение - всё готово. Поделиться конфигом/добавить доп пользователей можно по второй икноке слева, в нижней панели. Меняем только имя пользователя, всё остальное оставляем по дефолту, внизу кнопка "Поделиться". Создастся конфиг, копируем ссылку или показываем человеку qr код, готово.

По умолчанию в Amnezia используется устойчивый к блокировкам протокол AmneziaWG, но есть и другие, при желании можно посмотреть по приложению, так что при блокировка AWG можно будет попробовать другие протоколы.

### Shadowsocks + cloak <a id="shadowsocks-cloak"></a>
Устанавливается в 1 команду, благодаря установщику от [hirbodbehnam](https://github.com/HirbodBehnam/Shadowsocks-Cloak-Installer).
Просто подключаемся по ssh и вставляем следующее:
```curl -o Cloak-Installer.sh -L https://git.io/fj5mh && bash Cloak-Installer.sh```
На все вопросы просто тыкаем энтер, стандартные значения чаще всего самые подходящие
В конце установки получим qr код, и строку доступа внизу страницы, строку сохраняем куда-нибудь где не потеряем.
![](https://i.imgur.com/hW5mmPJ.png)

Клиенты:
Android: Скачиваем [раз](https://play.google.com/store/apps/details?id=com.github.shadowsocks) и [два](https://github.com/cbeuw/Cloak-android/releases), устанавливаем оба приложения, в первом сканируем qr или вставляем строку через кнопку справа вверху

IOS: Вот [это](https://apps.apple.com/us/app/shadowrocket/id932747118) приложение по идее должно поддерживать протокол из коробки, но проверить возможности нет.

Windows: скачиваем [программу](https://github.com/shadowsocks/shadowsocks-windows/releases), скачиваем файлик для вашей системы (если 64 бит, ck-client-windows-amd64-.exe, если 32, то ck-client-windows-386-X.exe, если не уверены - скачивайте первый), закидываем и то, и другое в какую-нибудь папочку для удобства пользования.
После запуска первой откроется окно, закрываем, открываем трей, пкм на иконку и добавляем сервер из предварительно скопированной строки
![](https://i.imgur.com/s1LmidW.png)
Программа выдаст ошибку, нажимаем ок, в том же месте нажимаем Edit Servers. В поле Plugin Program вставляем путь до файлика без кавычек, получить его можно если нажать на файл правой кнопкой мыши с зажатым шифтом и тыкнуть "Скопировать как путь". Сохраняем.
Для запуска проксирования жмём пкм на иконку в трее - system proxy - global
![](https://i.imgur.com/c4WQn4Q.png)

### Установка Vless
Установка этого протокола сильно сложнее и если желания разбираться с ~~хуё~~протоколами то советую остановиться на SS и перейти к клиентам. Если нет - добро пожаловать. Устанавливать будем не через еблю с консолью, а через красивую веб-морду 3x-ui. В установке ничего сложного нет.
Открываем консоль, вводим команды по очереди.
	```bash
	bash <(curl -Ls https://raw.githubusercontent.com/mhsanaei/3x-ui/master/install.sh)
	```
Установщик предложит изменить настройки, нажимаем y. Далее по списку: выбираем логин и пароль, пригодятся позже. Порт можете сделать любой, я выбрал 8761. На последний вопрос пишем panel. Почти готово. Осталось открыть порт, чтобы мы могли зайти в панель с домашней сети. Для этого пропишем:
	```bash
	ufw allow 8761
	```
вместо 8761 подставьте номер порта, который указали в установщике. Открываем браузер на выбор, в адресную строку вставляем:
	```
	http://айпи_сервера:порт/panel```
 Замените айпи и порт на свои значения и запишите куда-нибудь ссылку. Обязательно ещё пригодится. По этой ссылке откроется панель управления впном, а точнее впнами. В 3x-ui можно настроить множество различных протоколов, и даже ShadowSocks, который мы настроили чуть выше, но это более тяжёлый инструмент и надо оно не всем. Заходим в панель, включаем тёмную тему, чтобы глаза не резало и едем дальше.


![](https://i.imgur.com/Y2O9w4l.png)



![](https://i.imgur.com/iOjnJsW.png)


Тыкаем на Подключения - Добавить новое подключение


![](https://i.imgur.com/4jzh32u.png)


Выбираем протокол vless, порт ip оставляем пустым, порт 443. Поле клиент пока пропускаем, вернёмся позже.
Настройки если у вас промо тариф и шведский сервер:
dest ставим teamdocs.su:443
sni teamdocs.su
жмём get cert

![](https://i.imgur.com/1z02Age.png)


Возвращаемся к клиенту.


![](https://i.imgur.com/1g07gwL.png)

В поле email можем ввести что угодно, это надо будет чтобы различать разных клиентов на одном протоколе. Можно например сделать пяток клиентов и раздать корешам и каждому расход ограничить несколькими гигабайтами чтоб не втыкали. Протокол ставим как на скрине выше.

В итоге имеем следующую картину:


![](https://i.imgur.com/IXA6xF5.png)

Нажав на иконку qr кода можем отсканировать его с мобилки или скинуть скриншот корешу. Нажав на сам qr скопируется конфиг впна в формате строки.