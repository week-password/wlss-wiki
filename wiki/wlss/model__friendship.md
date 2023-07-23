[wiki](../../README.md) / [wlss](./index.md) /


# Модель. Дружба


# Дружба (Friendship)

Объект определяющий отношения "Дружбы" между пользователями А и Б. Содержит ссылки на **Аккаунты** этих пользователей.


### Аккаунт (Account)

Обязательный атрибут объекта **Дружба**. Хранит ссылку на **Аккаунт** пользователя у которого есть **Друг**.


### Друг (Friend)

Обязательный атрибут объекта **Дружба**. Хранит ссылку на **Аккаунт** пользователя, который является **Другом**.

Таким образом, **Другом** пользователя А является пользователь Б, если существует объект **Дружба**, в котором атрибут **Аккаунт** указывает на **Аккаунт** пользователя А, и атрибут **Друг** указывает на **Аккаунт** пользователя Б.

Дружба может быть только обоюдная, это значит что если существует объект **Дружба**(Аккаунт: А, Друг: Б), то обязательно должен существовать объект **Дружба**(Аккаунт: Б, Друг: А).

Невозможно существование объекта **Дружба**, у которого атрибуты **Аккаунт** и **Друг** ссылаются на один и тот же **Аккаунт** пользователя. Иными словами, пользователь не может дружить сам с собой.

Список **Друзей** связанных с **Аккаунтом** пользователя виден всем другим **Аккаунтам** пользователей системы.

Объекты **Дружбы** связывающие **Аккаунты** пользователей А и Б могут быть созданы, только если существует одна и только одна одобренная **Заявка в друзья**, ссылающаяся **Аккаунты** этих пользователей.


## Заявка в друзья (Friendship Request)

Объект представляющий собой заявку в друзья от **Аккаунта** пользователя А к **Аккаунту** пользователя Б. Существование этого объекта обозначает желание пользователя А добавить в друзья пользователя Б.


### Отправитель (Sender)

Обязательный атрибут объекта **Заявка в друзья**. Хранит ссылку на **Аккаунт** пользователя отправившего (создавшего) заявку.


### Получатель (Receiver)

Обязательный атрибут объекта **Заявка в друзья**. Хранит ссылку на **Аккаунт** пользователя, которому была отправлена заявка.


### Статус (Status)

Обязательный атрибут объекта **Заявка в друзья**. Хранит значение, обозначающее текущий статус заявки - **"На рассмотрении"** (Pending), **"Принята"** (Accepted), **"Отклонена"** (Rejected).

**Заявка в друзья** от **Аккаунта** пользователя A к **Аккаунту** пользователя Б не может быть создана, если выполняется хотя бы одно из условий:
- существует неотклонённая **Заявка в друзья** связывающая **Аккаунты** пользователей А и Б
- существует хотя бы один объект **Дружба** связывающий **Аккаунты** пользователей А и Б

**Заявка в друзья** не может указывать на два одинаковых **Аккаунта** (иными словами пользователь не может создать **Заявку в друзья** к самому себе).

Существовние более чем одной **Заявки в друзья** связывающей **Аккаунты** пользователей А и Б невозможно. Если существует отклонённая **Заявка в друзья** связывающая Аккаунты пользователей А и Б, то при создании новой **Заявки** старая (отклонённая) удаляется.

Если **Заявка в друзья** связывающая **Аккаунты** пользователей А и Б, находится в статусе **"Одобрена"** (Accepted), то должны существовать два объекта **Дружбы** - **Дружба**(Аккаунт: А, Друг: Б) и **Дружба**(Аккаунт: Б, Друг: А).

***

> Ссылка на [обсуждение](https://github.com/week-password/wisher/discussions/11).