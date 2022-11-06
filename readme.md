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

### Условия тестирования

> В таблице users более 100 000 записей

##### Список пользователей по имени Ivan

```mongodb
db.users.createIndex( { first_name: 1 } );
db.users.aggregate([
    {
        $match: {
            first_name: "Ivan"
        }
    }
]);
```

Без индекирования 065 ms
С индексированием 027 ms

##### Сумма возрастов пользователей по имени Ivan

```mongodb
db.users.createIndexes([{"first_name" : 1}, {"age": 1}])
db.users.aggregate([
    {
        $match: {
            first_name: "Ivan"
        }
    },
    {
        $group: { _id: "$first_name", total: { $sum: "$age" }}
    }
]);
```

Без индекирования 081 ms
С индексированием 023 ms

##### Пользователи с тегом только A

```mongodb
db.users.createIndex( { tags: 1 } );
db.users.aggregate([
    {
        $match: {
            tags: ["A"]
        }
    },
]);
```

Без индекирования 068 ms
С индексированием 024 ms

##### Пользователи с тегом A на первом уровне вложенности

```mongodb
db.users.createIndex( { tags: 1 } );
db.users.aggregate([
    {
        $match: {
            tags: "A"
        }
    }
]);
```

Без индекирования 066 ms
С индексированием 023 ms
