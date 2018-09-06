# CodeIgniter-Websocket-Apache-Secure
Pustaka ini berisi demo mengomentari / memposting secara realtime menggunakan CodeIgniter + Ratchet Websocket + Apache dengan Koneksi Aman.

## Sebelum melanjutkan ini
Saya asumsikan anda sudah mengerti kegunaan 3 hal di bawah ini:

Needs | Detail
--- | ---
Framework | CodeIgniter
Websocket | Ratchet
Apache | XAMPP (Recommended!)

(Jika anda tidak mengerti 3 hal tersebut anda bisa mencarinya di google)<br><br>

Pustaka ini sudah di uji dan bekerja 100% pada server localhost yang kemudian dilakukan <b>Port Forwading</b> agar bisa di akses online dan "Secure Connection Active"<br><br>

> <b>(Untuk hosting belum teruji)</b><br>
## Pustaka ini dibuat ?
* Saya tidak menemukan paduan antara CodeIgniter + Ratchet Websocket dengan "Secure Connection". Saya menemukan pustaka tetangga sebelah namun tidak disertakan "Secure Connection". anda bisa kunjungi disini
* Karena saya mencari Ratchet Websocket dengan "Secure Connection" di sumber mana saja, bahkan di situs resmi Ratchet saya masih tidak menemukan sumber yang jelas mengenai "Secure Connection" untuk Ratchet Websocket.
* Tidak ada panduan jelas bagaimana cara menggunakan Apache sebagai jembatan "Secure Connection" untuk Ratchet Websocket
* Mempermudah developer untuk bermigrasi dari Long Polling ke Websocket untuk penghematan bandwitch
* Menjadikan aplikasi menjadi realtime tanpa bermigrasi ke NodeJS yang rumit

## Bagaimana cara menggunakan ?
1. Unduh kode di atas
2. Buka file assets/js/main.js dan gulir ke baris 15 <br>
    ubah domain example.domain.com <br>
       <code> var conn = new WebSocket("wss://example.domain.com/wss2/NNN"); </code> <br>
    dengan domain anda
3. pastikan anda menggunakan apache, disini saya menggunakan apache yang disertakan oleh XAMPP
    - buka file httpd.conf yang berada di<br>
      <b>Linux</b>: /opt/lampp/etc/httpd.conf<br>
      <b>Windows</b>: xampp/apache/conf/httpd.conf<br>
      <b>MacOS</b>: saya tidak memakai MacOS<br>
    + <b>enable mod_proxy.so</b><br>
      search mod_proxy.so<br>
      - <b>Jika mod_proxy ada {</b><br>
          hapus tanda '#' pada <br>
          <code>#LoadModule proxy_module modules/mod_proxy.so</code><br>
          menjadi <br>
          <code>LoadModule proxy_module modules/mod_proxy.so</code><br>
      - <b>}else{</b><br>
          tambahkan sendiri <br>
          <code>LoadModule proxy_module modules/mod_proxy.so</code><br>
      - <b>}</b><br>
    + <b>enable mod_proxy_wstunnel.so</b><br>
      search mod_proxy.so<br>
      - <b>Jika mod_proxy ada {</b><br>
          hapus tanda '#' pada <br>
          <code>#LoadModule proxy_wstunnel_module modules/mod_proxy_wstunnel.so</code><br>
          menjadi <br>
          <code>LoadModule proxy_wstunnel_module modules/mod_proxy_wstunnel.so</code><br>
      - <b>}else{</b><br>
          tambahkan sendiri <br>
          <code>LoadModule proxy_wstunnel_module modules/mod_proxy_wstunnel.so</code><br>
      - <b>}</b><br>
4. <b>Restart apache</b>
5. <b>Jalankan 'chat-server.php' di terminal linux atau cmd windows</b>
    + <b>Linux</b><br>
    contoh: code saya ada di berkas /opt/lampp/htdocs/mydirectory<br>
    maka anda menjalankanya seperti ini di terminal<br>
    <code>php /opt/lampp/htdocs/mydirectory/application/third_party/secure_ratchet/bin/chat-server.php</code><br>
    atau anda masuk ke berkas alamat di atas kemudian klik kiri open terminal, kemudian masukan kode dibawah<br>
    <code>php bin/chat-server.php</code><br>
    + <b>Windows</b><br>
    contoh: code saya ada di berkas E:xampp/htdocs/mydirectory<br>
    anda masuk ke eplorer dan menuju ke alamat berkas di atas kemudian (klik shif + mouse klik kiri) pilih (open command window here)<br>
    kemudian masukan kode dibawah
    <code>php bin/chat-server.php</code><br>

 Kini anda telah selesai dalam proses konfigurasi pustaka ini

## Lisensi
Proyek ini dilisensikan di bawah MIT License - lihat file [LICENSE](https://github.com/aacassandra/CodeIgniter-Websocket-Apache-Secure/blob/master/LICENSE) untuk detailnya
