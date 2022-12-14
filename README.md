# HotelsForYou bot
Телеграм-бот, который ищет временное жилье в любой точке мире, исходя из предпочтения пользователя. Бот парсит API Hotels.com для вывода конечной информации по нужным критериям, которые пользователь предоставляет в ходе опроса. 

Опрос состоит из нескольких ступеней:
1. Направление (город)
2. Уточнение направления (районы города или города с идентичным названием в других странах)
3. Фильтр поиска (Самые дешевые | Low Price; Самые дорогие | High Price; Пользовательский поиск | Best Deal)
4. Дата прибытия 
5. Дата отъезда 
6. Кол-во выгруженны вариантов (макс. - 25)

Основной функционал бота зиждиться на фильтре поиска: 
* Low Price (поиск самых дешевых вариантов жилья в районе выбранного направления); 
* High Price (поиск самых дорогих вариантов жилья в районе выбранного направления); 
* Best Deal (пользовательский поиск, строящийся на диапазоне цены и расстоянии от центра). 

Callback_data от inline клавиатуры с выбранным фильтром передается фунцкии-парсеру, которая выполняет подбор отелей. 

Пользователю, после вывода ботом финальной информации, предоставляеются следующие дополнительные опции:
* Посмотреть фото выбранного им отеля (осуществляется с помощью отдельной функции-парсера);
* Забронировать жилье на выбранные даты (бронь происходит напрямую через сайт Hotels.coм).

# Особенности телеграм-бота
* Бот запоминает историю поиска пользователя, занося после первой итерации всю необходимую информацию в базу данных, и далее пользователю будет доступна опция просмотра истории поиска;
* Для управления ботом используются исключительно кнопки, за исключением запуска и помощи по функционалу;
* Простая подготовка запуска бота.

# Requirements 
* Python 3.10
* Telebot 0.0.4
* peewee 3.15
* python-dotenv

# Запуск телеграм-бота
Запустить файл main.python

# Структура базы данных: 
* SQLite
  * SearchHistory
     * id (INTEGER) - первичный ключи; 
     * user_id (INTEGER) - id пользователя;
     * user_name (TEXT) - имя пользователя;
     * date (DATE) - дата поиска; 
     * time (TIME) - время поиска; 
     * result (TEXT) - результат поиска.

# Команды бота:
* /start - запуск бота;
* /help - помощь по функционалу бота 
