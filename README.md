## «Етапи компіляції С-програм та автоматизація побудови С-програм»

### 2.1 Побудова програми з’єднання з СКБД PostgreSQL на основі монолітної С-програми

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/1b10239f-39e7-4650-8630-fb884008b7fc)

2.1.1 Встановити в ОС Linux програмний пакунок libpq-dev.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/6d5db348-39b1-4b3d-ab56-1bee7ee7b110)

2.1.2 Підключитись до ОС від імені користувача postgres, який є адміністратором
СКБД PostgreSQL та для якого не буде вимагатися пароль під час підключення до БД.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/e510a730-4c75-4e8b-8bd2-1f9ea27dfb4e)

2.1.3 Створити C-програму з назвою «db_connect.c», яка:
- встановлює з`єднання із СКБД PostgreSQL;
- під час з’єднання використовує назву БД з попередньої лабораторної роботи та
ім’я користувача postgres СКБД PostgreSQL, які вбудовані у програмний код;
- обробляє результат з’єднання (успішне та помилкове), виводячи на екран
відповідні повідомлення, які враховують назву БД;
- увесь програмний код розміщується лише у функції main.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/dcb79155-8afa-45e1-9530-d6499f2e1421)

2.1.4 Скомпілювати С-програму, враховуючи каталоги з header-файлами та
бібліотеками СКБД PostgreSQL.
Перевірити роботу executable-файла.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/10cc8f3c-d1fc-4784-90a0-85b0220a5aee)

2.1.5 Створити C-програму з назвою «db_connect_param.c», яка повторює всі дії C-
програми з назвою «db_connect.c», але назву бази даних та ім’я користувача програма
повинна брати як параметри командного рядку.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/848d6f7e-134c-4139-a890-810010ee1525)

2.1.6 Скомпілювати С-програму, враховуючи каталоги з header-файлами та
бібліотеками СКБД PostgreSQL.
Перевірити роботу executable-файла за двома варіантами назви БД: правильна назва
БД та будь-яка неправильна назва БД.

### 2.2 Побудова програми з’єднання з СКБД PostgreSQL за модульним принципом програмування

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/ac084c04-06bb-4774-9686-51a11f7280c2)

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/3c50c93d-241e-4910-9cad-0522c5caa39d)

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/8e32fbf1-8c49-412a-8759-6f594af60168)

2.2.1 Змінити код С-програми, враховуючи модульний принцип програмування:
- створити С-файл з назвою «connect_назва таблиці.c», який містить програмний
код з’єднання із СКБД PostgreSQL у вигляді функції з назвою «connect_назва таблиці», де
«назва таблиці» - назва реляційної таблиці з попередньої лабораторної работи;
- створити header-файл за шаблоном «назва таблиці.h» та додати до файлу
декларацію створеної функції;
- створити С-файл з назвою «назва таблиці.c», який містить main-функцію з
викликом функції з назвою «connect_назва таблиці».

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/3f9307cf-08a9-4b8a-acd7-ad2d57ab0adc)

2.2.2 Побудувати executable-файл.
Перевірити роботу executable-файла.

### 2.3 Побудова програми з’єднання з СКБД PostgreSQL через команду make

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/46294fb6-b85d-4bf8-85be-574b9ed4a774)

2.3.1 Створити Makefile, який містить наступний опис мети:
- мета створення object-файлу з назвою «connect_назва таблиці.o»;
- мета створення object-файлу з назвою «назва таблиці.o»;
- мета створення executable-файлу з назвою «назва таблиці».

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/933de3ed-9645-4a5c-8ac5-70543df5f45f)

2.3.2 Викнати команду make для побудови програми.

### 2.4 Побудова програми додавання рядку реляційної таблиці

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/4d5383d6-3a75-4eda-8e09-8108ac2025c6)

2.4.1 Створити файл як програмний модуль з назвою «add_назва таблиці.с» із
описом функції додавання рядку реляційної таблиці, яка повинна містити:
- команди транзакції (START TRANSACTION, LOCK TABLE назва таблиці ...,
INSERT INTO назва таблиці ..., COMMIT);
- повідомлення про результат виконання кожної команди.
Команду INSERT INTO створити за прикладом з попередньої лабораторної роботи.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/e0be5b02-2f97-4cdf-ab01-e1d1b9d581a6)

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/534b47e2-06e9-4324-9e82-620edfec521f)

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/55691954-5a33-4587-9ce5-bf24eef07f9c)

2.4.2 Оновити раніше створені файли:
- додати до файлу «назва таблиці.h» декларацію нової функції;
- виконати виклик нової функції із main-фукції файлу «назва таблиці.c»
- додати опис нової мети у файл Makefile

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/0c76a803-f59b-41a1-a880-7ad42b45dd56)

2.4.3 Скомпілювати С-файли програмних модулів командою make.

### 2.5 Побудова програми перегляду рядків реляційної таблиці

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/1cb4f9bd-40d7-4ab7-9797-2106215edb48)

2.5.1 Створити файл як програмний модуль з назвою «get_назва таблиці».с із описом
функції перегляду рядків реляційної таблиці, яка повинна містити:
- команди транзакції (START TRANSACTION, LOCK TABLE назва таблиці ...,
SELECT ... FROM назва таблиці ..., COMMIT);
- повідомлення про результат виконання кожної команди.
Команду SELECT ... FROM створити за прикладом з попередньої лабораторної
роботи.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/e7d02370-5b53-4d23-a5d0-d217f428d2f3)

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/c2b888c2-15e0-43e7-afb0-6b583f64793a)

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/a35fc1da-9bb4-40e1-b6af-2fcacf9a963f)

2.5.2 Оновити раніше створені файли:
- додати до файлу «назва таблиці».h декларацію нової функції;
- виконати виклик нової функції із main-фукції файлу «назва таблиці».c
- додати опис нової мети у файл Makefile

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/1e9538db-799e-447a-b1dc-c161e1eabc38)

2.5.3 Скомпілювати С-файли програмних модулів командою make.
Перевірити роботу executable-файла.

### 2.6 Додаткове налаштування процесу керування файлами через команду make

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/b99d044d-1331-4bf0-81c6-0ebda8af4764)

2.6.1 Додати до файлу Makefile наступні описи мети:
install – копіювання executable-файлу до каталогу bin домашнього каталогу
користувача postgres, наприклад, /var/lib/postgresql/bin/ (попередньо створити такий
каталог);
clean – видалення всіх object-файлів та executable-файлу.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/84dc0705-b79e-464b-98be-2f95c9e72f51)

2.6.2 Виконати команду make з метою clean.
Перевірити відсутність всіх object-файлів та executable-файлу.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/b2475e3f-7b6a-4223-b68a-2ff623e2efb8)

2.6.3 Скомпілювати С-файли програмних модулів командою make.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/32b80d4d-a7b2-417c-a939-5eee69f39b5d)

2.6.4 Виконати команду make з метою install.
Перевірити наявність executable-файлу у відповідному каталозі.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/a8fb34fe-177e-436d-aa4e-58515a173922)

Змін в файлах не було, компіляція не відбулася.

2.6.5 Повторно скомпілювати С-файли програмних модулів командою make. Надати
висновки щодо повідомлення команди.

### 2.7 Огляд етапів побудови С-програми GNU-компілятором GCC

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/9049fc6e-6035-4218-8fe5-4f3f171a1ef9)

2.7.1 Виконати prepocessing-етап для вказаного файлу, зберігши результат у файлі
«назва таблиці.i».

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/15ec8db2-f358-45e4-9301-38dc4561fe6c)

2.7.2 Виконати compilation-етап для файлу «назва таблиці.i», зберігши результат у
файлі «назва таблиці.s».

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/77c08cc3-bb69-4604-bbc7-b0b69aeb1cea)

2.7.3 Повторити compilation-етап для файлу «назва таблиці.i» з оптимізацію
програмного коду, зберігши результат у файлі «назва таблиці_opt.s», та визначити відсоток
зменшення кількості рядків після оптимізації.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/1fed4775-ce5c-499a-8739-42cbceb19632)

2.7.4 Виконати assembly-етап для файлу «назва таблиці.i» та зберегти результат у
object-файлі «назва таблиці.o».

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/34f64daf-29e4-4d19-869d-3bc0e487c40e)

2.7.5 Визначити командний рядок виконання linking-етапу для файлу «назва
таблиці.o».

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/55a8d210-ce83-44df-9915-f1d4d9bd638e)

2.7.7 Переглянути список файлів динамічних бібліотек, пов’язаних зі створеним
executable-файлом.

-----------------------------------------------------------------------------------------------------

## «Програмування міжпроцесної взаємодії з використанням каналів, черг повідомлень та програмування багатопоточної взаємодії»

### 2.1 Використання черг повідомлень для процесів, які взаємодіють з однією БД під керуванням серверу СКБД PostgreSQL

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/52259265-4bc4-4ef4-902d-90537349a0e7)

2.1.1 Підключитись до ОС від імені користувача postgres.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/6e33aff4-5164-49f7-a386-e230696aba93)

2.1.2 Забезпечити обмін повідомленням між двома процесами-копіями серверів
СКБД PostgreSQL, використовуючи команду LISTEN для програми-споживача та команду
NOTIFY для програми-постачальника через утиліту psql та враховуючи, що:
- назва черги повідомлень співпадає з вашим прізвищем в транслітерації,
наприклад, blazhko;
- рядок повідомлення = "Hello, process of Surname”, наприклад, "Hello, process of
Blazhko”;
- у псевдотерміналі програми-постачальника отримати PID процесу-копії серверу
СКБД;
- у псевдотерміналі програми-споживача отримати перелік назв черг повідомлень,
до яких програма

### 2.2 Програмна реалізація неіменованих каналів

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/9e96838f-a21d-4665-bc64-b6de4e30ad5c)

2.2.1 Створити програму на мові С з назвою pipe_read яка виконує дії:
- отримує повідомлення з неіменоваго каналу з використанням значення, яке
передано до програми через аргумент командного рядку;
- виводить на екран повідомлення типу "I'm child process of Surname with pid=",
наприклад, " I'm child process of Blazhko with pid=" зі значенням свого PID;
- виводить на екран повідомлення, в якому вказано розмір повідомлення,
отриманого раніше з каналу.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/c5f3e141-976d-441d-aa5a-a96d7752a127)

2.2.2 Створити програму на мові С з назвою pipe_write, яка виконує дії:
- створює неіменований канал;
- створює child-процес, в якому завантажується новий програмний образ з
викликом програми pipe_read та її аргументом;
- parent-процес передає у канал повідомлення типу "The Laboratory Work of
Surname", наприклад, " The Laboratory Work of Blazhko";
- parent-процес виводить на екран повідомлення типу "I'm parent process of
Surname with pid=", наприклад, " I'm parent process of Blazhko with pid=" зі значенням свого
PID;
- parent-процес виводить на екран повідомлення, в якому вказано розмір
повідомлення, переданого раніше у канал.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/6814455a-96bb-4333-aa9a-e872ee7d5827)

2.2.3 Скомпілювати програми та перевірити їх роботу.

### 2.3 Робота з іменованими каналами через інтерпретатор командного рядку

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/d0fdf58a-a884-47c3-8cf2-58133aa4c83b)

2.3.1 Створити іменований канал з використанням команди mkfifo:
- назва каналу співпадає з вашим прізвищем у транслітерації;
- права доступу до каналу = можна лише читати та писати власнику та групі
власника.

Переглянути властивості створеного каналу як файлу.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/b7f19cba-1b2b-49a8-9263-c3b9e3df90ba)

2.3.2 Підключити до іменованого каналу процес, який буде в нього записувати за
командою, визначеною з таблиці за вашим варіантом.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/60f19229-8ec7-4907-87d9-a750331c945c)

2.3.3 Перейти до нового (2-го) псевдотерміналу роботи з ОС Linux та створити
процес, який буде читати зі створеного раніше каналу.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/648a85a4-93b4-4bea-b0d0-9b4aae8e6c2a)

2.3.4 Видалити іменований канал.

### 2.4 Програмна реалізація іменованих каналів

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/2724dfd8-466b-4451-a1d8-5c976eb9d4c3)

2.4.1 Створити програму на мові С, яка буде створювати іменований канал та
виконувати дії у відповідності з пунктами попередніх завдань 2.3.1, 2.3.2, 2.3.4

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/23b0ec41-24de-4c7e-b124-ca0b59cf5b8c)

2.4.2 Скомпілювати програму та перевірити її роботу, враховуючи пункт завдання
2.3.3.

### 2.5 Програмування черги повідомлень

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/99df509c-3124-40f2-8285-b1769796a795)

2.2.1 Створити програму на мові С з назвою msgsnd, яка виконує дії:
- створює чергу, номер якої = (1000 + 100*m+n), де m = {1,2,3,4,5,6} – остання
цифра у номері вашої групи, n – номер вашого варіанту (важливо, щоб цей номер ще не
використовувався іншими студентами, інакше можлива помилка у зв`язку із обмеженням
прав доступу на вже кимось створену чергу, тоді оберіть інший номер);
- передає до черги повідомлення типу "Message from Surname", наприклад,
"Message from Blazhko";

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/44d655fa-b64b-48af-8c07-5b7f0cd56382)

