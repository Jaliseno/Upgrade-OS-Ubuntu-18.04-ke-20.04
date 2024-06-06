&nbsp; &nbsp; Halo Rekan CloudKilat ada informasi terbaru dari plesk nih, mereka akan terus menghadirkan versi baru Plesk Obsidian sesuai dengan jadwal yang telah ditetapkan. Versi baru ini akan mencakup fitur-fitur baru, pembaruan fungsional, dan pembaruan keamanan, selama tidak bertentangan dengan perangkat lunak yang disediakan oleh vendor OS. Namun sayangnya untuk versi OS ubuntu 18.04 hanya disupport hingga 1 Oktober 2024. Berdasarkan informasi tersebut kami telah membuat knowlage base untuk melakukan dist-upgrade dari OS versi 18.04 ke Ubuntu 20.04 (_Sebagai informasi untuk versi OS ubuntu 20.04 akan disupport hingga April 2025_) dan apabila nantinya versi OS Ubuntu 20.04 sudah tidak disupport lagi oleh Plesk kami juga telah membuat knowlage base untuk melakukan dist-upgrade dari OS versi 20.04 ke Ubuntu 22.04 (_tautan KB Ardi_).

## Persiapan
1. Lakukan backup secara menyeluruh sebelum Anda melakukan dist-upgrade, adapun untuk langkah backup Anda dapat memilih menu **Tools & Settings** >> **Backup Manager** >> Apabila Belum memiliki jadwal backup rutin Anda dapat memilih ****Create a Backup** >> Pilih sesuai kebutuhan >> Pilih **Ok** >> Setelah proses backup selesai silakan Anda Download hasil backup ke local komputer Anda.
**Catatan:** _*apabila ragu Anda dapat melakukan request ke tim support CloudKilat untuk melakukan snapshoot sebelum proses dist-upgrade dilakukan_
2. Pastikan Versi Plesk sudah disupport oleh versi OS Ubuntu 20.04 (_Plesk Obsidian 18.0.61.5_), untuk melihat versi Plesk Anda dapat menjalan perintah **_plesk -v_**. Apabila versi plesk masih belum disupport berikut knowlage base untuk upgrade versi plesk panel (_tautan KB Upgrade versi plesk_)
3. Pastikan versi PHP websute Anda sudah mensupport PHP versi 7.1 dan apabila belum kami sarankan untuk melakukan upgrade versi PHP website Anda, untuk detailnya silakan menghubungi pihak developer website Anda.

## Proses Dist-Upgrade dari OS versi 18.04 ke Ubuntu 20.04
1. Login ke layanan Kilat VM menggunakan user root atau user lain yang memiliki akses root
2. Unduh dan ekstrak versi tools terbaru ke layanan Kilat VM Anda dengan perintah sebagai berikut:
```
# wget https://github.com/plesk/ubuntu18to20/releases/download/v2.0.0/ubuntu18to20-2.0.0.zip
# unzip ubuntu18to20-2.0.0.zip
# chmod 755 ubuntu18to20
```

3. Untuk memantau proses konversi, gunakan utilitas **_screen_** untuk menjalankan tools di latar belakang dengan perintah berikut:

```
# screen -S ubuntu18to20
```

4. Setelah **_screen_** dibuat, jalankan tools yang sudah diekstrak perintah dibawah ini:

```
# ./ubuntu18to20
```
**Catatan:** _*perlu diperhatikan bahwa proses diatas akan membuat layanan melakukan restart beberapa kali dan jika koneksi SSH terputus Anda dapat masuk lagi ke sesi screen dengan perintah dibawah._

```
# screen -r ubuntu18to20
```

5. Proses Konversi akan membutuhkan waktu sekitar 30 Menit dan nantinya jika koneksi terputus setelah konversi selesai, silakan login kembali dilanjutkan menjalan perintah dibawah ini untuk memantau proses penyelesaiannya:
```
# ./ubuntu18to20 --status

atau

# ./ubuntu18to20 --monitor
```
**Catatan:** _*Sebagai alternatif, status dapat dipantau dengan memeriksa file log di /etc/motd. Setelah proses selesai, pesan berikut akan terlihat:_

```
===============================================================================
Message from the Plesk dist-upgrader tool:

The server has been upgraded to Ubuntu 20.
You can remove this message from the /etc/motd file.
===============================================================================
```

