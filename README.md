# Веб-додаток словник термінів та синонімів
## Функцональні вимоги

1.	Як користувач, я хочу мати можливість створити обліковий запис у додатку шляхом заповнення форми реєстрації, щоб мати доступ до всіх функцій та можливостей.
2.	Як користувач, я хочу мати можливість увійти до свого облікового запису за допомогою логіна та пароля, щоб мати доступ до персоналізованих функцій та інформації.
3.	Як користувач, я хочу мати можливість шукати терміни за їх назвою, оскільки це допоможе мені знаходити бажані слова швидше та ефективніше.
4.	Як користувач, я хочу мати можливість шукати терміни за їх категорією, оскільки це допоможе мені знаходити бажані слова швидше та ефективніше.
5.	Як користувач, я хочу мати можливість зберігати обрані терміни для подальшого використання, оскільки це зручно для мене при навчанні або роботі зі словником.
6.	Як користувач, я хочу мати можливість додавати коментарі та залишати відгуки до словникових термінів, щоб спілкуватися та обмінюватися думками з іншими користувачами.
7.	Як користувач, я хочу мати можливість переглядати синоніми для словникових термінів, щоб отримати додаткову інформацію про них.
8.	Як користувач, я хочу мати можливість додавати власні визначення та пояснення до словникових термінів, щоб доповнювати інформацію в словнику.
9.	Як адміністратор, я хочу мати можливість встановлювати термінам теги як "популярні" або "рекомендовані", щоб виділяти їх серед інших термінів.
10.	Як адміністратор, я хочу мати можливість додавати та оновлювати словникові терміни в базі даних, щоб забезпечити актуальність інформації у словнику.

## Rest API

1. Створити нового користувача (POST api/users)
    - Метод: POST
	- Опис: Створює нового користувача із даними отриманими з форми реєстрації
	- Параметри: Об’єкт користувача
	- Відповідь: Створений новий користувач, або повідомлено про помилку
2. Увійти до облікового запису користувача (POST api/username)
    - Метод: POST
	- Опис: Авторизує користувача за допомогою логіна та пароля
	- Параметри: Логін та пароль користувача
	- Відповідь: Токен авторизації або повідомлення про невдалу авторизацію
3. Шукати терміни за назвою (GET api/words/{word_id})
    - Метод: GET
	- Опис: Здійснює пошук термінів за їх назвою
	- Параметри: Пошуковий запит
	- Відповідь: Список знайдених термінів або порожній список, якщо нічого не знайдено
4. Шукати терміни за категорією (GET api/word_tags/{tag_id})
    - Метод: GET
	- Опис: Здійснює пошук термінів за їх категорією
	- Параметри: Категорія
	- Відповідь: Список знайдених термінів або порожній список, якщо нічого не знайдено
5. Зберегти обрані терміни (POST api/favorites)
    - Метод: POST
	- Опис: Зберігає обрані терміни користувача
	- Параметри: Cписок обраних термінів
	- Відповідь: Збережена збірка або повідомлено про помилку
6. Додати коментар до словникового терміну (POST api/words/{words_id}/comments)
    - Метод: POST
	- Опис: Додає новий коментар до вказаного терміну
	- Параметри: ID терміну та текст коментаря
	- Відповідь: Доданий коментар або повідомлено про помилку
7. Переглянути синоніми для словникового терміну (GET api/words/{words_id}/synonyms)
    - Метод: GET
	- Опис: Повертає список синонімів для вказаного терміну
	- Параметри: ID терміну
	- Відповідь: Список синонімів або порожній список, якщо синоніми відсутні
8. Додати власне визначення до словникового терміну (POST api/words/{words_id}/{definition})
    - Метод: POST
    - Опис: Додає власне визначення або пояснення до вказаного терміну
    - Параметри: ID терміну та текст визначення
    - Відповідь: Додане визначення або повідомлено про помилку
9. Додати тег до словникового терміну (POST /words/{tag_name})
    - Метод: POST
	- Опис: Створює нову категорію термінів або оновлює існуючу
	- Параметри: Об’єкт категорії
	- Відповідь: Створена або оновлена категорія або повідомлено про помилку
10. Додати або оновити словниковий термін (POST api/words/{words_id}/)
    - Метод: POST
	- Опис: Додає новий термін до бази даних або оновлює існуючий
	- Параметри: Об’єкт терміну
	- Відповідь: Доданий або оновлений термін, або повідомлено про помилку

## System behaviour

### Реєстрація та авторизація користувачів
  Користувач може створити обліковий запис, надавши інформацію про себе (ім'я, email, пароль) у формі реєстрації.
  Після успішної реєстрації користувач отримає підтвердження на email та зможе увійти до системи за допомогою логіна та пароля.
  Система зберігає інформацію про користувачів у безпечній базі даних.
  Користувач може вийти зі свого облікового запису в будь-який час.
### Пошук слів
  Користувач може шукати слова за їх назвою, вводячи текст у поле пошуку.
  Система шукає слова в базі даних за їх назвою та повертає список відповідних результатів.
  Користувач може вибрати слово зі списку результатів, щоб переглянути його детальну інформацію.
  Користувач може шукати слова за категорією, вибравши категорію з списку категорій.
  Система шукає слова в базі даних за їх категорією та повертає список відповідних результатів.
### Збереження улюблених слів
  Користувач може зберегти слово до своїх улюблених, натиснувши кнопку "Зберегти" на сторінці детальної інформації про слово.
  Збережені слова додаються до списку улюблених користувача.
  Користувач може переглянути список своїх улюблених слів у будь-який час.
  Користувач може видалити слово зі списку улюблених, натиснувши кнопку "Видалити" на сторінці детальної інформації про слово.
### Додавання коментарів та відгуків
  Користувач може додати коментар до слова, ввівши текст коментаря та натиснувши кнопку "Відправити".
  Коментарі додаються до сторінки детальної інформації про слово.
  Інші користувачі можуть переглянути коментарі та залишити свої відгуки.
  Користувач може видалити свій коментар, натиснувши кнопку "Видалити" під коментарем.
### Перегляд синонімів
  Користувач може переглянути синоніми для слова, натиснувши кнопку "Синоніми" на сторінці детальної інформації про слово.
  Система шукає синоніми для слова в базі даних та повертає список відповідних результатів.
  Користувач може вибрати синонім зі списку результатів, щоб переглянути його детальну інформацію.
### Додавання власних визначень
  Користувач може додати власне визначення або пояснення до слова, ввівши текст визначення та натиснувши кнопку "Відправити".
  Власні визначення додаються до сторінки детальної інформації про слово.
### Управління категоріями (тегами)
  Адміністратор:
  Може створювати нові категорії (теги) для слів.
  Може редагувати назви та описи категорій.
  Може видаляти категорії.
  
  Користувач:
  Може переглядати список доступних категорій.
  Може шукати слова за категорією.
  Не може створювати, редагувати або видаляти категорії.
### Додавання та оновлення слів
  Адміністратор:
  Може додавати нові слова до бази даних.
  Може редагувати інформацію про існуючі слова (назву, опис, категорію, синоніми).
  Може видаляти слова з бази даних.
  
  Користувач:
  Не може додавати нові слова до бази даних.
  Може редагувати інформацію про існуючі слова з дозволу адміністратора.
  Не може видаляти слова з бази даних.
