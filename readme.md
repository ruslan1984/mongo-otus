# Домашняя работа 4

### Облако Яндекс

> https://console.cloud.yandex.ru/

##### Название инстанса:

> mongo-2022-84923

##### IP адрес:

> 130.193.51.6

##### Пользователь

> root

##### Пароль

> 123

##### Строка подключения:

> mongodb://root:123@130.193.51.6:27017/otus?authSource=admin&readPreference=primary&appname=MongoDB%20Compass&directConnection=true&ssl=false

---

##### БД

> shop

##### Коллекция

> products

##### Структура

> \_id: ObjectId
> name: String
> price: Int32
> count: Int32

---

### Команды

##### Подключиться к БД

> use shop

##### Список продуктов

> db.shop.find()

##### Добавить запись

> db.products.insert({ name: "Горох", price: 15,count: 20 })

##### Добавить несколько записей

> db.products.insertMany([ { name: "Манка", price: 2, count: 23}, { name: "Картошка", price: 8, count: 25} ])

##### Удалить запись

> db.products.deleteOne({ \_id: ObjectId("63276de99f7330ba5c8b4074") })

##### Обновить запись

> db.products.update({ \_id: ObjectId("6327674353e647d3c7860d82") }, { $set: { count: 8 } })

### Выборка записей

##### Вывести запись с id 6327674353e647d3c7860d82

> db.products.find({\_id: ObjectId("6327674353e647d3c7860d82") })

##### Вывести запись с count больше 18

> db.products.find({"count" : {$gt: 18}})

##### Вывести запись с price меньше или равно 5

> db.products.find({"price" : {$lte: 5}})

##### Общее количество записей

> db.products.countDocuments()

##### Вывести количество записей с price меньше или равно 5

> db.products.count({"price" : {$lte: 5}})
