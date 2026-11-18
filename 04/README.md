# RANGKUMAN MATERI TEORI SISTEM TERDISTRIBUSI DAN TERDESENTRALISASI

## PERTEMUAN 4

---

## A. IDENTITAS MATERI

| Keterangan | Informasi |
|---|---|
| Mata Kuliah | Teori Sistem Terdistribusi dan Terdesentralisasi |
| Pertemuan | Pertemuan ke-4 |
| Topik Materi | Konsistensi dan Replikasi pada Sistem Terdistribusi |
| Sumber Materi | 04--konsistensi-dan-replikasi (1).pdf |
| AI yang Digunakan | ChatGPT GPT-6 |
| Format Dokumen | Markdown (.md) |

---

## B. TUJUAN PEMBELAJARAN

Setelah mempelajari materi pada pertemuan ini, mahasiswa diharapkan mampu:

1. Memahami dan menjelaskan konsep konsistensi dalam sistem terdistribusi serta alasan pentingnya menjaga kesamaan data antar-node.
2. Memahami berbagai model konsistensi, Teorema CAP, dan hubungan antara tingkat konsistensi dengan latensi sistem.
3. Memahami konsep replikasi data, jenis-jenis replikasi, strategi sinkronisasi replika, serta mekanisme penanganan konflik.
4. Menjelaskan berbagai protokol replikasi dan menganalisis penerapannya pada sistem nyata, khususnya PostgreSQL dan Apache Ignite.

---

## C. RANGKUMAN MATERI

### 1. Pengertian dan Pentingnya Konsistensi pada Sistem Terdistribusi

Konsistensi merupakan kondisi ketika data yang terdapat pada beberapa node atau server dalam sistem terdistribusi memiliki nilai yang sama atau memberikan informasi yang sesuai berdasarkan aturan konsistensi tertentu. Hal ini penting karena dalam sistem terdistribusi, data biasanya disimpan di beberapa lokasi yang berbeda dan dapat mengalami perubahan secara bersamaan.

Sebagai contoh, sebuah aplikasi memiliki beberapa server yang menyimpan salinan data pengguna. Ketika pengguna memperbarui informasi pada salah satu server, sistem perlu memastikan bahwa perubahan tersebut juga dapat diterapkan pada server lainnya. Proses menjaga agar seluruh salinan data tetap sesuai inilah yang disebut konsistensi data.

**Mengapa Konsistensi Penting?**

Konsistensi diperlukan agar pengguna mendapatkan informasi yang benar ketika mengakses sistem. Jika tidak dijaga, pengguna dapat memperoleh informasi yang berbeda tergantung pada server yang melayani permintaannya.

Contohnya terdapat pada sistem perbankan. Seorang nasabah melakukan transfer uang dari rekening A ke rekening B. Server pertama telah mengurangi saldo rekening A, tetapi server kedua belum memperbarui saldo rekening B. Apabila nasabah langsung menggunakan saldo rekening B untuk melakukan transaksi lain, sistem dapat menampilkan saldo yang belum sesuai dengan hasil transfer.

Kondisi tersebut dapat menimbulkan masalah karena proses transaksi tidak mencerminkan keadaan data yang sebenarnya.

**[MODIFIKASI]** Permasalahan tersebut menunjukkan bahwa konsistensi tidak hanya berkaitan dengan kesamaan angka pada beberapa server, tetapi juga berkaitan dengan kebenaran suatu proses bisnis. Dalam transaksi keuangan, misalnya, pengurangan saldo dari rekening pengirim dan penambahan saldo ke rekening penerima perlu dikelola sebagai operasi yang saling berkaitan. Apabila salah satu perubahan berhasil sementara perubahan lainnya belum diterapkan, sistem berpotensi menghasilkan kondisi data yang tidak sesuai.

Beberapa alasan konsistensi menjadi penting antara lain:

1. **Menjaga integritas data:** Memastikan informasi yang disimpan tidak mengalami perbedaan yang tidak semestinya.
2. **Menghindari informasi yang bertentangan:** Pengguna tidak memperoleh nilai data yang berbeda secara tidak terkontrol.
3. **Mendukung transaksi:** Operasi yang saling berkaitan dapat diproses dengan aturan yang tepat.
4. **Meningkatkan kepercayaan pengguna:** Sistem dapat memberikan informasi yang dapat diandalkan.
5. **Mendukung keandalan sistem:** Perubahan data dapat dikelola meskipun sistem menggunakan beberapa server.

### 2. Teorema CAP

Teorema CAP merupakan konsep dalam sistem terdistribusi yang menjelaskan hubungan antara tiga karakteristik utama, yaitu Consistency, Availability, dan Partition Tolerance.

Ketiga karakteristik tersebut adalah:

**a. Consistency (Konsistensi)**

Consistency berarti setiap pembacaan data memberikan nilai yang sesuai dengan jaminan konsistensi sistem. Dalam gambaran sederhana pada materi, seluruh node memiliki data yang sama.

**b. Availability (Ketersediaan)**

Availability merupakan kemampuan sistem untuk tetap memberikan respons terhadap permintaan pengguna. Artinya, ketika pengguna mengakses layanan, sistem tetap berusaha memberikan jawaban meskipun terdapat gangguan pada sebagian komponennya.

**c. Partition Tolerance (Toleransi Partisi)**

Partition Tolerance merupakan kemampuan sistem untuk tetap beroperasi ketika terjadi gangguan komunikasi atau pemisahan jaringan antar-node.

Network partition dapat terjadi ketika dua atau lebih bagian sistem tidak dapat berkomunikasi karena masalah jaringan. Kondisi ini perlu diperhitungkan karena sistem terdistribusi bergantung pada komunikasi antarperangkat.

**Hubungan Ketiga Komponen CAP**

