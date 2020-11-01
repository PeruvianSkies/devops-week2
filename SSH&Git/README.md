## SSH & Git

Ketika proses pembuatan instance selesai, kemudian kembali ke terminal untuk membuat **SSH-key**
   > `$ ssh-keygen -C "peruvian3@aws"`

![imagename](assets/git1.png)

Kemudian masuk ke direktori .ssh
   > `$ cd .ssh/`

Copy isi file id_rsa.pub
![imagename](assets/git2.png)

Buka github.com masuk setting dan klik **SSH-Key**
New SSH-Key kemudian masukkan paste isi file id_rsa.pub
![imagename](assets/git3.png)

Kembali ke terminal untuk cek konektivitas akun Github

> `$ ssh -T git@github.com`

![imagename](assets/git4.png)

Jika sudah terkoneksi buka github repository sgnd untuk fork aplikasi
Tunggu sampai proses fork ke repository pribadi berhasil

![imagename](assets/git5.png)
![imagename](assets/git6.png)


Kembali lagi ke terminal untuk melakukan clone repo

> `$ git clone git@github.com:PeruvianSkies/dumbplay.git`

![imagename](assets/git7.png)

Membuat sedikit perubahan pada file README.md

![imagename](assets/git8.png)

Kembali ke Terminal untuk melakukkan pull

> `$ git pull`

![imagename](assets/git9.png)

Membuat sedikit perubahan kembali pada file README.md

![imagename](assets/git10.png)

Kemudian saya lakukan commit repo

> `$ git add .`

> `$ git commit -m "edited file"`

![imagename](assets/git11.png)

Kemudian saya lakukan push repo

> `$ git push`

![imagename](assets/git12.png)