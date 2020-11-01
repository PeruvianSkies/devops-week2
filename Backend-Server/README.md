## Application Server for Backend

Sebelumnya saya sudah membuat instance AWS untuk server backend dengan spesifikasi sebagai berikut
``` 
OS  : Ubuntu Server 18.04
CPU : 1 Core
RAM : 2 gb
HDD : 15 gb
```
![imagename](assets/back1.png)


Ketika sudah masuk ke dalam server backend clone repository yang sudah di fork pada github.com menggunakan SSH yang sudah di konfigurasi sebelumnya

> `$ git clone git@github.com:PeruvianSkies/dumbplay.git`

![imagename](assets/back3.png)

Install nodeJS 10, npm sequelize dan pm2
![imagename](assets/back4.png)
![imagename](assets/back5.png)

Install MySQL-client agar bisa melakukan migrasi database

>`$ sudo apt-get install mysql-client`

Kemudian saya mencoba koneksi ke console MySQL dengan user dan password yang sudah saya konfigurasikan pada server database

> `$ mysql -h 172.31.58.125 -u peruvian1 -p`

![imagename](assets/back2.png)

Create database aplikasi

> `mysql> create database dumbplay;`

![imagename](assets/back6.png)

Ubah konfigurasi pada file config.json

![imagename](assets/back10.png)

Posisikan sudah berada pada direktori Backend lakukan migrasi database dengan sequelize

>`$ sequelize db:migrate`

![imagename](assets/back7.png)

Copy file .env 

>`$ cp .env-copy .env`

![imagename](assets/back8.png)

Lakukan NPM install 

>`$ npm install`

![imagename](assets/back9.png)

Jalankan pm2 agar aplikasi tetap berjalan

>`$ pm2 start ecosystem.config.js`

![imagename](assets/back11.png)

