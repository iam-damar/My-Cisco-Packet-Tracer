## Konfigurasi Router Dasar &middot; 
> Memahami tentang apa itu Router? dan apa fungsinya? dan bagaimana cara mengkonfigurasi Router?.

Router termasuk kedalam kelompok intermediary Devices, atau sebagai perangkat sekaligus jembatan bagi PC/komputer dalam berkomunikasi. <br/>
Khususnya Router ini dapat menghubungkan satu PC ke PC yang lain dengan Network Address yang berbeda.

Sehingga perbedaan antara switch dan router terletak pada Network Address akses komunikasi antar PC. <br/>
Pada Switch hanya perlu menghubungkan antar PC yang memiliki Network Address sama. <br/>
Sedangkan pada Route perlu mendefinisikan Network Address pada PC yang berbeda dan memasukannya kedalam sebuah gateway. <br/>

`Pada project sederhana ini konfigurasi router dibagi menjadi 2 step.`
- Step Pertama, mengkonfigurasikan router pada bagian pemberian password authentikasi pada :
  - `User Exec Mode`
  - `Priviledge Exec Mode`
  Konfigurasi ini diset dibagian `global configuration mode`.<br/>
  Disini juga akan dilakukan pemberian Message of The Day (MOTD) pada awal masuk router beserta mengganti `nama pada router`.
  `(Hal ini juga dapat diterapkan pada Switch)`
- Step Kedua, mengkonfigurasikan `Pengalamatan IP pada PC melalui router`. Dimana `PC dengan beda Network Address` dapat saling berkomunikasi.
              Hal ini diperlukan yang namanya `Gateway`. akan tetapi pada tahap ini hanya cukup pada `Step Pertama Saja`.


## Komponen yang dibutuhkan

Berikut komponen yang dibutuhkan dalam konfigurasi router dasar didalam Packet Tracer

- **Router** (Cukup 1 buah saja) (Dapat menggunakan `PT Router` atau router jenis lain sesuai dengan kebutuhan)

Berikut untuk langkah-langkah konfigurasi router-nya.

