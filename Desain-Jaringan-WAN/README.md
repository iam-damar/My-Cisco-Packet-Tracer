## Membuat Desain Jaringan WAN &middot; 
> Pengenalan tentang apa itu WAN?, dan Membuat WAN sederhana.

WAN (Wide Area Network) merupakan sebuah jaringan komputer yang menghubungkan antar end-device/komputer dalam jangkauan yang sangat luas baik antar negara maupun antar benua. WAN terdiri dari gabungan jaringan LAN (Local Area Network) dan MAN (Metropolitan Area Network).

## Komponen yang dibutuhkan

komponen yang dibutuhkan dalam membuat jaringan WAN dan konfigurasinya didalam Packet Tracer

- **End-Device** : PC atau Laptop. (12 Buah)
- **Network Media/Connection** : Copper Straight-Through Cable, Copper Cross-over Cable
- **Intermediary Device** : Switch (Dapat Menggunakan Switch Tipe 2960-24TT) (4 Buah), Router (Dapat Menggunakan Router Tipe 2811) (2 Buah) <br/>

Desain WAN :

<img src="https://drive.google.com/uc?export=view&id=1hRmBpbcI6yxBEQS1mR5jka4gk6xUBw53" alt="login"
      style="width: 650px; max-width: 100%; height: auto"/> <br/>

Berikut untuk IP address pada PC, Network address, Gateway ke router dan Dynamic Routing yang dapat dimasukan kedalam Desain jaringan WAN.

## Membuat jaringan WAN sederhana di Packet Tracer Cisco

- **Konfigurasi IP Address dan Gateway**
  <br/>Pada masing-masing PC yang telah ditambahkan kedalam workspace packet tracer sesuai desain diatas, kemudian dapat memasukan IP address dan Gateway ke masing-masing PC.
  Berikut ini untuk daftar IP dan gateway yang perlu dimasukan ke PC:
  
  | List PC | IP address | Gateway | Subnet |
  | :---: | :---: | :---: | :---: |
  | PC0 | 192.168.1.1 | 192.168.1.254 | 255.255.255.0 |
  | PC1 | 192.168.1.2 | 192.168.1.254 | 255.255.255.0 |
  | PC2 | 192.168.1.3 | 192.168.1.254 | 255.255.255.0 |
  
  | List PC | IP address | Gateway | Subnet |
  | :---: | :---: | :---: | :---: |
  | PC3 | 192.168.2.1 | 192.168.2.254 | 255.255.255.0 |
  | PC4 | 192.168.2.2 | 192.168.2.254 | 255.255.255.0 |
  | PC5 | 192.168.2.3 | 192.168.2.254 | 255.255.255.0 |
  
  | List PC | IP address | Gateway | Subnet |
  | :---: | :---: | :---: | :---: |
  | PC6 | 192.168.3.1 | 192.168.3.254 | 255.255.255.0 |
  | PC7 | 192.168.3.2 | 192.168.3.254 | 255.255.255.0 |
  | PC8 | 192.168.3.3 | 192.168.3.254 | 255.255.255.0 |
  
  | List PC | IP address | Gateway | Subnet |
  | :---: | :---: | :---: | :---: |
  | PC9 | 192.168.4.1 | 192.168.4.254 | 255.255.255.0 |
  | PC10 | 192.168.4.2 | 192.168.4.254 | 255.255.255.0 |
  | PC11 | 192.168.4.3 | 192.168.4.254 | 255.255.255.0 |
  
  **Untuk Router :**
  
  | List Router | IP address |
  | :---: | :---: |
  | Router0 | 172.10.5.1 | 
  | Router1 | 172.10.6.2 |
  
- **Konfigurasi Network Address**
  <br/>Daftar network address yang ada pada masing-masing PC

  | List Network Address | Terkait ke |
  | :---: | :---: |
  | 192.168.1.0 | Router0 |
  | 192.168.2.0 | Router0 |
  | 192.168.3.0 | Router1 |
  | 192.168.4.0 | Router1 |

