![gambar 1](timer_future/Gambar/image.png)
Penjelasan : "hey hey!" muncul sebelum "howdy!" dan "done!" karena pesan ditambahkan sebelum executor dijalankan. Ini menunjukkan sifat asynchronous dari kode.

![With Drop](<timer_future/Gambar/Screenshot 2025-05-19 163001.png>)
![No Drop](<timer_future/Gambar/Screenshot 2025-05-19 163132.png>)
Penjelasan : 

Saat ada drop setelah beberapa saat process akan selesai secara sendiri, tetapi saat tidak ada drop executor.run() tidak akan berhenti karena masih menunggu tugas baru. 

Selain itu Pesan "howdy!", "howdy1!", "howdy2!", "howdy3!" selalu muncul dalam urutan yang sama karena ini adalah bagian pertama dari setiap tugas async yang dijalankan secara berurutan saat executor.run() dimulai. 

Pesan "done!", "done1!", "done2!", "done3!" muncul dalam urutan yang berbeda-beda karena:
- Setiap tugas menunggu timer yang sama (2 detik)
- Timer dimulai hampir bersamaan tapi bisa ada variasi mikrodetik
- Sistem operasi menjadwalkan thread secara berbeda di setiap eksekusi
- Eksekutor asynchronous mengerjakan tugas-tugas yang siap (ready) dalam urutan yang bisa bervariasi