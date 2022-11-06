# Домашняя работа 5

### Облако Яндекс

> https://console.cloud.yandex.ru/

##### Название инстанса:

> mongo-test1

##### IP адрес:

> 158.160.34.196

##### Пользователь

> root

##### Пароль

> 123

##### Строка подключения:

> mongodb://root:123@158.160.34.196:27017/otus?authSource=admin&readPreference=primary&appname=MongoDB%20Compass&directConnection=true&ssl=false

---

##### БД

> otus

##### Коллекция users

> \_id: ObjectId
> first_name: String
> last_name: String
> job: ObjectId
> status: String
> age: Int32
> tags : [String]

##### Коллекция jobs

> \_id: ObjectId
> name: String

##### Список пользователей по имени Ivan

db.users.aggregate([{
$match: {
first_name: "Ivan"
}
}]);
Без индекирования 019 ms

##### Сумма возрастов пользователей по имени Ivan

db.users.aggregate([
{
$match: {
first_name: "Ivan"
}
},
{
$group: { _id: "$first_name", total: { $sum: "$age" }}
}
]
);

##### Пользователи с тегом только A

db.users.aggregate([
{
$match: {
tags: ["A"]
}
},

    ]

);

##### Пользователи с тегом A на первом уровне вложенности

db.users.aggregate([
{
$match: {
tags: "A"
}
},

    ]

);

##### Пользователи с подробным данными о работе

db.users.aggregate([
{ $lookup:{
from: "jobs",
localField: "job",
foreignField: "_id",
as: "job"
} }
]);
