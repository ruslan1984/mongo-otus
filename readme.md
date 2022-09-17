# Домашняя работа 3

#### файл docker-compose.yaml

> version: "3.8"<br />
> services:<br /> &nbsp;&nbsp;mongo:<br /> &nbsp;&nbsp;&nbsp;&nbsp;image: mongo<br /> &nbsp;&nbsp;&nbsp;&nbsp;restart: always<br /> &nbsp;&nbsp;&nbsp;&nbsp;environment:<br /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br />MONGO_INITDB_ROOT_USERNAME: root<br /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br />MONGO_INITDB_ROOT_PASSWORD: example<br /> &nbsp;&nbsp;&nbsp;&nbsp;volumes:<br /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- ./db:/data/db<br /> &nbsp;&nbsp;mongo-express:<br /> &nbsp;&nbsp;&nbsp;&nbsp;image: mongo-express<br /> &nbsp;&nbsp;&nbsp;&nbsp;restart: always<br /> &nbsp;&nbsp;&nbsp;&nbsp;ports:<br /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 8081:8081<br /> &nbsp;&nbsp;&nbsp;&nbsp;environment:<br /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ME_CONFIG_MONGODB_ADMINUSERNAME: root<br /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ME_CONFIG_MONGODB_ADMINPASSWORD: example<br /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ME_CONFIG_MONGODB_URL: mongodb://root:example@mongo:27017/<br />

---

- старт: docker-compose up
- стоп: docker-compose down
