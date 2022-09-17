# Домашняя работа 3

#### файл docker-compose.yaml

> version: "3.8"
> services:
> &nbsp;&nbsp;mongo:
> &nbsp;&nbsp;&nbsp;&nbsp;image: mongo
> &nbsp;&nbsp;&nbsp;&nbsp;restart: always
> &nbsp;&nbsp;&nbsp;&nbsp;environment:
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;MONGO_INITDB_ROOT_USERNAME: root
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;MONGO_INITDB_ROOT_PASSWORD: example
> &nbsp;&nbsp;&nbsp;&nbsp;volumes:
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- ./db:/data/db
> &nbsp;&nbsp;mongo-express:
> &nbsp;&nbsp;&nbsp;&nbsp;image: mongo-express
> &nbsp;&nbsp;&nbsp;&nbsp;restart: always
> &nbsp;&nbsp;&nbsp;&nbsp;ports:
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 8081:8081
> &nbsp;&nbsp;&nbsp;&nbsp;environment:
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ME_CONFIG_MONGODB_ADMINUSERNAME: root
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ME_CONFIG_MONGODB_ADMINPASSWORD: example
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ME_CONFIG_MONGODB_URL: mongodb://root:example@mongo:27017/

---

- старт: docker-compose up
- стоп: docker-compose down
