
# Краткое описание проекта:

_Суть проекта:_ Мониторинг процесса работы (дорожная карта).

**Общие условия:**
- HTML, CSS, PHP, MYSQL (JS – только на сайте и в админпанели, для обычных пользователей – JS не использовать или использовать по минимуму, чтобы функционал оставался работоспособным).
- Оптимизированный и валидный (по W3C) код для быстрой загрузки, нет ошибок в коде.
- Чистый и безопасный код, без лишних ссылок для внешних ресурсов, дыр и уязвимостей.
- Легковесный и компактный (не более 10-20 мб).
- Все ссылки все должны быть относительными - для быстрого трансфера на хостинги.
- Возможность расширять функционал (модульность).
> *Шрифты и цвета*
> - Шрифты: Verdana, Geneva, Sans-serif;
> - Размер шрифтов: 1.5 em
> - Цвета: #3399FF, #333, #666666, Красный

---
**Термины и понятия:**

Мониторинг (контроль) – система учета выполненных, выполняемых и запланированных работ.
- _Updates (текущий контроль)_ – информация о состоянии выполненной, выполняемой и запланированной работе на определённый момент времени (отчет на определенный день).
На сайте это страница со списком (блоки) процессов (задач) (указано на рисунке). 
На каждом блоке кнопки редактирование, архивация и удаление.
   Архивация в блоке (OLD) - -нужна для скрытия выполненных процессов из списка, чтобы не мешали.
   Архив над шапкой (OLD) – это старые выполненное процессы, потребуется для просмотра и возобновления. 
   Также имеется фильтр для фильтрации по пользователю и по метке процесса.
