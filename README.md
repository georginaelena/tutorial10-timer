# Tutorial 10

_Nama    : Georgina Elena Shinta Dewi Achti<br>
NPM     : 2206810995<br>
Kelas   : AdvProg - B_

## 1.2. Understanding How It Works
![](https://i.imgur.com/TxkiGfp.png)
Dalam kode Rust ini, kita melihat implementasi sederhana dari executor untuk menjalankan tugas-tugas asinkron. Ini menggunakan struktur data seperti Task, Spawner, dan Executor, serta komunikasi antara spawner dan executor. Urutan output dipengaruhi oleh cara executor menjalankan tugas-tugas asinkron.

Output "hey hey" dicetak pertama kali karena berada di dalam blok main() yang dieksekusi sebelum tugas-tugas asinkron. Kemudian, tugas asinkron "howdy!" dieksekusi. Sebelum eksekusinya selesai, "done!" belum dicetak karena executor menunggu dengan TimerFuture (dalam kode ini, 2 detik) sampai tugas asinkron selesai baru kemudian mencetak "done!".