2.2.2 Створити програму на мові С з назвою msgrcv, яка отримує повідомлення з
черги , номер якої =(1000 + 100*m+n), де m ={1,2,3,4,5,6} – остання цифра у номері вашої
групи, n – номер вашого варіанту.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/f32cb2a8-e4ad-45a6-866a-94dc42fda6db)

2.2.3 Скомпілювати програми та перевірити їх роботу.

### 2.6 Програмування потоків

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/b4766214-e65c-4a8c-a5b4-51506dcfab35)

2.6.1 Створити програму на мові C за прикладом з рисунку 12, в якій функції двох
потоків:
- виводять на екран повідомлення, які враховують ваше прізвище транслітерацією
та номер функції;
- повідомлення виводиться (n+5) разів, де n – номер варіанту.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/8d53ad3a-f698-403b-ae5a-4da7e9870b50)

  2.6.2 Скомпілювати програму та перевірити її роботу.


-----------------------------------------------------------------------------------------------------

## «Програмування безпечної міжпроцесної та міжпотокової взаємодії в Unix-подібних ОС»

### 2.1 Аналіз наявності змагань у міжпотоковій взаємодії на основі алгоритму
«Змінні блокування»

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/b237d53c-1251-4eb5-9491-9c3735696532)

2.1.1 В лабораторній роботі No11 було використано таблицю реляційної бази даних.
Для проведення експериментів над механізмами взаємного виключення декількох потоків
під час паралельного доступу до структурної змінної з використанням алгоритму «Змінні
блокування» створити С-програму за прикладом на рисунку 14 та назвою за шаблоном
«db_lockvars_ваше_прізвище.c», яка містить:
- опис структурної змінної, який відповідає структурі реляційної таблиці;
- налаштування роботи двох потоків через окремі функції з назвою T1,T2;
- структури даних роботи алгоритму «Змінні блокування» в програмному коді
потокових функцій;
- кожна функція повинна:
    - спочатку виконати операцію читання значення будь-якого елемента структури;
    - в подальшому виконати операцію зміни значення вказаного елемента структури;
