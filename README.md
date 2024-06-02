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
