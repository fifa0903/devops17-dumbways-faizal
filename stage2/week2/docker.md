pertama tama kita deploy aplikasi seperti biasa dan kemudian pastikanm file frontend dan backend berjalan dengan lancar dan atur reverse proxy nya

<img width="960" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/bddde919-085e-4f4e-8e8b-20310d484d26">

<img width="960" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/44c8f6eb-7b42-4f16-b65f-04ade11c93cd">

<img width="956" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/b929f01b-356e-4557-9930-892c6932c079">

kemudian install docker

<img width="458" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/cbbf57c0-82e8-4aba-9c1f-ced2ba528d4b">

gunakan sudo usermod -aG docker (user) untuk meringkas command sudo pada docker
 
<img width="960" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/a4ca079b-fe1d-4659-9335-a86aba1b2fd5">

masuk ke folder wayshub-frontend dan buat Dockerfile menggunakan nano Dockerfile

```
FROM node:14.21.3-alpine
WORKDIR /app
COPY . .
RUN npm install
EXPOSE 3000
CMD ["npm", "start"]
```

<img width="960" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/5d4c7d60-bce0-435e-b5f8-971daa7daa1c">

pull image mysql ke docker

<img width="955" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/eaa0e93e-c884-42e3-88bb-658c187dba3b">

buat database dengan compose mysql kemudian masuk ke mysql on top docker dan grant all user dengan docker exec -it wayshub-db

```
version: "3.8"
services:
    db:
      image: mysql
      container_name: wayshub-db
      expose:
        - 3306
      ports:
        - 3306:3306
      volumes:
        - ~/mysqldata:/var/lib/mysql
      environment:
        - MYSQL_ROOT_PASSWORD=fama1234
        - MYSQL_USER=fama
        - MYSQL_PASSWORD=fama1234
        - MYSQL_DATABASE=wayshub
```

<img width="960" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/2dd3b39a-1aeb-4972-bf5b-cb65a51a0edc">

buat dockerfile untuk backend yang berisikan migrasi data backend ke mysql dan run aplikasi dari backend

```
FROM node:14.21.3-alpine
WORKDIR /app

COPY . .
RUN npm install
RUN npm install sequelize-cli -g
RUN sequelize db:create

COPY migrations /migrations
RUN sequelize db:migrate

EXPOSE 5000
CMD [ "npm", "start" ]
```

<img width="960" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/a0280c9c-bb68-4dcf-a96d-ce9cf96d3f90">

pull image node 14.21.3

<img width="940" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/affc9ac2-32c1-4c8a-9a49-b3d27fea2ba0">

jalankan docker build -t fama-frontend . untuk membuat image dengan format wayshubfe pada directory wayshub-frontend

atau jalankan docker-compose.yml dengan docker compose up -d dan docker compose down untuk mematikan

```
version: "3.8"
services:
    db:
      image: mysql
      container_name: wayshub-db
      ports:
        - 3306:3306
      volumes:
        - ~/mysqldata:/var/lib/mysql
      environment:
        - MYSQL_ROOT_PASSWORD=fama1234
        - MYSQL_USER=fama
        - MYSQL_PASSWORD=fama1234
        - MYSQL_DATABASE=wayshub
    backend:
      depends_on:
        - db
      build: ./wayshub-backend
      container_name: wayshub-be
      stdin_open: true
      ports:
        - 5000:5000
    frontend:
      build: ./wayshub-frontend
      container_name: wayshub-fe
      stdin_open: true
      ports:
        - 3000:3000 
```

<img width="960" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/7e39aba4-286c-40e7-9def-113b2173e472">

masuk ke docker login dan ganti nama file dengan format docker tag <nama image> <username/namafile>

<img width="956" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/3297a6fe-218b-49a7-a4e8-bb04ae6d7b2c">

kemudian push dengan docker push <nama file>

<img width="918" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/aa924fd9-5af4-4cc1-bcc0-cfff2c6edc09">

<img width="945" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/d7279fce-71e8-4a17-980a-498bb25bf666">

kemudian jalankan certbot untuk mendapatkan secure link

<img width="959" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/f2b7830c-1b04-4d59-9b42-dccfe0ca99b5">