- _Timeline (общий контроль)_ – информация о состоянии выполненных, выполняемых и запланированных работ на всем промежутке времени (ход работы - полный отчет от начала до конца).
На сайте это страница с генерированной [таблицей](https://github.com/Rustapo/pro_tz/blob/master/1.xlsx) содержащая данные в виде даты (указано в [таблице](https://github.com/Rustapo/pro_tz/blob/master/1.xlsx)).
- _User panel / Admin panel_ (сам персональный кабинет) - индивидуальная страница пользователя, содержащая блок ссылок на страницы сайта доступные для текущего пользователя.
- _Users_ (обычные пользователи) - все зарегистрированные пользователи, которые не имеют доступа к данным других пользователей и не знают о существовании других пользователей, работа с ними идет индивидуально. Система изолированных пользователей со своим текущим и общим контролем статуса.
- _Группы / Права пользователей_ - назначение прав пользователям для работы (просмотр и изменение) в разделах сайта.
Существует следующие группы (админ, модер, пользователь) и Права ( открыть/закрыть доступ к просмотру статической страницы).
## Основной функционал:

**1) Пользователи:**
![Админу](https://github.com/Rustapo/pro_tz/blob/master/6a.jpg)

_Admin (Администратор)_ – все возможности включены;

_Функции администратора:_
- создает/редактирует/удаляет пользователя (Логин, Имя, E-mail для уведомлений, назначает группы и права, активный/не активный)
На странице с пользователями должны быть видны дата последнего входа;
- назначает группу модератора и указывает с какими пользователями он может работать;
- добавляет права любому пользователю (просмотр закрытых статических страниц);
- создает/редактирует/удаляет процесс (также этапы и стадии);
- пишет в чат пользователю (модератор также участвует, если назначен);
- получает уведомления на E-mail и визуально на блоке – от Пользователя и Модератора.
- создает/редактирует/удаляет статические страницы (для одного/всех пользователей).
- импортирует в БД таблицу xls / xlsx.

_Moderator (Модератор)_ – это обычный пользователь, который может смотреть/изменять данные в Updates определенных пользователей (разрешенные администратором).
При выборе Moderator должна появиться (или будет неактивной до выбора) комбо выбора пользователей, которые разрешены для просмотра/изменений данных для текущего пользователя.
Если модератор добавит/изменит процесс или напишет в чат, то Админ также должен уведомляться.

_Функции модератора:_
- создает/редактирует процесс (этапы и стадии) для назначенного пользователя.
- пишет в чат назначенному пользователю (админ видит).
- получает уведомления на E-mail и визуально на блоке – от Админа и Пользователя.

_User (Пользователь)_ – это обычный пользователь просмотр только своих данных _Updates_, _Timeline_ и доступных страниц.

_Функции пользователя:_
- входит в кабинет через логин и пароль, который дал админ;
- может переходить в Updates, Timline и доступные страницы;
- видит свой список процессов, созданных админом/модератором;
- видит древо процесса, созданных админом/модератором;
- пишет в чат админу/модератору
- получает уведомления на E-mail и визуально на блоке – от Админа и Модератора.

---
**2. Мониторинг процессов:**


_Updates:_ Отображается «Древо процесса» (Этапы и Стадии) и «Чат с пользователем».
При создании/редактировании процесса Админом/Модератором, написании в Чат –приходит уведомление на почту Пользователя.
**_a)_** Администратор заполняет форму содержащая для заполнения следующие поля:
- Дата, время (ставится автоматически с указанием временного пояса +5,0);
- Комбо поле с пользователями (список пользователей зарегистрированной в системе);
- Название процесса, Описание процесса и т.д. как указано на рисунке, названия этапов/стадий указано в [таблице](https://github.com/Rustapo/pro_tz/blob/master/1.xlsx);
- Метки которые меняют цвет блока процесса и этапа:
«Normal» (стоит по умолчанию), «Confirmation»,«Urgent», «Approval» - выделяют < div >- блок разными цветами («Normal» – цвет “Silver/Gray”;«Confirmation» – цвет “Pale yellow/Yellow”; «Urgent» – цвет “Pale red/Red”; «Approval» – цвет “Pale green/Green”;
- Кнопка прикрепления файлов в форме для комментариев;
- Кнопка отправки комментариев.
> Пример: Создания процесса "Регистрация телефона":
> - Выбор пользователя в комбо-боксе: Vasya_Pupkin
> - Метка процесса: "NORMAL" (цвет серый).  При изменении метки - меняется цвет блока Этапа в древе процесса и блок самого Процесса в
> Updates. Если цвет был изменен в нескольких этапах, то приоритет будет последнего измененного Этапа.
> - _Название процесса:_ Регистрация телефона
> - _Описание процесса:_ Телефон Iphone
> - _Тип процесса процесса:_ REGISTRATION
> - _Дата добавления_ (текущая по умолчанию или выбор даты): 13-06-2018
> - _Название этапа:_ Pre-submission
> - _Стадия этапа:_ Request to import
> - _Описание:_ "Была создана заявка на импорт телефона и ожидается копии накладной" или -Пусто-.

**_b)_** Если выбрать в блоке тип срочного сообщения "Для этого пользователя" или "Для всех", то:
- При выборе "Для этого пользователя" - все поля становятся неактивными, кроме "Выбор пользователя", "Метка процесса" "Название процесса".
- При выборе "Для всех" - все поля становятся неактивными, кроме "Метка процесса" "Название процесса".

Созданные срочные сообщения отображаются:
- у админа в списке процессов пользователя и доступны для редактирования/удаления.
- у пользователя отображаются/собираются в верхнем блоке "в шапке".

**_c)_** Пользователь кликает в персональном кабинете на ссылку «Updates» попадает на страницу с информацией предназначенная только для его просмотра.
![Админу](https://github.com/Rustapo/pro_tz/blob/master/1a.jpg)
![Пользователю](https://github.com/Rustapo/pro_tz/blob/master/1b.jpg)
![Админу](https://github.com/Rustapo/pro_tz/blob/master/2a.jpg)
![Пользователю](https://github.com/Rustapo/pro_tz/blob/master/2b.jpg)
![Админу](https://github.com/Rustapo/pro_tz/blob/master/3a.jpg)
![Пользователю](https://github.com/Rustapo/pro_tz/blob/master/3b.jpg)
**_d)_** При создании процесса создается этап и стадия одновременно. Процесс не может быть без этапа. Этап не может быть без стадии. Порядок и количество этапов и стадий не фиксирован. Название этапов и стадий указано в [таблице](https://github.com/Rustapo/pro_tz/blob/master/1.xlsx).
![Админу](https://github.com/Rustapo/pro_tz/blob/master/4a.jpg)
**_e)_** При редактировании процесса (этапа, стадии) - открывается форма с подставленными данными из БД. При изменении поля, соответственно вносится изменения.

_Timeline:_ Суммарное отображение данных всех процессов по датам.
![Админу](https://github.com/Rustapo/pro_tz/blob/master/5a.jpg)
![Пользователю](https://github.com/Rustapo/pro_tz/blob/master/5b.jpg)
**a)** для Админа – также имеется комбо с выбором пользователя, для фильтрации по пользователю;
для Модератора – комбо с выбором назначенного пользователя, для фильтрации по пользователю,
для Пользователя – комбо нет, отображается все свои процессы, включая архивные.


**b)** В _Timeline_ генерируется готовая [таблица](https://github.com/Rustapo/pro_tz/blob/master/1.xlsx) по данным _Updates_.
  Если был добавлен/изменен процесс (добавлен/изменен этап или стадия) - то добавляется соответствующая колонка в [таблице](https://github.com/Rustapo/pro_tz/blob/master/1.xlsx).
  Данные автоматические переносятся с _Updates_ в _Timeline_.
  Столбцы с названиями Этапа/Стадии будут появлятся по мере создания этапа/стадии и отображать только даты.
  Названия этапов/стадий указано в [таблице](https://github.com/Rustapo/pro_tz/blob/master/1.xlsx).

---
**3. Статические страницы:**
![Админу](https://github.com/Rustapo/pro_tz/blob/master/7a.jpg)
![Админу](https://github.com/Rustapo/pro_tz/blob/master/8a.jpg)
![Пользователю](https://github.com/Rustapo/pro_tz/blob/master/8b.jpg)
![Админу](https://github.com/Rustapo/pro_tz/blob/master/9a.jpg)
![Пользователю](https://github.com/Rustapo/pro_tz/blob/master/9b.jpg)
Простейший WYSIWYG или MARKDOWN редактор для создания/редактирования/удаления статической страницы.
Созданные страницы могут быть доступны для всех или для конкретного пользователя.
В кабинете эти страницы нужны для ссылок скачивания файлов, описания проекта, контакты и любая страница с заметками.

---
**4. Парсинг xls файлов в БД.**
![Админу](https://github.com/Rustapo/pro_tz/blob/master/8a1.jpg)
![Админу](https://github.com/Rustapo/pro_tz/blob/master/8a2.jpg)
   Модифицированный поиск (searchimport.php и searchmoh.php) страница поиска по БД по данным полученные после парсинга xls файла в БД. Скрипт готовый, нужно прикрутить к кабинету.

---
## Дополнительный функционал:
   В дальнейшей поддержке потребуется добавление новых функций
   - матрица Эйзенхауэра
   - Канбан доска,
   - общая статистика,
   - форма для экспорта данных в pdf,
   - календарь событий,
   - мультиязычность,
   - смена темы оформления 
   - другие функции.

---
## Контакты для связи:
## Почта: forwagram+github@gmail.com
## Телеграм: @atocubot или [зеркало](https://t.me/atocubot)
