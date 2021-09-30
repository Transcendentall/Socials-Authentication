# Socials-Authentication

# Лабораторная работа № 2 "Socials-Authentication" 
# по теме "Протокол HTTP. Основы работы с консолью разработчика в браузере."

# Цель: 
Получить практические навыки работы с HTTP протоколом, проанализировать процесс аутентификации пользователей в двух произвольных веб-ресурсах.

# Теоретическая часть:
# Постановка задачи: 
Написать эссе, в котором анализируется процесс аутентификации пользователей в двух произвольных веб-ресурсах.

# Порядок выполнения:
# Анализ задачи и написание эссе:

Продолжим мучить сайт ФЕФУ. Поэкспериментируем с блэкбордом, ибо всё равно мы его почти не используем.

Итак, https://bb.dvfu.ru/.

<img src="https://github.com/Transcendentall/Socials-Authentication/blob/main/104.jpg">

Заходим. Сразу бросается в глаза bb.dvfu.ru, открываем его и видим кучу заголовков запроса.

		Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
		Accept-Encoding: gzip, deflate, br
		Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
		Connection: keep-alive
		Cookie: _ga=GA1.2.1154677803.1629866822; _ym_uid=162986682260831964; _ym_d=1629866822; _gid=GA1.2.242962149.1632876390; _ym_isad=2; _ym_visorc=w; session_id=0ADA578C92D74A67AB39FF077F2EEEC7; s_session_id=58C62945C882162F8BE07C5AE516FF90; web_client_cache_guid=01e82d19-fcd0-457f-924f-82a3988d1e1f; _univer_session=44flhg7ep71jkbrtqre2akgpng; LtpaToken2=0lLH7FyctgcA/sRfjAQFYb8XcMiv8yg5M1ASCr8hzfJahjZbrQGnlfROGdbzhkJEFrVlIASk9FTHbjlePeNDXfCCJo4rqRLnuVowSkRY5LDTv4J6FMDq5VUP0dbd88IP9wCXpk5IIktwFLAnIJzt7EX2EgIgu1usGKt38/Odp5MADfpRpnuCSLGixZkE/orgnfmpSFbk44j9UZ/C3W/tPaLnje3fFwd/3FbyN3nOPM8FUWa43eJ1wqTbKjNbrIYeOMA/zeqVp44aUcegxkVGZ771L+EJ5DKqO285cG2LqBnyxJ+lZyVN3AfqzkfBOibU1WoqZHi0wa/fQr5wQZEYdT9C3yZ2zWrcCZJkl35PpqFGqXKWdtvuNOqZK5sFXQenPEYH0T748sInFGNsLG1pcw==; _univer_identity=6ec573ef220bb659ee677629a4880ed00766c398c10cbfe9e2b6a1baf58f55f2a%3A2%3A%7Bi%3A0%3Bs%3A16%3A%22_univer_identity%22%3Bi%3A1%3Bs%3A50%3A%22%5B24766%2C%22zdhp1Q77PgllXAtCvZxPgMvDZ9TY2oOb%22%2C2592000%5D%22%3B%7D; _jwts=31cf74b0aee7041f9c2777e6a16954eead9c5d42e36168642b2dd92dffb5d714a%3A2%3A%7Bi%3A0%3Bs%3A5%3A%22_jwts%22%3Bi%3A1%3Bs%3A175%3A%22eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MzM5MTM0OTEsInVpZCI6MjQ3NjYsInVzZXJuYW1lIjoiYm9seWNoZXYubGkiLCJyb2xlIjoiYWRtaW4ifQ.dN57J6NGqyj2PcWMpasVqh-BZaj5eMVeTMiJZ1Brdcs%22%3B%7D; JSESSIONID=6A5D82983D252436636957EBFF6D598C
		Host: bb.dvfu.ru
		sec-ch-ua: "Chromium";v="94", "Google Chrome";v="94", ";Not A Brand";v="99"
		sec-ch-ua-mobile: ?0
		sec-ch-ua-platform: "Windows"
		Sec-Fetch-Dest: document
		Sec-Fetch-Mode: navigate
		Sec-Fetch-Site: none
		Sec-Fetch-User: ?1
		Upgrade-Insecure-Requests: 1
		User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/94.0.4606.61 Safari/537.36


