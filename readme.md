# Learn Docker

mengambil image 

```
docker pull image
```


untuk menjalankan image 

```
docker run <namaimage>
```

menjalankan server nginx

```
docker run -it --rm -d -p port_bind:port_image --name name-image image

contoh:

docker run -it --rm -d -p 8080:80 --name web nginx

atau bisa dengan menambahkan volumes

docker run -it --rm -d -p port_bind:port_image -v directory_local:directory_container image

keterangan:

-d (daemon) = menjalankan proses secara backgound service

-p (port) = port untuk mengatur bind port

-v (volumes) = untuk mengatur mount directory pada local ke container

docker run -it --rm -d -p 8080:80 --name web -v E:\Programming\Web\boostrap:/usr/share/nginx/html nginx
```





## Docker Compose

untuk menggunakkan compose, terlebih dahulu buat file docker-compose.yml.

file ini nantinya yang akan dijalankan oleh dockernya nantinya

bedanya docker-compose.yml dan dockerfile yaitu terletak pada fungsinya

docker-compose.yml digunakkan untuk menjalankan image apa saja yang digunakkan untuk aplikasinya

sedangakan 

dockerfile digunakkan untuk mengatur image yang kita buat nantinya. 

bagaimana aplikasi kita dijalankan, image apa yang dibutuhkan, folder mana yang akan dibutuhkan nantinya 

setelah kita membuild aplikasi kita menjadi image


Pada kali ini akan membahas docker-compose.yml

### RUN

```
docker-compose up -d

up : untuk membuat dan menjalankan container

-d : melakukan proses secara background
```


### Menghentikan container

untuk menghentikan terdapat dua cara yaitu dengan perintah **down** dan **down**

down : digunakan untuk untuk mengahapus semua kontainer, network, images dan volumes(untuk menggunakkan perintah ini hati hati)

stop : menghentikan service dari container

```
docker-compose stop <nama image>

apabila terdapat dua container yang berjalan bisa menggunakan perintah dibawah

docker-compose stop <nama image 1> <nama image 2>
```

## menjalankan container

```
docker-compose start <nama image/container>

atau juga misal ada 2 container yang ingin dijalankan

gunankan perintah dibawah

docker-compose start <nama image 1> <nama image 2>
```

## menghapus container

untuk mengahapus container terlebih dahulu hentikan service container

kemudian gunakkan perintah dibawah

```
docker-compose rm <nama container/image>
```


## Menampilkan container yang berjalan

```
docker-compose ps
`
