Додаток для вивчання англійської мови з допомогою anki-методу. Користувач щодня повинен заходити в додаток щоб перевірити свої знання.
- Реєстрація/авторизація
- Можливість створити групу карток з певною мовою (для початку тільки англійською)
- В цій групі має бути можливість додавання картки, на одній стороні якої написане слово іноземною мовою, на іншій - її переклад
	- картки повинні мати можливість зв'язуватись з іншими картками за декількома методами: "схожість за написанням слова іноземного слова", "схожість за тлумаченням з рідної мови", "однаковий переклад для рідної мови, з різними іноземними словами"
- Для кожної групи користувач повинен мати можливість увімкнути сповіщення про нагадування що треба навчатись, повинна бути реалізована можливість налаштування періодичності цих сповіщень, на даному етапі реалізувати сповіщення на електронну адресу.
- Після створення групи, для користувача повинен бути доступний режим роботи "тренування", під час якого йому показуватимуться картки з цієї групи.
	1. перед початком режиму "тренування", користувач повинен мати вибір, яка сторона картки йому буде показуватись, в майбутньому реалізувати змішаний режим
	2. Також повинен бути вибір з якою кількістю карток може бути почата сесія (наприклад: в групі 200 карток, користувач може обрати що одна сесія буде містити 20 карток із них)
	3. після того як користувач прочитав слово на картці, вона повинна повернутись щоб побачити переклад на іншій стороні.
	4. реалізувати меню після повертання картки, де користувач може обрати один з наступних варіантів: "переклав дуже легко", "переклав без проблем", "переклав з труднощами" та "не переклав", в залежності від цього, сформувати певну сесію, з статистичними даними. На основі цих статистичних даних в рамках однієї сесії реалізувати алгоритм де користувачеві попадатимуться картки в яких він найменше орієнтується.
	5. сесія повинна бути активна впродовж поточного дня, наступного дня - створитись нова
- Також для поточної групи повинен бути режим "перекласти речення із слів із цієї групи". Перед початком цього режиму користувач повинен вказати режим його роботи: формувати речення із іноземної мови та перекладати його на рідну, чи навпаки. Також повинно бути вказано кількість слів для формування, відповідно чим більша кількість слів тим важче буде речення.
	- Первинне формування повинно відбуватись через ChatGPT, для обох варіантів формування повинні бути використані різні промпти в залежності яка мова обрана.
	- Переклад сформованого речення повинен відбуватись із допомогою deepl.
	- Промпти для різних мов повинні бути сформовані заздалегідь та зберігатись в БД.
	- Також можна реалізувати функцію складності створеного речення, і його окремо вказувати в промпті.


## er-діаграма БД
![[anki-app-extended.png]]
[Діаграма на dbdesigner](https://dbdesigner.page.link/WBcextXt7HcXJidt6)