Ах да, и ещё одно. Наверху Status Code: 200 OK, т.е. всё хорошо и страница у нас работает без проблем.
Мы видим, что язык - русский, что платформа - винда и прочие вещи, которые отмечались в прошлом эссе. Но если присмотреться к названиям куков, то среди кучи очень сложных и запутанных имён можно заметить такие интересные вещи, как _univer_identity. Очевидно, эта штука и должна отвечать за авторизацию. А ведь есть ещё и _univer_session...

<img src="https://github.com/Transcendentall/Socials-Authentication/blob/main/105.jpg">


Попробуем провернуть что-нибудь, и посмотреть, будут ли какие-нибудь изменения.

Например, попробуем ввести заведомо неверные логин и пароль:

<img src="https://github.com/Transcendentall/Socials-Authentication/blob/main/106.jpg">

И... о чудо, изменения правда есть, и их много.

Хотя бы начать с того, что мы теперь не в bb.dvfu.ru, а в login.
В первую очередь, конечно, бросается в глаза появившееся снизу окошко "Form Data".

		user_id: billiherrington
		password: threehundredbucks
		login: Войти
		action: login
		new_loc: 

user_id - это введённый нами логин
password - введённый нами пароль
login и action показывают, какое действие мы пытались осуществить (залогиниться, то есть войти).

Что характерно, добавились также новые заголовки запросов. Например заголовков


		Cache-Control: max-age=0
		Content-Length: 109
		Content-Type: application/x-www-form-urlencodedHost: bb.dvfu.ru
		Origin: https://bb.dvfu.ru
		Referer: https://bb.dvfu.ru/

не было раньше.

Т.е. теперь указывается, что страница устаревает через 0 секунд, и что мы переместились сюда из https://bb.dvfu.ru/.
И ведь действительно, мы теперь уже в https://bb.dvfu.ru/webapps/login/.

А теперь попробуем авторизироваться правильно, введя корректные логин и пароль.

После этого статус меняется на 302 Found, т.е. запрошенный документ временно доступен по другому адресу.

Заголовки запросов после этого особо не изменились, как и "Form Data" (но теперь в "Form Data" отображаются наши истинные логин и пароль. По сей причине я "Form Data" показывать, пожалуй, не буду.).
Но вот Responce дополнились новыми куками. Хотя в остальном они тоже без изменений.

<img src="https://github.com/Transcendentall/Socials-Authentication/blob/main/108.jpg">
<img src="https://github.com/Transcendentall/Socials-Authentication/blob/main/107.jpg">

Напоследок попробуем выйти. Замечаем, что после выхода отображается, что наше действие теперь - не login, а logout.

<img src="https://github.com/Transcendentall/Socials-Authentication/blob/main/109.jpg">


_________

Не повредило бы ещё с чем-нибудь поэкспериментировать. Можно было бы попробовать с "Моим универом", но это не самая лучшая идея, потому что и то, и другое ФЕФУшное. Надо бы что-нибудь другое для разнообразия.

Попробуем провернуть то же самое с VK...

Как всегда мы видим много заголовков запросов. А статус страницы 200, тоже как всегда.

<img src="https://github.com/Transcendentall/Socials-Authentication/blob/main/111.jpg">

В случае неверного ввода мы увидим нечто схожее с тем, что мы видели на Блэкборде, но всё же другое. Тут нас ждёт "Query String Parameters" вместо "Form Data", причём здесь есть email, но нет логина, пароля и указания на совершаемое нами действие.

<img src="https://github.com/Transcendentall/Socials-Authentication/blob/main/112.jpg">

Если мы зайдём верно (с корректными логином и паролем), то увидим очень много всего, включая различные "Form Data" и прочее. Но, к чести ВК, тут нельзя так просто взять и найти введённый пользователем пароль. И это очень хорошо!

# Вывод:
Удалось на примере двух сайтов рассмотреть, как реализована авторизация пользователя. Хотя заголовки запросов в обоих случаях были почти одинаковы (кроме куков, разумеется), авторизация работает весьма и весьма по-разному. И степень защищённости данных пользователя тоже разная: в Блэкборде можно легко выяснить пароль и логин, а вот в ВК - нет.
Полагаю, цель лабораторной работы достигнута.