Dalam kondisi terjadi network partition, sistem harus menentukan bagaimana menangani permintaan yang masuk. Secara sederhana, terdapat dua pendekatan yang sering dibahas:

1. **CP (Consistency dan Partition Tolerance):** Sistem lebih mengutamakan konsistensi ketika terjadi partisi jaringan. Beberapa permintaan dapat ditolak atau ditunda sampai komunikasi kembali normal.
2. **AP (Availability dan Partition Tolerance):** Sistem tetap berusaha memberikan layanan meskipun sebagian node tidak dapat berkomunikasi. Konsekuensinya, data antar-node dapat berbeda untuk sementara waktu.

Contoh yang terdapat dalam materi adalah aplikasi e-commerce dengan dua server:

- Server A melayani wilayah barat Indonesia.
- Server B melayani wilayah timur Indonesia.

Ketika koneksi antara kedua server terputus, terdapat dua kemungkinan pendekatan.

**Jika memilih pendekatan AP:**

Pengguna di kedua wilayah tetap dapat melakukan pembelian. Namun, informasi stok pada server A dan B mungkin belum sama karena perubahan belum dapat disinkronkan.

**Jika memilih pendekatan CP:**

Sistem dapat membatasi transaksi yang membutuhkan data bersama sampai koneksi kembali pulih. Tujuannya agar keputusan transaksi tidak menggunakan informasi yang berpotensi berbeda.

**[MODIFIKASI]** Teorema CAP bukan berarti sebuah sistem hanya boleh memiliki dua dari tiga karakteristik tersebut dalam seluruh keadaan. Hal yang perlu diperhatikan adalah ketika terjadi partisi jaringan, sistem harus menentukan prioritas antara konsistensi dan ketersediaan. Dalam kondisi jaringan normal, sistem tetap dapat dirancang untuk memberikan konsistensi dan ketersediaan secara bersamaan.

### 3. Model Konsistensi pada Sistem Terdistribusi

Model konsistensi merupakan aturan atau jaminan yang menentukan bagaimana perubahan data dapat dilihat oleh node atau klien lain. Setiap model mempunyai tingkat jaminan yang berbeda, terutama mengenai waktu dan urutan perubahan data dapat diketahui oleh pengguna.

Beberapa model konsistensi yang dibahas dalam materi adalah sebagai berikut.

**a. Strong Consistency**

Strong Consistency merupakan model yang memberikan jaminan kuat terhadap keterbaruan data. Setelah suatu perubahan dinyatakan selesai, pembacaan berikutnya akan memperoleh nilai terbaru sesuai urutan operasi yang dijamin oleh sistem.

Contohnya adalah sistem perbankan. Ketika saldo rekening berubah setelah transaksi, sistem perlu memastikan pembacaan berikutnya tidak menggunakan saldo lama yang dapat menyebabkan kesalahan transaksi.

Model ini biasanya membutuhkan mekanisme koordinasi antar-node yang lebih ketat. Materi menyebutkan Two-Phase Commit dan Paxos sebagai contoh protokol yang berkaitan dengan pengelolaan konsistensi.

**b. Eventual Consistency**

Eventual Consistency merupakan model yang tidak mengharuskan semua replika memiliki data yang sama secara langsung setelah terjadi perubahan. Namun, apabila tidak ada pembaruan baru dan proses sinkronisasi berjalan dengan baik, seluruh replika pada akhirnya akan mencapai keadaan yang sama.

Model ini cocok untuk sistem yang mengutamakan ketersediaan dan kecepatan respons.

Contohnya adalah sistem database terdistribusi seperti Amazon DynamoDB dan Apache Cassandra yang dapat menggunakan pendekatan konsistensi eventual sesuai konfigurasi dan kebutuhan penggunaannya.

Eventual Consistency juga berkaitan dengan konsep BASE:

- **Basically Available:** Sistem berusaha tetap menyediakan layanan meskipun terjadi kegagalan sebagian.
- **Soft State:** Kondisi data pada replika dapat berubah seiring proses sinkronisasi berlangsung.
- **Eventual Consistency:** Data pada seluruh replika pada akhirnya akan konsisten jika tidak terdapat pembaruan baru dan sinkronisasi berhasil.

**c. Causal Consistency**

Causal Consistency merupakan model yang menjaga urutan operasi yang memiliki hubungan sebab-akibat. Apabila suatu operasi bergantung pada operasi sebelumnya, maka urutan tersebut harus tetap dipertahankan ketika dilihat oleh node atau pengguna lain.

Contohnya pada media sosial. Seseorang membuat sebuah postingan, kemudian pengguna lain memberikan komentar. Sistem seharusnya tidak menampilkan komentar tersebut sebelum postingan yang menjadi konteksnya tersedia.

Sementara itu, operasi yang tidak memiliki hubungan sebab-akibat dapat terlihat dalam urutan yang berbeda pada node lain.

**d. Read-Your-Writes Consistency**

Read-Your-Writes Consistency menjamin bahwa setelah pengguna melakukan perubahan data, pembacaan berikutnya oleh pengguna yang sama akan melihat hasil perubahan tersebut.

Contohnya ketika seseorang mengirim pesan melalui aplikasi messaging. Pesan yang dikirim langsung muncul pada layar pengirim meskipun perangkat penerima belum menerima atau menampilkan pesan tersebut.

Model ini membantu menjaga pengalaman pengguna agar perubahan yang baru dilakukan tidak seolah-olah hilang ketika aplikasi dibuka atau diperbarui.

**e. Monotonic Read Consistency**

Monotonic Read Consistency menjamin bahwa pengguna yang telah membaca suatu versi data tidak akan mendapatkan versi yang lebih lama pada pembacaan berikutnya.

Contohnya pada timeline media sosial. Ketika pengguna sudah melihat postingan terbaru, kemudian melakukan refresh, sistem seharusnya tidak menampilkan kondisi timeline yang lebih lama dari versi yang sebelumnya sudah dilihat.