- функції затримки для імітації паралельної роботи потоків.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/6c082cba-405e-42f1-b26a-57a18c5357fd)

2.1.2 Скомпілювати програму та перевірити її роботу. Зробити висновок щодо
наявності або відсутності змагань потоків.

### 2.2 Аналіз наявності змагань у міжпотоковій взаємодії на основі алгоритму «Строге чергування»

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/9e6478e2-c50b-4535-a3a9-b5c378c2f0bd)

2.2.1 Для проведення експериментів над механізмами взаємного виключення
декількох потоків під час паралельного доступу до структурної змінної з використанням
алгоритму «Строге чергування» створити С-програму з назвою за шаблоном
«db_strictwatching_ваше_прізвище.c», яка містить:
- опис структурної змінної, який відповідає структурі реляційної таблиці;
- налаштування роботи двох потоків через окремі функції з назвою T1,T2;
- структури даних роботи алгоритму «Строге чергування» в програмному коді
потокових функцій;
- кожна функція повинна:
    - спочатку виконати операцію читання значення будь-якого елемента структури;
    - в подальшому виконати операцію зміни значення вказаного елемента структури;
- функції затримки для імітації паралельної роботи потоків.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/151e5edb-636c-462d-a1b5-fdf4206e4cb0)

2.2.2 Скомпілювати програму та перевірити її роботу. Зробити висновок щодо
наявності або відсутності змагань потоків.

