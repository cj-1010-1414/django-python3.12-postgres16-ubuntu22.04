# Setting Django Menggunakan Python 3.12 di Ubuntu 22.04

Ini cara memulai proyek Django Framework menggunakan Python 3.12 di Ubuntu 22.04 (Zorin OS 16).

## 1. Instalasi Python 3.12

Lakukan di terminal sebaris demi sebaris!

```
kamu@komputermu:~$ sudo apt update
kamu@komputermu:~$ sudo apt upgrade
kamu@komputermu:~$ sudo apt install software-properties-common
kamu@komputermu:~$ sudo add-apt-repository ppa:deadsnakes/ppa
kamu@komputermu:~$ sudo apt update
kamu@komputermu:~$ sudo apt install python3.12
```

Konfirmasi instalasi dengan:

```
kamu@komputermu:~$ python3.12 -V
kamu@komputermu:~$ pip3.12 -V
```

## 2. Instalasi Django

Lakukan perintah berikut baris demi baris!

```
# Bikin direktori, nama terserah. Dan masuk ke direktori tersebut
kamu@komputermu:~$ mkdir django-project
kamu@komputermu:~$ cd django-project

# buat .env
kamu@komputermu:~$ python3.12 -m venv .env

# aktifkan .env
kamu@komputermu:~$ source .env/bin/activate

# Instalasi django, pastikan sudah muncul ada (.env) di terminal setelah perintah di atas
(.env)kamu@komputermu:~$ python -m pip install Django

# Install driver untuk PostgreSQL
(.env)kamu@komputermu:~$ python -m pip install psycopg
```

## 3. Instalasi PostgreSQL 16

Ini adalah instalasi Postgres yang digunakan secara lokal. Tidak menerima koneksi jarak jauh dari IP berbeda.

```
kamu@komputermu:~$ sudo apt install gnupg2 wget vim
kamu@komputermu:~$ sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
kamu@komputermu:~$ curl -fsSL https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/postgresql.gpg
kamu@komputermu:~$ sudo apt update

# instalasi Postgres
kamu@komputermu:~$ sudo apt install postgresql-16 postgresql-contrib-16

# mulai servis
kamu@komputermu:~$ sudo systemctl start postgresql
kamu@komputermu:~$ sudo systemctl enable postgresql

# cek versi
kamu@komputermu:~$ psql --version

# Buka koneksi sebagai pengguna root
kamu@komputermu:~$ sudo -u postgres psql

# Ganti passwordnya
postgres=# ALTER USER postgres PASSWORD 'PassworMuSendiri@69';

# Buatkan database untuk django.
postgres=# create database namadatabase;

# Bikin pengguna database 'namadatabase'
postgres=# create user namapengguna with encrypted password 'passwordpengguna';

# Berikan perizinan 'namapengguna' untuk menggunakan 'namadatabase'
postgres=# grant all on database namadatabase to namapengguna;
postgres=# alter database namadatabase owner to namapengguna;
postgres=# grant usage, create on schema public to namapengguna;

# berikan akses django untuk membuat database untuk tes
postgres=# alter user django createdb;
```

## 4. Penutup

Beres!