**f. Sequential Consistency**

Sequential Consistency merupakan model yang memastikan seluruh operasi terlihat seolah-olah dijalankan dalam satu urutan tertentu yang sama oleh semua node. Urutan tersebut harus sesuai dengan urutan operasi yang dilakukan masing-masing proses, tetapi tidak harus mengikuti waktu nyata secara ketat.

Contohnya pada media sosial, seluruh pengguna dapat melihat urutan posting yang sama meskipun terdapat sedikit keterlambatan ketika informasi diperbarui.

**g. Linearizability**

Linearizability merupakan salah satu jaminan konsistensi yang paling kuat. Model ini memastikan operasi terlihat seolah-olah terjadi secara atomik pada suatu titik waktu di antara awal dan akhir operasi sebenarnya.

Setiap operasi juga harus mempertahankan urutan waktu nyata. Artinya, apabila suatu operasi telah selesai sebelum operasi lain dimulai, urutan tersebut harus tetap dipertahankan.

Contohnya adalah pengecekan keunikan username. Ketika dua pengguna mencoba mendaftarkan username yang sama secara bersamaan, sistem harus memastikan hanya satu pendaftaran yang berhasil.

Materi mencantumkan etcd, ZooKeeper, dan Spanner sebagai contoh sistem yang berkaitan dengan jaminan konsistensi kuat.

**Perbandingan Model Konsistensi**

| Model | Jaminan Utama | Contoh Penggunaan |
|---|---|---|
| Strong Consistency | Pembacaan memperoleh data terbaru sesuai jaminan sistem | Sistem perbankan |
| Eventual Consistency | Replika pada akhirnya mencapai data yang sama | Database terdistribusi |
| Causal Consistency | Urutan sebab-akibat tetap dipertahankan | Postingan dan komentar |
| Read-Your-Writes | Pengguna melihat perubahan yang baru dibuatnya | Aplikasi messaging |
| Monotonic Read | Pengguna tidak melihat versi data yang lebih lama dari yang pernah dibaca | Timeline media sosial |
| Sequential Consistency | Semua node melihat urutan operasi yang sama | Sistem berbagi informasi |
| Linearizability | Operasi tampak atomik dan mengikuti urutan waktu nyata | Pengecekan username unik |

**[MODIFIKASI]** Setiap model konsistensi mempunyai tujuan yang berbeda. Sistem yang mengelola transaksi keuangan membutuhkan jaminan yang lebih kuat dibandingkan sistem yang menampilkan jumlah pengunjung atau aktivitas media sosial. Oleh karena itu, pemilihan model konsistensi perlu disesuaikan dengan dampak kesalahan data terhadap pengguna dan proses bisnis.

### 4. Trade-off antara Latensi dan Konsistensi

Latensi merupakan waktu yang dibutuhkan sistem untuk memproses permintaan dan memberikan respons kepada pengguna.

Dalam sistem terdistribusi, terdapat hubungan antara tingkat konsistensi dengan latensi. Semakin tinggi jaminan konsistensi yang dibutuhkan, biasanya semakin banyak komunikasi dan koordinasi antar-server yang harus dilakukan. Hal tersebut dapat meningkatkan waktu respons.

Materi menjelaskan hubungan tersebut sebagai berikut:

- Konsistensi meningkat → latensi cenderung meningkat.
- Konsistensi menurun → latensi dapat lebih rendah.

**a. Strong Consistency dan Latensi**

Pada Strong Consistency, sistem perlu memastikan perubahan data telah memenuhi aturan konsistensi sebelum memberikan respons. Jika data berada pada beberapa server dengan lokasi berbeda, komunikasi antar-server dapat menambah waktu pemrosesan.

Contohnya, terdapat dua pusat data di Jakarta dan Yogyakarta. Ketika pengguna mengubah data di Jakarta, sistem perlu memastikan perubahan tersebut juga diterapkan sesuai aturan konsistensi pada pusat data Yogyakarta sebelum menyelesaikan permintaan tertentu.

**b. Eventual Consistency dan Latensi**

Pada Eventual Consistency, sistem dapat memberikan respons tanpa harus menunggu seluruh replika selesai menerima pembaruan. Dengan demikian, waktu respons dapat lebih cepat.

Namun, pengguna yang membaca dari server berbeda mungkin memperoleh nilai yang belum sama untuk sementara waktu.

**[MODIFIKASI]** Trade-off ini menunjukkan bahwa tidak semua aplikasi harus menggunakan konsistensi paling kuat. Aplikasi perbankan, misalnya, perlu memberikan perhatian besar terhadap kebenaran saldo dan transaksi. Sebaliknya, aplikasi yang menampilkan jumlah tayangan atau aktivitas pengguna mungkin masih dapat menerima keterlambatan sinkronisasi selama informasi akhirnya diperbarui dengan benar.

### 5. Pengertian dan Tujuan Replikasi Data

Replikasi data merupakan proses membuat dan memelihara salinan data yang sama pada beberapa node atau server dalam sistem terdistribusi.

Tujuan utamanya adalah meningkatkan ketersediaan, keandalan, dan kinerja sistem. Dengan adanya beberapa salinan data, layanan tidak harus bergantung pada satu server saja.

Contohnya sebuah perusahaan memiliki database utama di Jakarta. Untuk mendukung ketersediaan layanan, perusahaan menambahkan salinan database di Yogyakarta dan Denpasar.

Jika server di Jakarta mengalami gangguan, salinan data yang tersedia di lokasi lain dapat membantu menjaga layanan tetap berjalan sesuai mekanisme yang diterapkan.

Beberapa tujuan replikasi data adalah:

1. **Availability:** Apabila satu server mengalami kegagalan, server lain masih dapat menyediakan salinan data.
2. **Performance:** Pengguna dapat membaca data dari server yang lokasinya lebih dekat sehingga waktu akses dapat berkurang.
3. **Reliability:** Penyimpanan salinan pada beberapa node membantu mengurangi risiko kehilangan data akibat kegagalan satu perangkat.
4. **Scalability:** Beban permintaan baca dapat dibagi ke beberapa server sehingga tidak seluruhnya ditangani oleh satu server.

**[MODIFIKASI]** Replikasi bukan sekadar menggandakan database. Sistem juga harus mempunyai mekanisme untuk menyebarkan perubahan, menentukan urutan pembaruan, dan menangani konflik apabila beberapa replika mengalami perubahan secara bersamaan. Tanpa mekanisme tersebut, jumlah salinan data yang banyak justru dapat meningkatkan kemungkinan terjadinya perbedaan informasi.

### 6. Jenis-Jenis Replikasi Data

Berdasarkan materi perkuliahan, replikasi dapat dibedakan berdasarkan hubungan antar-node dan waktu penyinkronan data.

**a. Master-Slave (Primary-Secondary)**

Pada model Master-Slave, terdapat satu node utama yang bertugas menerima operasi penulisan data. Node lainnya bertindak sebagai replika yang menerima salinan perubahan dan umumnya digunakan untuk membaca data.

Karakteristiknya:

- Penulisan data dilakukan melalui master atau primary.
- Replika secondary menerima pembaruan dari node utama.
- Pembacaan dapat dibagi ke beberapa replika.
- Pengelolaan perubahan lebih terpusat.

Kelebihannya adalah mekanisme penulisan relatif mudah dikelola. Namun, master dapat menjadi bottleneck dan berpotensi menjadi single point of failure apabila tidak disertai mekanisme failover.

Contoh yang dicantumkan dalam materi adalah PostgreSQL Streaming Replication.

**b. Multi-Master (Peer-to-Peer)**

Pada model Multi-Master, beberapa node memiliki kemampuan untuk menerima operasi baca dan tulis.

Karakteristiknya:

- Setiap node dapat menerima perubahan data.
- Pembaruan perlu disebarkan ke node lain.
- Sistem lebih fleksibel ketika melayani permintaan dari beberapa lokasi.
- Potensi konflik meningkat apabila beberapa node mengubah data yang sama.

Kelebihannya adalah penulisan tidak hanya bergantung pada satu server. Namun, sistem membutuhkan mekanisme penanganan konflik yang baik.

Materi mencantumkan PostgreSQL Logical Replication, Apache Cassandra, MongoDB, dan Apache Ignite sebagai contoh teknologi yang berkaitan dengan pendekatan multi-master atau replikasi multi-node sesuai konfigurasi masing-masing.

**c. Synchronous Replication**

Synchronous Replication merupakan metode replikasi ketika sumber menunggu konfirmasi dari replika sesuai aturan sinkronisasi sebelum operasi dianggap selesai.

Pendekatan ini memberikan jaminan konsistensi yang lebih kuat, tetapi dapat meningkatkan latensi karena sistem harus menunggu komunikasi dengan replika.

**d. Asynchronous Replication**

Asynchronous Replication merupakan metode ketika sumber menyelesaikan transaksi tanpa harus menunggu seluruh replika menerima atau menerapkan perubahan.

Kelebihannya adalah waktu respons lebih cepat. Namun, apabila sumber mengalami kegagalan sebelum perubahan berhasil disebarkan, terdapat risiko data yang belum sempat direplikasi hilang dari replika.

### 7. Strategi Sinkronisasi Replika

Strategi sinkronisasi replika dapat dibedakan berdasarkan waktu sinkronisasi, arah replikasi, cara pengiriman perubahan, dan penanganan konflik.

**a. Berdasarkan Waktu Sinkronisasi**

Terdapat tiga pendekatan utama:

1. **Asynchronous:** Sumber melakukan commit tanpa menunggu replika. Kinerja lebih cepat, tetapi risiko kehilangan perubahan yang belum tersalin lebih besar.
2. **Semi-Synchronous:** Sumber menunggu setidaknya satu replika menerima data sebelum melanjutkan proses sesuai mekanisme yang digunakan. Pendekatan ini menjadi kompromi antara konsistensi dan performa.
3. **Synchronous:** Sumber menunggu seluruh replika yang diwajibkan melakukan commit sebelum operasi dianggap selesai. Konsistensi lebih kuat, tetapi latensi dapat lebih tinggi.

**b. Berdasarkan Arah Replikasi**

1. **Master-Slave:** Satu node bertindak sebagai sumber utama penulisan, sedangkan node lainnya menerima salinan perubahan.
2. **Master-Master:** Beberapa node mempunyai kemampuan dan peran yang relatif setara dalam menerima operasi baca dan tulis.
3. **Master-Master Asymmetric:** Beberapa node dapat melakukan baca dan tulis, tetapi memiliki peran, sumber daya, atau kemampuan yang berbeda.

**c. Berdasarkan Cara Sinkronisasi**

1. **Pull-Based:** Replika secara berkala memeriksa sumber untuk mengetahui apakah terdapat pembaruan. Jika ditemukan perubahan, replika mengambil data tersebut.
2. **Push-Based:** Sumber secara aktif mengirimkan pembaruan kepada replika ketika terjadi perubahan. Materi menyebutkan Change Data Capture (CDC), WebSockets, dan Server-Sent Events (SSE) sebagai teknologi yang berkaitan dengan pendekatan ini.
3. **Hybrid:** Menggabungkan pendekatan pull-based dan push-based sesuai kebutuhan sistem.

**d. Berdasarkan Penanganan Konflik**

Ketika beberapa replika melakukan pembaruan terhadap data yang sama, sistem membutuhkan mekanisme untuk menentukan bagaimana perubahan tersebut digabungkan atau dipilih.

Beberapa pendekatan yang dibahas adalah:

- Last Write Wins (LWW).
- Vector Clocks.
- Conflict-Free Replicated Data Types (CRDT).
- Operational Transformation (OT).

### 8. Penanganan Konflik Replikasi

Konflik replikasi dapat terjadi ketika beberapa node melakukan perubahan terhadap data yang sama sebelum pembaruan dari node lain diterima.

**a. Last Write Wins (LWW)**

Last Write Wins merupakan pendekatan yang memilih perubahan berdasarkan timestamp terbaru. Pembaruan yang dianggap paling baru akan digunakan, sedangkan pembaruan lainnya tidak dipertahankan sebagai nilai akhir.

Kelebihannya adalah mekanisme relatif sederhana. Namun, pendekatan ini berisiko menghilangkan perubahan lain yang sebenarnya juga penting. Selain itu, ketepatan timestamp menjadi faktor yang perlu diperhatikan.

**b. Vector Clocks**

Vector Clocks digunakan untuk mencatat hubungan urutan dan sebab-akibat antarperubahan. Dengan informasi tersebut, sistem dapat mengetahui apakah dua pembaruan memiliki hubungan sebab-akibat atau terjadi secara konkuren.

Konsep ini berkaitan dengan materi pertemuan sebelumnya mengenai sinkronisasi waktu logis.

**c. Conflict-Free Replicated Data Types (CRDT)**

CRDT merupakan jenis struktur data yang dirancang agar perubahan pada beberapa replika dapat digabungkan dengan aturan tertentu tanpa menghasilkan konflik yang tidak dapat diselesaikan.

Materi memberikan contoh penghitung jumlah pengunjung website yang dikelola oleh dua pengguna, yaitu Agnes Monica dan Bambang.

Kondisi awal:

```text
{"Agnes Monica": 0, "Bambang": 0}
```

Agnes Monica mencatat lima pengunjung:

```text
{"Agnes Monica": 5, "Bambang": 0}
```

Bambang mencatat tiga pengunjung:

```text
{"Agnes Monica": 0, "Bambang": 3}
```

Ketika kedua perangkat melakukan sinkronisasi, sistem menggunakan aturan nilai maksimum untuk setiap elemen.

Perhitungannya:

- Nilai Agnes Monica = max(5, 0) = 5.
- Nilai Bambang = max(0, 3) = 3.

Hasil akhirnya:

```text
{"Agnes Monica": 5, "Bambang": 3}
```

Total pengunjung adalah:

```text
5 + 3 = 8 pengunjung
```

Contoh tersebut menggambarkan bagaimana CRDT dapat menggabungkan perubahan lokal dari beberapa perangkat menggunakan aturan penggabungan yang sesuai.

Materi juga mencantumkan Yjs sebagai contoh implementasi teknologi yang menggunakan konsep CRDT untuk kolaborasi dokumen.

**d. Operational Transformation (OT)**

Operational Transformation merupakan pendekatan untuk mengatasi konflik perubahan dalam dokumen yang diedit secara bersamaan oleh beberapa pengguna.

Materi memberikan contoh dokumen awal:

```text
abc
```

Terdapat dua pengguna yang melakukan perubahan secara bersamaan:

- Agnes Monica menyisipkan huruf `x` pada indeks 0 sehingga dokumennya menjadi `xabc`.
- Bambang menghapus karakter `c` pada indeks 2 sehingga dokumennya menjadi `ab`.

Jika perubahan tersebut diterapkan tanpa penyesuaian posisi, hasilnya dapat berbeda:

- Agnes menerapkan perintah hapus indeks 2 pada `xabc`, sehingga huruf `b` terhapus dan hasilnya `xac`.
- Bambang menerapkan perintah sisip `x` pada indeks 0 pada `ab`, sehingga hasilnya `xab`.

Hasil kedua pengguna tidak sama.

OT menyelesaikan masalah tersebut dengan mentransformasikan operasi agar posisi perubahan menyesuaikan kondisi dokumen terbaru.

Dalam contoh:

- Pada sisi Agnes, operasi hapus indeks 2 ditransformasikan menjadi hapus indeks 3 karena terdapat penyisipan karakter di awal.
- Pada sisi Bambang, operasi penyisipan di indeks 0 tetap diterapkan dan posisi penghapusan disesuaikan.

Hasil akhirnya menjadi:

```text
xab
```

**[MODIFIKASI]** CRDT dan OT sama-sama dapat digunakan untuk mendukung kolaborasi, tetapi pendekatannya berbeda. CRDT mengandalkan struktur data dan aturan penggabungan yang dirancang agar perubahan dapat disatukan, sedangkan OT mengubah operasi berdasarkan perubahan lain yang terjadi secara bersamaan. Keduanya membantu menjaga kesesuaian dokumen ketika beberapa pengguna melakukan pengeditan pada waktu yang sama.

### 9. Protokol Replikasi

Materi memperkenalkan beberapa protokol yang digunakan untuk mengelola replikasi data dalam sistem terdistribusi.

**a. Primary-Based (Master-Slave)**

Pada pendekatan ini, satu node utama menerima operasi penulisan, sedangkan replika lainnya menerima pembaruan dan dapat digunakan untuk membaca data.

Pendekatan ini memudahkan pengaturan perubahan karena penulisan data memiliki sumber utama.

**b. Quorum-Based**

Quorum-Based merupakan mekanisme replikasi yang menentukan jumlah minimum node yang harus memberikan konfirmasi agar operasi baca atau tulis dianggap berhasil.

Materi menggunakan rumus:

```text
W + R > N
```

Keterangan:

- `W` = jumlah minimum node yang harus mengonfirmasi operasi write.
- `R` = jumlah minimum node yang harus merespons operasi read.
- `N` = jumlah seluruh node dalam sistem.

Contohnya terdapat tiga node, yaitu A, B, dan C.

Konfigurasi:

```text
N = 3
W = 2
R = 2
```