### 2.3 Аналіз наявності змагань у міжпотоковій взаємодії на основі алгоритму Петерсона

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/bcda5f14-6ed9-4260-b4d8-e500ef0ac498)

2.3.1 Для проведення експериментів над механізмами взаємного виключення
декількох потоків під час паралельного доступу до структурної змінної з використанням
алгоритму Петерсона створити С-програму з назвою за шаблоном
«db_peterson_ваше_прізвище.c», яка містить:
- опис структурної змінної, який відповідає структурі реляційної таблиці;
- налаштування роботи двох потоків через окремі функції з назвою T1,T2;
- кожна функція повинна:
    - спочатку виконати операцію читання значення будь-якого елемента структури;
    - в подальшому виконати операцію зміни значення вказаного елемента структури;
- структури даних роботи алгоритму Петерсона в програмному коді потокових
функцій;
- функції затримки для імітації паралельної роботи потоків.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/4a16f584-3e7c-4f30-8ad6-01e6b69a4533)

2.3.2 Скомпілювати програму та перевірити її роботу. Зробити висновок щодо
наявності або відсутності змагань потоків.

### 2.4 Аналіз наявності змагань у міжпотоковій взаємодії на основі двійкового семафору

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/1020e266-816c-4747-a75a-831de52cb7d1)