## Membuat konfigurasi router step pertama di Packet Tracer Cisco

  
1. **Download Packet Tracer Cisco** (Saya menggunakan Versi 8.1.1  32-bit)           _**(Bagi yang belum mendownload)**_ <br/>
   Link download untuk Packet Tracernya [Disini](https://www.packettracernetwork.com/download/download-packet-tracer.html)
   Lakukan instalasi Packet Tracer melalui windows Installer.

2. **Login Cisco NetAcad Account**
   Setelah melakukan instalasi pada Packet Tracer, diwajibkan untuk login terlebih dahulu saat masuk kedalam aplikasinya.<br/>
   Pada sistem login dapat menggunakan Cisco NetAcad atau Skill for All (Jika belum punya bisa registrasi terlebih dahulu) <br/>
   <img src="https://drive.google.com/uc?export=view&id=1kBPsGgtdzBefeubn9mGOI_XrZwuXUOfY" alt="login"
      style="width: 400px; max-width: 100%; height: auto"/> <br/>
      
3. **Masukan Komponen**
   Pada `Logical Workspace`, masukan beberapa komponen kedalam Workspace (background yang warna putih)
   Menuju ke `Network Komponen Box` (Pada bagian kiri pojok bawah) lalu pilih `Device Type Selection Box` -> Klik `Network Devices`
   <img src="https://drive.google.com/uc?export=view&id=1BjDXOFb5IR8Jqw4Q7FP8Rx2qS16Pe-N1" alt="Device type selection box"
      style="width: 400px; max-width: 100%; height: auto"/> <br/>
   Kemudian pada `Network Device` menuju ke paling bawah klik gambar `router`. Disebelah kanan pilih `PT Router`
   
   **(Dapat menggabungkan Komponen yang sudah dibuat sebelumnya di Konfigurasi LAN Dasar)**
   <br/> Menjadi seperti berikut :
   
   <img src="https://drive.google.com/uc?export=view&id=1i32kIMK8fj20QvL8hgb11k90tgP1EGhy" alt="Device type selection box"
      style="width: 400px; max-width: 100%; height: auto"/> <br/>

4. **Konfigurasi Router**
   Pada Router dibagian tab `Physical` akan dijumpai gambar bagan `router`. Bagian `router` yang ditandai garis warna biru adalah tombol power router, <br/>
   yang berfungsi untuk melakukan booting pada router dan mematikan router apabila tidak digunakan.
   <br/>
   <img src="https://drive.google.com/uc?export=view&id=1rhXSSSieFTMqC8S8oMrZR7gD5XofA7ma" alt="Device type selection box"
      style="width: 400px; max-width: 100%; height: auto"/> <br/>
   
   Lalu menuju pada tab `CLI` dimana router akan dikonfigurasikan didalam tab tersebut.
   tab `CLI` memuat sistem operasi berbasis IOS (InterNetwork Operating System) yang mengoperasikan router secara keseluruhan.
   
   Dalam mengkonfigurasi `Router` perlu menuju ke `global configuration mode`, dikarenakan pada mode tersebut membawahi 2 mode yang lain yaitu `User Exec Mode` dan `Priviledge Exec Mode`. 
   
   Berikut Langkah-Langkahnya:
   
   1. Pertama klik Router lalu nyalakan router hingga berwarna hijau
   
   2. Selanjutnya masuk menuju tab `CLI`.
   
   3. Didalam Tab `CLI` jika terdapat pesan `Would you like to enter the initial configuration dialog? [yes/no]:` maka jawab `no` saja.
   
   4. Kemudian tekan `Enter`. dan secara langsung masuk kedalam `User Exec Mode` yang ditandai dengan `(Route>)`.
   
   5. Untuk masuk ke `Priviledge Mode` dapat mengetikan kode berikut pada `User Exec Mode` :
      ```
      enable
      ```
   6. Didalam `priviledge Mode` jika ingin mengecek status router dan konfigurasinya dapat mengetikan kode berikut :
      ```
      show running-config
      ```
      tujuan dari `running-config` adalah untuk mengetahui isi dari konfigurasi router, dan mengecek apabila terdapat konfigurasi yang kurang sesuai pada router.
      file `running-config` dsimpan didalam RAM yang bersifat `Volatile` atau sementara, sehingga jika router dimatikan maka semua konfigurasi akan hilang. 
   
   7. Selanjutnya mencoba untuk memberi password pada `Priviledge Mode`
      Caranya :
      - Pada mode `Priviledge` ketikan kode berikut:
        ```
        configure terminal
        ```
        `configure terminal` berfungsi untuk masuk ke `global configuration mode`. 
        <br/> Selanjutnya didalam `global configuration mode` perlu menset password pada `priviledge mode` dengan cara :
        ```
        enable password 123
        ```
        123 adalah `nama password` dapat berupa text maupun angka (password tanpa menggunakan spasi).
        atau dengan menggunakan `enkripsi` :
        
        ```
        enable secret helo123
        ```
        Berikut jika ingin menambahkan Username bersama dengan password
        
        ```
        username damar secret 123
        ```
        `123` adalah password yang sudah terenkripsi.
        
     Setelah Password (& username jika perlu) pada `Priviledge Mode` sudah ditambahkan.<br/> 
     Selanjutnya pada bagian `User Exec Mode` juga perlu ditambahkan password.
     Caranya :
     
      - Masuk ke `line console` dengan cara mengetikan kode berikut:
        
        ```
        line console 0
        ```
        lakukan kode diatas pada `global configuration mode`. Setelah itu akan diarahkan ke line configuration  (Route (config-line)#... )<br/>
        pada line configuration, dapat menambahkan password (beserta username jika perlu) engan cara :
        
        ```
        username userdamar secret 123
        ```
        lalu Aktifkan autentikasinya `User Exec Mode` dengan mengetik `login` pada `line console`
        
        ```
        login
        ```
        Mirip dengan pengisian user dan pwd pada `Priviledge Mode` akan tetapi jika tanpa enkripsi cukup mengganti `secret` dengan kata `password`.
        setelah menambahkan username dan password pada line console maka keamanan route dari segi autentikasi sudah selesai. Dan jika perlu juga dapat menambahkan MOTD dengan cara :
        
        - Masuk ke `global config mode` jika masih di `line console` bisa ketikan `exit` dahulu.
        - kemudian ketik : 
          
          ```
          banner motd &Authorized Only !&
          ```
        
        _**(Jika ingin mengganti nama router ketik kode berikut )**_ :
        
        ```
        hostname Router_damar
        ```
        pada `global configuration mode`
        
        _**(Jika ingin menenkripsi semua password ketik kode berikut )**_ :
        
        ```
        service password-encryption
        ```
        pada `global configuration mode`
        
5. Pengujian
   
   Ketik `exit` pada `global config mode` dan exit lagi pada `priviledge mode`. setelah itu akan dilakukan proses login dari awal.
   Masukan username maupun password konfigurasi yang sudah dibuat tadi di User Exec mode dan priviledge Exec mode.

## Selesai
   Sekian untuk konfigurasi Router menggunaakn Packet Tracer Cisco. dan untuk hasil jadi dapat diunduh pada repositori file bernama <br/>`Konfigurasi Router Dasar - CPT`<br/>

<h4 align="center">
  Crafted By Damar Djati Wahyu Kemala
</h4>

**@Bahasa-Indonesia**
