# Setting Django Menggunakan Python 3.12 di Ubuntu 22.04

Ini cara memulai proyek Django Framework menggunakan Python 3.12 di Ubuntu 22.04 (Zorin OS 16).

## 1. Instalasi Python 3.12

Lakukan di terminal sebaris demi sebaris!

```
sudo apt update
sudo apt upgrade
sudo apt install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update
sudo apt install python3.12
```

Konfirmasi instalasi dengan:

```
python3.12 -V
pip3.12 -V
```

## 2. Instalasi Django

Lakukan perintah berikut baris demi baris!

```
# Bikin direktori, nama terserah. Dan masuk ke direktori tersebut
mkdir django-project
cd django-project

# buat .env
python3.12 -m venv .env

# aktifkan .env
source .env/bin/activate

# Instalasi django, pastikan sudah muncul ada (.env) di terminal setelah perintah di atas
python -m pip install Django

# Install driver untuk PostgreSQL
python -m pip install psycopg
```

## 3 Instalasi PostgreSQL