Pemeriksaan:

```text
W + R > N
2 + 2 > 3
4 > 3
```

Syarat quorum terpenuhi.

**Skenario Write**

Klien mengirimkan perintah untuk menyimpan data `x = 100` kepada tiga node.

- Node A berhasil menyimpan dan memberikan ACK.
- Node B berhasil menyimpan dan memberikan ACK.
- Node C mengalami keterlambatan atau timeout.

Karena sistem sudah menerima dua ACK dan memenuhi nilai W = 2, operasi write dapat dinyatakan berhasil.

**Skenario Read**

Klien meminta data x dan sistem mengambil respons dari minimal dua node.

Misalnya Node A memberikan nilai terbaru `x = 100`, sedangkan Node C masih memiliki versi lama.

Karena konfigurasi quorum memenuhi irisan antara write quorum dan read quorum, setidaknya terdapat satu node yang termasuk dalam kedua kelompok tersebut.

**[MODIFIKASI]** Konsep quorum membantu sistem menentukan jumlah respons minimum yang diperlukan tanpa harus selalu menunggu seluruh node. Namun, rumus `W + R > N` saja tidak otomatis menjamin seluruh sistem memiliki konsistensi yang benar. Implementasinya tetap perlu memperhatikan versi data, mekanisme pemilihan nilai terbaru, serta aturan penanganan kegagalan dan konflik.

**c. State Machine Replication**

State Machine Replication merupakan pendekatan replikasi dengan menjalankan perintah yang sama dalam urutan yang sama pada beberapa replika.

Tujuannya adalah menjaga agar seluruh replika menghasilkan kondisi akhir yang sama.

Materi memberikan contoh tiga replika A, B, dan C dengan keadaan awal:

```text
x = 10
```

Klien mengirimkan perintah:

```text
SET x = 20
```

Tahapan proses:

1. Klien mengirimkan permintaan kepada leader, yaitu replika A.
2. Leader menetapkan urutan perintah dan menambahkannya ke log.
3. Leader mengirimkan perintah kepada replika B dan C.
4. Leader menerima konfirmasi bahwa perintah telah tersimpan pada log replika sesuai mekanisme yang digunakan.
5. Perintah dinyatakan committed.
6. Seluruh replika menerapkan perintah tersebut pada penyimpanan lokal.

Hasil akhirnya:

```text
Replika A: x = 20
Replika B: x = 20
Replika C: x = 20
```

Dengan demikian, ketiga replika mempunyai keadaan yang sama.

**d. Gossip Protocol**

Gossip Protocol merupakan mekanisme komunikasi ketika node menyebarkan informasi kepada beberapa node lain yang dipilih secara acak. Proses ini berlangsung secara berulang hingga informasi menyebar ke sebagian besar atau seluruh anggota cluster.

Materi memberikan contoh penggunaan Gossip Protocol pada Apache Cassandra.

Gambaran prosesnya:

1. Node A mendeteksi perubahan data atau perubahan kondisi node lain.
2. Node A memilih satu atau beberapa peer secara acak.
3. Node A mengirimkan informasi status kepada peer yang dipilih.
4. Node penerima memperbarui informasi lokalnya.
5. Node tersebut kemudian menyebarkan informasi kepada peer lainnya.
6. Proses berulang sehingga informasi menyebar ke seluruh cluster.

Kelebihan pendekatan ini adalah penyebaran informasi tidak harus selalu bergantung pada satu koordinator pusat.

**e. Chain Replication**

Chain Replication merupakan pendekatan replikasi yang mengatur node dalam bentuk rantai. Pembaruan data diteruskan melalui urutan node dalam rantai tersebut.

Secara umum, operasi tulis diproses melalui node yang berada di bagian awal rantai dan diteruskan ke node berikutnya. Setelah pembaruan mencapai bagian akhir rantai, hasilnya dapat dikonfirmasi sesuai protokol yang digunakan. Pembacaan biasanya dilayani oleh node di bagian akhir rantai.

Pendekatan ini membantu menjaga urutan penerapan pembaruan pada replika. Namun, kinerja dan ketersediaannya bergantung pada komunikasi serta kondisi node yang membentuk rantai.

---

## D. CONTOH PENERAPAN DAN ANALISIS

### 1. Contoh Penerapan

**a. Replikasi Database pada Sistem Perbankan**

Sistem perbankan dapat menggunakan beberapa server database untuk mendukung ketersediaan dan keandalan data. Salinan database dapat ditempatkan pada pusat data yang berbeda agar layanan tidak sepenuhnya bergantung pada satu lokasi.

Ketika terjadi transaksi, sistem harus memastikan perubahan saldo diterapkan sesuai aturan konsistensi yang digunakan. Replikasi membantu menyediakan salinan data, sedangkan mekanisme konsistensi mengatur bagaimana perubahan tersebut disebarkan dan dibaca.

**b. Replikasi pada Aplikasi E-Commerce**

Sebuah aplikasi e-commerce dapat menggunakan beberapa server database untuk melayani pengguna dari berbagai wilayah.

Misalnya server Jakarta melayani pengguna wilayah barat, sedangkan server Yogyakarta melayani pengguna wilayah tengah dan timur. Replikasi memungkinkan data tersedia di beberapa lokasi sehingga permintaan baca dapat dilayani lebih dekat dengan pengguna.

Namun, apabila terdapat perubahan stok secara bersamaan, sistem membutuhkan mekanisme konsistensi dan penanganan konflik agar jumlah stok tidak menjadi tidak sesuai.

**c. Kolaborasi Dokumen Secara Real-Time**

Aplikasi pengeditan dokumen bersama memungkinkan beberapa pengguna melakukan perubahan pada dokumen yang sama.