2.4.1 Для проведення експериментів над механізмами взаємного виключення
декількох потоків під час паралельного доступу до структурної змінної з використанням
двійкового семафору створити С-програму з назвою за шаблоном
«db_semaphore2_ваше_прізвище.c», яка містить:
- опис структурної змінної, який відповідає структурі реляційної таблиці;
- налаштування роботи двох потоків через окремі функції з назвою T1,T2;
- кожна функція повинна:
    - спочатку виконати операцію читання значення будь-якого елемента структури;
    - в подальшому виконати операцію зміни значення вказаного елемента структури;
- назва семафору співпадає з вашим прізвищем транслітерацією;
- права доступу при відкритті семафору = можна читати, писати та виконувати
власнику та групі власника;
- функції керування семафором;
- функції затримки для імітації паралельної роботи потоків.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/a135a478-6092-48d9-9921-b4e76ad0d65c)

2.4.2 Скомпілювати програму та перевірити її роботу. Зробити висновок щодо
наявності або відсутності змагань потоків.

### 2.5 Аналіз наявності змагань у міжпотоковій взаємодії на основі м’ютексу

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/b12916a1-b8e8-4592-8cab-99130a19129c)

2.5.1 Для проведення експериментів над механізмами взаємного виключення
декількох потоків під час паралельного доступу до структурної змінної з використанням
м’ютексу створити С-програму з назвою за шаблоном «db_mutex_ваше_прізвище.c»:
- опис структурної змінної, який відповідає структурі реляційної таблиці;
- налаштування роботи двох потоків через окремі функції з назвою T1,T2;
- кожна функція повинна:
    - спочатку виконати операцію читання значення будь-якого елемента структури;
    - в подальшому виконати операцію зміни значення вказаного елемента структури;
- функції керування м’ютексом;
- функції затримки для імітації паралельної роботи потоків.

![image](https://github.com/Sergiy-Pats/ttt/assets/78663930/67bcc880-9d0a-45cd-a6c4-afa1c23683a9)

2.5.2 Скомпілювати програму та перевірити її роботу. Зробити висновок щодо
наявності або відсутності змагань потоків.
