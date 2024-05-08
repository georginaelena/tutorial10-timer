# Tutorial 10

_Nama    : Georgina Elena Shinta Dewi Achti<br>
NPM     : 2206810995<br>
Kelas   : AdvProg - B_

## 1.2. Understanding How It Works
![](https://i.imgur.com/TxkiGfp.png)

Dalam kode Rust ini, kita melihat implementasi sederhana dari executor untuk menjalankan tugas-tugas asinkron. Ini menggunakan struktur data seperti `Task`, `Spawner`, dan `Executor`, serta komunikasi antara spawner dan executor. Urutan output dipengaruhi oleh cara executor menjalankan tugas-tugas asinkron.

Output "hey hey" dicetak pertama kali karena berada di dalam blok `main()` yang dieksekusi sebelum tugas-tugas asinkron. Kemudian, tugas asinkron "howdy!" dieksekusi. Sebelum eksekusinya selesai, "done!" belum dicetak karena executor menunggu dengan `TimerFuture` (dalam kode ini, 2 detik) sampai tugas asinkron selesai baru kemudian mencetak "done!".

## 1.3. Multiple Spawn and removing drop

Multiple Spawn and Removing Drop:
![](https://i.imgur.com/vFk3zdN.png)

Multiple Spawn and Put Drop:
![](https://i.imgur.com/M3APs8F.png)

Fungsi `spawner.spawn(async { ... })` bertugas memicu task-task asinkron yang akan dieksekusi oleh Executor. Sementara itu, fungsi `drop(spawner)` bertindak sebagai penanda bahwa tidak akan ada lagi task yang dimasukkan ke dalam antrian tugas yang akan dieksekusi.

Output yang dihasilkan ketika `drop(spawner)` ada dan ketika tidak ada berbeda. Perbedaan tersebut terjadi karena tanpa `drop(spawner)`, executor akan terus menunggu task baru untuk dieksekusi, sehingga tugas yang telah siap akan langsung dieksekusi. Namun, dengan `drop(spawner)`, executor mengetahui bahwa tidak akan ada lagi task baru yang masuk ke dalam antrian, sehingga ia akan menyelesaikan dulu tugas-tugas yang masih ada di dalam antrian sebelum mengakhiri eksekusi. Inilah yang menyebabkan perbedaan urutan output pada bagian "done".