CRDT atau Operational Transformation dapat digunakan untuk menangani perubahan yang terjadi secara bersamaan. Dengan mekanisme tersebut, perubahan dari setiap pengguna dapat digabungkan sehingga dokumen tidak menghasilkan kondisi yang berbeda pada masing-masing perangkat.

**d. Replikasi pada Database Terdistribusi**

Database seperti Apache Cassandra dapat menggunakan pendekatan replikasi dan Gossip Protocol untuk menyebarkan informasi antar-node.

Dengan mekanisme tersebut, node dapat bertukar informasi mengenai kondisi cluster dan perubahan data sehingga sistem dapat mendukung penyimpanan data pada beberapa server.

**e. Pengelolaan Data pada Cluster**

Sistem yang menggunakan beberapa server dapat menerapkan State Machine Replication untuk memastikan setiap replika menjalankan perintah dalam urutan yang sama.

Contohnya adalah sistem yang memiliki leader untuk menerima permintaan, mengatur urutan perintah, dan menyebarkan log kepada replika lainnya.

**f. Studi Kasus PostgreSQL dan Apache Ignite**

Materi perkuliahan mencantumkan dua studi kasus:

1. PostgreSQL 18 Streaming Replication.
2. Apache Ignite 3 Master-Master.

Kedua teknologi tersebut digunakan sebagai bahan pembahasan mengenai penerapan replikasi dalam sistem nyata.

PostgreSQL Streaming Replication berkaitan dengan pengiriman perubahan dari server utama kepada server standby. Sementara itu, Apache Ignite 3 dibahas dalam konteks replikasi master-master.

Materi PDF mengarahkan mahasiswa untuk mempelajari lebih lanjut melalui lecture notes dan source code yang menyertai perkuliahan. Karena dokumen lecture notes dan source code tersebut tidak termasuk dalam file PDF yang tersedia, detail konfigurasi maupun hasil pengujian implementasinya tidak dijabarkan di sini.

### 2. Analisis

Konsistensi dan replikasi merupakan dua konsep yang saling berkaitan dalam sistem terdistribusi, tetapi mempunyai fungsi yang berbeda.

Replikasi berfungsi menyediakan salinan data pada beberapa node, sedangkan konsistensi mengatur bagaimana perubahan pada salinan tersebut diterapkan dan dilihat oleh pengguna.

Semakin banyak replika yang dimiliki, semakin besar pula kebutuhan komunikasi untuk menyebarkan perubahan. Oleh karena itu, sistem perlu menentukan strategi replikasi yang sesuai dengan kebutuhan aplikasi.

Pada sistem yang mengutamakan ketepatan data, seperti perbankan, konsistensi menjadi hal yang sangat penting. Sistem tidak boleh sembarangan memberikan informasi saldo yang belum mencerminkan transaksi terakhir. Sebaliknya, pada aplikasi yang menampilkan informasi dengan dampak kesalahan lebih rendah, seperti jumlah tayangan atau statistik pengunjung, keterlambatan sinkronisasi sementara mungkin masih dapat diterima.

Pemilihan model replikasi juga perlu disesuaikan dengan kondisi sistem. Master-Slave relatif mudah dikelola karena penulisan data dilakukan melalui satu node utama, tetapi dapat menimbulkan ketergantungan terhadap master. Multi-Master lebih fleksibel karena beberapa node dapat menerima perubahan, tetapi membutuhkan mekanisme penanganan konflik yang lebih baik.

Strategi sinkronisasi juga memengaruhi kinerja. Synchronous Replication memberikan jaminan bahwa replika tertentu telah menerima perubahan sebelum operasi selesai, tetapi dapat meningkatkan latensi. Asynchronous Replication lebih cepat karena tidak harus menunggu replika, tetapi memiliki risiko kehilangan perubahan yang belum sempat disebarkan ketika terjadi kegagalan.

Quorum-Based menjadi salah satu pendekatan untuk menentukan jumlah node yang harus memberikan konfirmasi. Sementara itu, State Machine Replication menekankan pentingnya menjalankan perintah dalam urutan yang sama pada seluruh replika.

CRDT dan Operational Transformation juga menunjukkan bahwa konflik dapat ditangani dengan pendekatan yang berbeda. CRDT menggunakan struktur data dan aturan penggabungan, sedangkan OT melakukan transformasi terhadap operasi yang saling bertabrakan.

**[MODIFIKASI]** Berdasarkan keseluruhan materi, tidak ada satu metode replikasi atau model konsistensi yang selalu paling baik untuk semua aplikasi. Pengembang perlu mempertimbangkan kebutuhan bisnis, jumlah pengguna, lokasi server, latensi jaringan, risiko kegagalan, serta tingkat ketepatan data yang harus dipertahankan. Pemilihan yang tepat dapat membantu sistem tetap cepat, tersedia, dan dapat dipercaya.

---

## E. PENGGUNAAN ARTIFICIAL INTELLIGENCE (AI)

### 1. AI yang Digunakan

- Nama AI: ChatGPT GPT-6
- Tujuan penggunaan: Membantu memahami, menganalisis, menyusun, dan mengembangkan rangkuman materi perkuliahan.
- Sumber utama: Materi perkuliahan yang diberikan oleh dosen, yaitu file `04--konsistensi-dan-replikasi (1).pdf`.

### 2. Prompt yang Digunakan

Berikut prompt yang digunakan untuk menghasilkan rangkuman:

> Analisis seluruh isi file PDF materi Teori Sistem Terdistribusi dan Terdesentralisasi pertemuan 4 yang saya lampirkan. Susun rangkuman lengkap dalam format Markdown dengan mengikuti template README bagian A sampai G yang telah saya berikan.
>
> Gunakan materi dosen sebagai sumber utama dan pertahankan istilah serta konsep sesuai materi. Kembangkan penjelasan agar mudah dipahami, tambahkan contoh penerapan yang relevan dengan bidang Informatika, serta berikan analisis terhadap konsep yang dibahas.
>
> Pastikan pembahasan mencakup pengertian konsistensi, pentingnya konsistensi, Teorema CAP, model konsistensi, trade-off latensi dan konsistensi, pengertian replikasi data, jenis replikasi, strategi sinkronisasi replika, penanganan konflik menggunakan LWW, Vector Clocks, CRDT dan OT, serta protokol replikasi seperti Primary-Based, Quorum-Based, State Machine Replication, Gossip Protocol, dan Chain Replication.
>
> Sertakan contoh perhitungan quorum dan contoh penggabungan data menggunakan CRDT sesuai materi. Jelaskan studi kasus PostgreSQL 18 Streaming Replication dan Apache Ignite 3 Master-Master hanya berdasarkan informasi yang tersedia. Jika lecture notes atau source code pendukung tidak tersedia, jangan mengarang hasil implementasinya.
>
> Gunakan bahasa Indonesia yang natural seperti laporan mahasiswa S1 Informatika, bukan bahasa yang terlalu kaku. Jangan mengarang fakta atau referensi. Berikan hasil akhir berupa README lengkap yang siap dimasukkan ke repository GitHub.

### 3. Bagian yang Disesuaikan dari Keluaran AI

Bagian dari hasil rangkuman yang dikembangkan atau disesuaikan meliputi:

1. **Pengertian dan Model Konsistensi:** Penjelasan diperluas dengan membandingkan Strong Consistency, Eventual Consistency, Causal Consistency, Read-Your-Writes, Monotonic Read, Sequential Consistency, dan Linearizability beserta contoh penerapannya.
2. **Teorema CAP dan Trade-off Latensi:** Pembahasan dikembangkan dengan menggunakan contoh aplikasi e-commerce dan dua pusat data agar hubungan antara konsistensi, ketersediaan, toleransi partisi, serta waktu respons lebih mudah dipahami.
3. **Jenis dan Strategi Replikasi:** Penjelasan mengenai Master-Slave, Multi-Master, Synchronous, Asynchronous, Semi-Synchronous, Pull-Based, Push-Based, dan Hybrid disusun dengan membandingkan cara kerja serta kelebihan dan keterbatasannya.
4. **Penanganan Konflik dan Protokol Replikasi:** Contoh CRDT, Operational Transformation, Quorum-Based, State Machine Replication, Gossip Protocol, dan Chain Replication dikembangkan dengan penjelasan tahapan kerja dan contoh yang sesuai dengan materi.

Penyesuaian dilakukan untuk memperjelas pemahaman materi, memperbaiki penjelasan yang kurang lengkap, serta menambahkan contoh dan analisis yang relevan dengan bidang Informatika.

### 4. Penanda Hasil Modifikasi

Bagian yang mengalami pengembangan atau penyesuaian dari hasil awal AI diberikan tanda **[MODIFIKASI]** pada bagian terkait dalam rangkuman.

Keterangan:
- **[MODIFIKASI]**: Bagian yang mengalami pengembangan, penambahan penjelasan, perbaikan, atau penyesuaian.
- Bagian tanpa tanda: Bagian yang dipertahankan karena sudah sesuai dengan materi dan tidak memerlukan perubahan substantif.

---

## F. KESIMPULAN

Berdasarkan materi pertemuan keempat, konsistensi dan replikasi merupakan dua hal penting dalam membangun sistem terdistribusi yang andal. Konsistensi berfungsi menjaga agar perubahan data dapat dilihat sesuai aturan yang ditetapkan, sedangkan replikasi menyediakan salinan data pada beberapa node untuk meningkatkan ketersediaan, kinerja, dan keandalan sistem.

Materi ini membahas Teorema CAP, berbagai model konsistensi, serta trade-off antara konsistensi dan latensi. Selain itu, terdapat beberapa jenis dan strategi replikasi, seperti Master-Slave, Multi-Master, Synchronous, Asynchronous, dan Semi-Synchronous. Sistem juga membutuhkan mekanisme penanganan konflik seperti Last Write Wins, Vector Clocks, CRDT, dan Operational Transformation agar perubahan yang terjadi pada beberapa replika dapat dikelola dengan baik.

Berbagai protokol replikasi seperti Primary-Based, Quorum-Based, State Machine Replication, Gossip Protocol, dan Chain Replication memiliki mekanisme kerja serta karakteristik yang berbeda. Pemilihan protokol perlu disesuaikan dengan kebutuhan dan kondisi sistem yang dibangun.

Dengan mempelajari materi ini, mahasiswa dapat memahami bagaimana data dikelola pada beberapa server, bagaimana perubahan disebarkan, serta bagaimana sistem mempertahankan konsistensi ketika terjadi gangguan jaringan atau perubahan secara bersamaan. Pengetahuan tersebut menjadi dasar penting dalam pengembangan database terdistribusi, aplikasi berbasis cloud, dan layanan digital yang membutuhkan ketersediaan serta keandalan tinggi.

---

## G. DAFTAR REFERENSI

1. Purnomosidi, B. (Tanpa tahun). *04: Konsistensi dan Replikasi pada Sistem Terdistribusi*. Materi Perkuliahan Teori Sistem Terdistribusi dan Terdesentralisasi, Program Studi Informatika, Fakultas Teknologi Informasi, Universitas Teknologi Digital Indonesia.
2. Apache Cassandra. (Tanpa tahun). *Apache Cassandra Documentation*. https://cassandra.apache.org/doc/
3. PostgreSQL Global Development Group. (Tanpa tahun). *PostgreSQL Documentation*. https://www.postgresql.org/docs/
4. Apache Ignite. (Tanpa tahun). *Apache Ignite Documentation*. https://ignite.apache.org/docs/

---

**Dokumentasi Tugas**

- Repository: [disdec-teori](https://github.com/hendfirmsh/disdec-teori)
- Direktori: `04/`
- File: `README.md`

---
