## Reverse Proxy

Buka cloudflare.com dan tambahkan ip server backend

![imagename](assets/rev1.png)

Kembali ke server 1 untuk mengkonfigurasi proxy,
buat file .config baru di dalam direktori yang sama dengan file .config pada server frontend.
Untuk `server_name` arahkan ke domain api yang sudah dibuat sebelumnya, dan arahkan `proxy_pass` ke IP server backend dengan port `:5000`

![imagename](assets/rev2.png)

Buka browser untuk cek konektifitas

![imagename](assets/rev3.png)

## SSL Configuration

Sebelumnya saya ubah terlebih dahulu mode **Proxied** menjadi mode **DNS only** pada cloudflare
Kemudian copy Global API Key pada menu profile

![imagename](assets/rev4.png)

Kembali ke terminal server public untuk konfigurasi

Buat folder .secrets dan isikan folder tersebut dengan file cloudflare.ini untuk menyimpan Api key

Posisikan pada user **root**

>`$ sudo su`

>`# mkdir /root/.secrets`

>`# nano /root/.secrets/cloudflare.ini`

Isikan file tersebut dengan format berikut

dns_cloudflare_email = "putraasdasdasd@gmail.com"
dns_cloudflare_api_key = "global-apikey"

Berikan permission pada folder dan file tersebut agar hanya bisa diakses oleh **root**

>`$ sudo chmod 0700 /root/.secrets`

>`$ sudo chmod 0400 /root/.secrets/cloudflare.ini`

Terapkan SSL dengan perintah certbot

>`$ sudo certbot certonly --dns-cloudflare --dns-cloudflare-credentials /root/.secrets/cloudflare.ini -d tianputra.instructype.com,*.tianputra.instructype.com --preferred-challenges dns-01`

![imagename](assets/rev5.png)
![imagename](assets/rev6.png)

Edit file reverse proxy untuk server backend
Hapus pada bagian `listen [::]:443 ssl ipv6only=on;`

>`$ sudo nano /etc/nginx/dumbways/dumbplay.conf`

![imagename](assets/rev7.png)

Restart Nginx

>`$ sudo systemctl restart nginx.service`

***
***

Masuk server frontend untuk edit file `api.js`

>`$ sudo nano dumbplay/frontend/src/config/api.js`

Arahkan **baseURL** ke domain api dan tambahkan dengan `/api/v1`

![imagename](assets/rev8.png)

Restart pm2.

>`$ pm2 restart 0`

Sebelumnya saya sudah melakukan tes menggunakan aplikasi **Postman**

Berikut tampilan login pada browser

![imagename](assets/rev9.png)

SSL certificate untuk domain api

![imagename](assets/rev10.png)

