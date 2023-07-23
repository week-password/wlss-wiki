[wiki](../../README.md) / [wlss](./index.md) /


# Модель. Аккаунт


# Аккаунт (Account)

_Также может употребляться как "Аккаунт пользователя" в определённых контекстах, где нужна более литературная формулировка. При этом смысл определения "Аккаунт пользователя" тот же что и у определения "Аккаунт"._

Сущность, которая представляет идентитчность реального пользователя в системе. Используется для идентификации пользователя и совершения действий в системе от его имени.

Атрибуты **Аккаунта** пользователя не видны пользователям других **Аккаунтов** внутри системы.


### Логин (Login)

Обязательный атрибут **Аккаунта** пользователя.
Используется в качестве уникального читаемого идентификатора пользователя в системе. Например, `birthdaysgift`.
Не виден пользователям других **Аккаунтов** внутри системы, используется только для аутентификации и формирования url-ссылки на веб страницы связанные с пользователем этого **Аккаунта**.
Представляет из себя строку длиной от 1 до 50 символов (включительно). Допустимые символы - `A-Z`, `a-z`, `0-9`, `-`, `_`.


### Почта (Email)

Обязательный атрибут **Аккаунта** пользователя.
Используется для взаимодействия с пользователем вне системы. Например, активация и восстановление доступа пользователя к системе. Не виден пользователям других **Аккаунтов** внутри системы.
Представляет из себя строку длиной от 5 до 200 символов (включительно), удовлетворяющую такому регулярному выражению: `.+@.+\..+`


### Пароль (Password)

Короткоживущий объект-значение. Используется для входа в систему. Например, `qwerty123`.
Представляет из себя строку длиной от 8 до 500 символов (включительно). Допустимые символы - любые.
**Пароль** не хранится внутри системы. Система хранит только **Хэш** этого пароля. Данный объект-значение используется только для валидации и передачи текста пароля внутри системы - от клиентского приложения к серверу.


### Хэш Пароля (Password Hash)

Объект, являющийся обязательным атрибутом сущности **Аккаунта**.
Используется для проверки **Пароля** пользователя в системе во время аутентификации.


**Значение (Value)**

Обязательный атрибут **Хэша Пароля**.
Используется для хранения значения **Хэша Пароля** от **Аккаунта** пользователя.
Представляет из себя строку сгенерированную одним из алгоритмов хэширования.


**Алгоритм (Algorithm)**

Обязательный атрибут **Хэша Пароля**.
Используется для хранения алгоритма, с помощью которого был сгенерирован хэш. Это необходимо чтобы в дальнейшем можно было сгенерировать такой же хэш.
Представляет из себя строку из множества строк являющихся результатом работы алгоритма хэширования.


**Соль (Salt)**

Обязательный атрибут **Хэша Пароля**.
Используется для хранения соли, которая применялясь при хэшировании.
Представляет из себя сгенерированный uuid4 в виде строки.

***

> Ссылка на [обсуждение](https://github.com/week-password/wisher/discussions/7).