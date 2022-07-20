## Konfigurasi LAN Dasar &middot; 
> Pengenalan tentang apa itu LAN?, serta beberapa komponen didalam jaringan komputer.

LAN (Local Area Network) merupakan sebuah jaringan komputer yang menghubungkan antar end-device didalam area terbatas atau lokal.
LAN sendiri dapat dijumpai di rumah, sekolah, didalam suatu departement dikantor, dan area kampus atau Universitas.

## Komponen yang dibutuhkan

Berikut komponen yang dibutuhkan dalam membuat LAN dan konfigurasinya didalam Packet Tracer

- **End-Device** : PC atau Laptop. (4 Buah)
- **Network Media/Connection** : Copper Straight-Through
- **Intermediary Device** : Switch (Dapat Menggunakan Switch Tipe PT/Generic) (1 Buah) <br/>
  (Switch sendiri merupakan penghubung komunikasi antar komputer/PC satu dengan lainnya dalam network address yang sama)<br/>
  (Switch menerima pesan dan memudahkan pertukaran data/pesan antar komputer/PC)

Berikut untuk langkah-langkahnya.

## Membuat LAN sederhana di Packet Tracer Cisco

1. **Download Packet Tracer Cisco** (Saya menggunakan Versi 8.1.1  32-bit)
   Link download untuk Packet Tracernya [Disini](https://www.packettracernetwork.com/download/download-packet-tracer.html)
   Lakukan instalasi Packet Tracer melalui windows Installer.

2. **Login Cisco NetAcad Account**
   Setelah melakukan instalasi pada Packet Tracer, diwajibkan untuk login terlebih dahulu saat masuk kedalam aplikasinya.<br/>
   Pada sistem login dapat menggunakan Cisco NetAcad atau Skill for All (Jika belum punya bisa registrasi terlebih dahulu) <br/>
   <img src="https://drive.google.com/uc?export=view&id=1kBPsGgtdzBefeubn9mGOI_XrZwuXUOfY" alt="login"
      style="width: 400px; max-width: 100%; height: auto"/> <br/>
      
3. **Masukan Komponen**
   Pada `Logical Workspace`, masukan beberapa komponen kedalam Workspace (background yang warna putih)
   Menuju ke `Network Komponen Box` (Pada bagian kiri pojok bawah) lalu pilih `Device Type Selection Box` -> Klik `End Device`
   <img src="https://drive.google.com/uc?export=view&id=1BjDXOFb5IR8Jqw4Q7FP8Rx2qS16Pe-N1" alt="Device type selection box"
      style="width: 400px; max-width: 100%; height: auto"/> <br/>
   Kemudian pada `End Device` bisa memakai PC atau Laptop (Dibagian kanan Device Type Selection Box) yang ingin dimasukan kedalam workspace.<br/>
   Untuk `Switch` pertama perlu mengeklik `Network Devices` pada `Device type selection box` lalu di bagian bawah sendiri klik gambar `Switch`<br/>
   Sehingga pada bagian kanan akan muncul variasi `switch` yang ada. Pilih `PT-Switch`.

4. **Konfigurasi LAN**
   Dalam mengkonfigurasikan LAN (Local Area Network) kita perlu menghubungkan masing masing PC ke Switch, <br/>
   perlu menggunakan kabel `copper straight-through`. Caranya : Masih pada `Device Type Selection Box` lalu pilih `Connection` (tanda petir)<br/>
   dibagian kanan pilih kabel copper straight-through.
   
   Dalam Menguhubungkan kabel dari PC ke Switch dengan cara : Pertama klik gambar `copper straight-through` lalu klik PC kemudian akan muncul pilihan kabel<br/>
   pilih `FastEthernet 0` pada `PC` lalu hubungkan ke Switch pilih `FastEthernet 0/1` (sesuai urutan jika PC banyak tinggal menyesuaikan).<br/>
   Bentuk jadinya seperti berikut: <br/>
   <img src="https://drive.google.com/uc?export=view&id=1fKYTYfQibBVTcbl1nYEm858HGJkLpZYS" alt="Device type selection box"
      style="width: 400px; max-width: 100%; height: auto"/> <br/>

5. Konfigurasi IP Address
   Setelah PC dan Switch terhubung melalui Network Media/Kabel fisik, tetap saja jaringan antar PC tidak dapat berkomunikasi satu sama lain karena IP address<br/>
   atau alamat untuk mengirim pesan antar PC belum ada. Sehingga perlu untuk menambahkan IP Address ke masing-masing PC.
   Caranya :
   - Pertama, klik pada salah satu PC, cth: `PC0`.
   - Kemudian klik tab `Desktop` pilih `IP Configuration` pada `IPv4 Address` masukan IP berikut untuk masing masing PC<br/>
     `PC 0` 
     ```
     192.168.1.1
     ```
     `PC 1` 
     ```
     192.168.1.2
     ```
     `PC 2` 
     ```
     192.168.1.3
     ```
     `PC 3` 
     ```
     192.168.1.4
     ```
     Lalu pada Subnet Mask untuk semua PC sebagai berikut:
     ```
     255.255.255.0
     ```
6. Pengujian
   Setelah memasang IP Address di setiap PC kita perlu menguji IP disetiap PC tersebut. 
   caranya cukup sederhana, Pertama kita klik salah satu PC, cth: PC0 lalu kita pilih tab `Desktop` kemudian pilih `Command Prompt`.<br/>
   Pada `Command Prompt` masukan kode berikut :
   ```
   ping 192.168.1.2
   ```
   Ping ini tergantung alamat IP address mana yang dituju. jika terdapat jawaban `Reply ...` maka sukses dan jika yang muncul RTO (request time out)<br/>
   Maka kemungkinan besar terdapat konfigurasi pada IP atau Subnetnya yang masih tidak sesuai.<br/>

## Selesai
   Sekian untuk konfigurasi LAN menggunaakn Packet Tracer Cisco. dan untuk hasil jadi dapat diunduh pada repositori file bernama `Konfigurasi LAN Dasar - CPT`<br/>

<h4 align="center">
  Crafted By Damar Djati Wahyu Kemala
</h4>
