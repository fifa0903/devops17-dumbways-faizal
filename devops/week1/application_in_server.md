perbandingan antara monolith dan microservice?

jawab :

monolith merupakan bentuk arsitektur aplikasi yang terdiri dari 1 pusat database yang mencakup semua service

microservice merupakan bentuk aristektur aplikasi yang terdiri dari bagian" tersendiri dan tidak terpusat pada 1 database. setiap service memiliki bagian sendiri

jalankan wayshub-frontend pada node.js

jawab :

kita menganggap bahwa node.js sudah terinstall pada local tunneling

pertama tama kita git clone repository dari wayshub-frontend

git clone https://github.com/dumbwaysdev/wayshub-frontend

<img width="746" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/01965f55-7215-4dbe-8cc1-b268b809980b">

kita pindah ke folder wayshub-frontend cd wayshub-frontend/

kita bisa lihat bahwa sudah ada package.json dan package-lock.json sehingga tidak perlu set npm init -y

<img width="602" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/f30ec4b0-4421-4680-b7dc-7abcfe431686">

untuk melihat versi node yang digunakan saat ini

<img width="341" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/1c1cef3c-0998-410c-87f3-84214e01aff5">

jalankan npm run build dan tunggu dengan smpai selesai. kemudian untuk menjankan aplikasi ikuti petunjuk 

<img width="736" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/18bb971f-41e9-426e-8b43-398c93cae194">

install = npm install -g serve dan jalankan serve -s build untuk menjalankan aplikasi pada node.js 

<img width="942" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/119ee481-2e2b-4a35-97a7-ce38fc2a2e77">

kita bisa melihat hasilnya walaupun masih terdapat error karena masih ada package yang belum terinstall

<img width="943" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/0d22b90c-810e-4627-b4b0-3cd29ac32514">

kita install dulu package xsel

<img width="795" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/89db3e61-98d4-44a2-bc3d-6dfe2e85256f">

jalankan aplikasi lagi

<img width="569" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/7b89829a-fef6-40d8-a60b-400604e83509">

walaupun terdapat error tidak masalah kita tetap bisa menjalankan aplikasi

<img width="805" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/1fbc68c9-130c-4dd3-b935-cc05a25e739d">


jalankan aplikasi golang dan python menampilkan nama sendiri!

jawab :

1.  golang

buat folder terlebih dahulu menggunakan : mkdir golang dan pindah ke folder golang : cd golang/

kemudian install golang terlebih dahulu dengan :

wget https://golang.org/dl/go1.16.5.linux-amd64.tar.gz && sudo su

kemudian gunakan kode ini untuk close root :

rm -rf /usr/local/go && tar -C /usr/local -xzf go1.16.5.linux-amd64.tar.gz && exit

<img width="923" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/36e9cd4f-dd1b-471b-b94d-854fb75bbc90">

masuk ke .bashrc : sudo nano .bashrc dan pastekan : export PATH=$PATH:/usr/local/go/bin pada bagian paling bawah 

untuk mengecek dimana golangnya lihat ke folder /usr/local/go/bin

gunakan exec bash untuk refresh dan jalankan go version untuk mengecek golang

<img width="473" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/5290b736-ba99-420d-aa00-4351b6781314">

buat file .go dengan nano index.go

tulis nama kalian dengan kode dibawah

run dengan go run index.go

<img width="377" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/82fe7cd3-5b58-4e1c-872e-6a942b2ce40f">

<img width="348" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/2e9e58d6-a6cc-4ab8-9c1f-8d2de37868bf">

untuk build kalian bisa gunakan : go build index.go

kemudian run dengan ./index

<img width="345" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/96ea1ec3-f742-41cd-b126-9c1a83d2441d">


2.  python

untuk aplikasi python sebenarnya sudah terinstal pada ubuntu server namun packagenya belum ada sehingga perlu diinstall dengan

sudo apt install python3-pip

pip install flask

<img width="951" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/f61abea9-7fd7-40c8-8459-f50a0dbec6ad">

namun karena sudah pernah terinstal tampilan jadi seperti ini. kemudian buat file python dengan nano index.py dan masukkan nama seperti pada gambar

<img width="329" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/3d238ba6-7644-4733-9714-b1b7c1427911">

kemudian jalankan file dengan python3 index.py dan kita bisa melihat bahwa aplikasi berada pada port 5000

<img width="845" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/5e616984-f75d-4cd8-93b3-6acac192e48b">

<img width="326" alt="image" src="https://github.com/fifa0903/devops17-dumbways-faizal/assets/132969781/dfca4a26-9b41-48a1-b05a-d00e8e82411c">

