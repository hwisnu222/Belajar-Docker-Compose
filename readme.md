# Learn Docker

mengambil image 

```
docker pull image
```


untuk menjalankan image 

```
docker run <namaimage>
```

membuat container

```
docker container create --name <image> -p port_host:port_container
```

menjalankan server nginx

```
docker run -it --rm -d -p port_host:port_container --name name-image image

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

stop : menghentikan service dari container

```
docker-compose stop <nama image>

apabila terdapat banyak container yang berjalan bisa menggunakan perintah dibawah

docker-compose stop
```

## menjalankan container

```
docker-compose start
```

## menghapus container

untuk mengahapus container terlebih dahulu hentikan service container

kemudian gunakkan perintah dibawah

```
docker-compose rm <nama container/image>
```

atau bisa juga menggunakkan **down**.

dengan perintah ini semua network, volumes akan dibersihkan

```
docker-compose down
```


## Menampilkan container yang berjalan

```
docker-compose ps
```

## Membersihkan sampah container

untuk melihat storage yang tidak diperlukan, gunakkan perintah dibawah

```
docker system df

makan nanti akan menampilkan size yang tidak digunakkan
```

kemudian untuk menghapusnya gunakkan perintah 

```
docker system prune


untuk menghapus sekaligus volume yang tidak dipakai gunakkan perintah

docker system prune -a --volumes

maka semua volumes yang tidak dipakai akan dihapus
```

dengan menggunakkan perintah diatas makan semua image yang tidak digunakkan atau tidak dipakai oleh container lain akan dihapus