- **Konfigurasi Dynamic Routing (RIP)**
  <br/>Setelah IP address dan gateway beserta subnet telah dimasukan ke masing-masing PC selanjutnya adalah melakukan konfigurasi RIP pada router,
  akan tetapi sebelum ke RIP perlu mengkonfigurasikan dahulu Gateway, IP Address Router, dan subnetnya.
  Caranya dapat melalui `TAB CLI` maupun `TAB CONFIG`.
  
  `TAB CLI`
    > <br/>Pada Priviledge mode masuk ke global configuration
    ```
    configure terminal
    ```
    > Lalu masuk ke kabel fastEthernet yang terhubung ke router
    > Sebagai contoh fastEthernet 0/1 atau fa0/1 terhubung ke route maka dapat mengetikan kode berikut :
    ```
    interface FastEthernet0/1
    ```
    > Kemudian setelah masuk kedalam interface, masukan nomor gateway pada router dengan nilai subnet default.
    ```
    ip address 192.168.1.254 255.255.255.0
    ```
    Lalu ketik no shutdown agar interface router dapat hidup selama router itu menyala.
    ```
    no shutdown
    ```
    Jika menggunakan `Tab config`, pada menu `fastEthernet` Dapat mengaktifkan `PORT STATUS` (klik kotak sampai muncul tanda centang)
    
    > Sehingga komputer dapat terhubung ke Router.
    
  <br/>
  
  `TAB Config`
    <br/>
    > Masuk saja pada tab config, lalu pada menu sebelah kiri pilih `fastEthernet` yang terhubung ke masing-masing switch. kemudian masukan `Gateway-nya`.
    Lalu 
  
  Selanjutnya Menambahkan IP address pada Router
  Pada `TAB CLI` <br/>
    > dari priviledge mode masuk ke global configuration
    ```
    configure terminal
    ```
    > kemudian jika antar Router terhubung melalui kabel cross-over bertipe Ethernet maka ketikan kode berikut
    ```
    interface Ethernet0/0
    ```
    > Nomor Kabel `aka 0/0` sesuai kabel yang terhubung antar router (USAHAKAN SAMA nomornya)
    > lalu masukan IP ROUTER
    ```
    ip address 172.168.5.1 255.255.255.0
    ```
    > Selanjutnya ketik no shutdown
    ```
    no shutdown
    ```
  Jika ingin mengkonfigurasikan di `TAB CONFIG` dapat mengikuti cara sebelumnnya.
  
  Setelah Melakukan konfigurasi gateway, IP address router, dan Subnet, selanjutnya adalah melakukan konfigurasi RIP pada Router.
  
  **Konfigurasi RIP** dapat dilakukan 2 cara yaitu dengan CLI maupun CONFIG ke menu routernya secara langsung.
  
  untuk mempersingkat waktu, dapat menggunakan CONFIG, dengan cara:
  
  1. Pertama, Menuju ke `TAB CONFIG` pada Router lalu masuk ke `TAB RIP`. 
  2. Kemudian pada `RIP Routing` masukan Network addressnya lalu klik button `Add` 
     - `Router0` masukan NETWORK ADDRESS BERIKUT :
        
        | Network Address |
        | :---: |
        | 172.10.0.0 | 
        | 192.168.1.0 |
        | 192.168.2.0 |
        
     - `Router1` masukan NETWORK ADDRESS BERIKUT :

        | Network Address |
        | :---: |
        | 172.10.0.0 | 
        | 192.168.3.0 |
        | 192.168.4.0 |
   
   Setelah `RIP` pada masing-masing router memiliki network address, maka antar router dapat saling bertukar informasi dan mengenalkan IP address antar PC yang berada
   di router yang berbeda.
   
- Pengujian
   Setelah semua konfigurasi dilakukan selanjutnya melakukan pengujian koneksi antar PC. 
   caranya cukup sederhana, Pertama kita klik salah satu PC, cth: PC0 lalu kita pilih tab `Desktop` kemudian pilih `Command Prompt`.<br/>
   Pada `Command Prompt` masukan kode berikut :
   ```
   ping 192.168.3.1
   ```
   Ping ini tergantung alamat IP address mana yang dituju. jika terdapat jawaban `Reply ...` maka sukses dan jika yang muncul RTO (request time out)<br/>
   Maka kemungkinan besar terdapat konfigurasi yang kurang sesuai.<br/>

- Backup
    Setelah dilakukan pengujian dapat dilakukan backup pada perangkat jaringan khususnya router. Tujuan dari Backup adalah saat router di matikan data konfigurasi
    tidak akan hilang, dan saat di nyalakan kembali data konfigurasi yang kita buat otomatis akan di muat oleh router kembali.
    caranya :
    
    pada `priviledge mode` router ketik
    ```
    copy running-config startup-config
    ```
    lalu tekan `enter` dan `enter` lagi.
    
## Selesai
   Sekian untuk membuat jaringan WAN menggunaakn Packet Tracer Cisco. dan untuk hasil jadi dapat diunduh pada repositori file bernama <br/>`Desain Jaringan WAN - CPT`<br/>

<h4 align="center">
  Crafted By Damar Djati Wahyu Kemala
</h4>

**@Bahasa-Indonesia**

