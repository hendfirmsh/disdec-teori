# RANGKUMAN MATERI TEORI SISTEM TERDISTRIBUSI DAN TERDESENTRALISASI

## PERTEMUAN 05

---

## A. IDENTITAS MATERI

| Keterangan | Informasi |
|---|---|
| Mata Kuliah | Teori Sistem Terdistribusi dan Terdesentralisasi |
| Pertemuan | Pertemuan ke-5 |
| Topik Materi | Fault Tolerance |
| Sumber Materi | 05--fault-tolerant-sys (1).pdf |
| AI yang Digunakan | ChatGPT GPT-6 |
| Format Dokumen | Markdown (.md) |

---

## B. TUJUAN PEMBELAJARAN

Setelah mempelajari materi pertemuan ini, mahasiswa diharapkan mampu:

1. Memahami dan menjelaskan alasan *fault tolerance* diperlukan dalam sistem terdistribusi dan terdesentralisasi.
2. Memahami pengertian *fault tolerance* dan *fault tolerant systems*.
3. Menjelaskan berbagai jenis *fault* yang dapat terjadi dalam sistem teknologi informasi.
4. Memahami klasifikasi *fault* berdasarkan sumber penyebabnya.
5. Memahami berbagai *design patterns* untuk mencapai *fault tolerance* serta penerapannya menggunakan Python.
6. Memahami bagaimana berbagai bahasa pemrograman dan perangkat pengembangan menyediakan mekanisme untuk menerapkan *fault tolerance*.

---

## C. RANGKUMAN MATERI

### 1. Pengertian Fault Tolerance

*Fault tolerance* adalah kemampuan suatu sistem untuk tetap menjalankan operasionalnya dengan baik meskipun terjadi kegagalan atau kesalahan pada satu atau beberapa komponen di dalam sistem tersebut.

Dalam sistem teknologi informasi, kegagalan dapat terjadi pada perangkat keras, perangkat lunak, maupun koneksi jaringan. Oleh karena itu, sistem perlu dirancang agar tidak langsung berhenti bekerja ketika salah satu komponennya mengalami masalah.

Konsep ini sangat penting terutama pada sistem yang membutuhkan *high availability*, *mission critical system*, dan *life-critical system*. Contohnya adalah layanan perbankan, layanan penyimpanan data, dan sistem yang digunakan untuk mendukung aktivitas penting.

**[MODIFIKASI]** Hal yang perlu dipahami adalah bahwa *fault tolerance* bukan berarti sistem tidak akan pernah mengalami kegagalan. Kegagalan tetap mungkin terjadi, tetapi sistem dirancang agar dampaknya dapat dikurangi dan layanan tetap dapat berjalan atau dipulihkan dengan cepat.

### 2. Pentingnya Fault Tolerance pada Sistem Terdistribusi dan Terdesentralisasi

Sistem terdistribusi dan terdesentralisasi terdiri dari banyak komponen yang saling berhubungan dan bekerja sama. Komponen tersebut dapat berada pada perangkat atau lokasi yang berbeda serta berkomunikasi melalui jaringan.

Karena melibatkan banyak komponen, kemungkinan terjadinya gangguan juga semakin beragam. Sebagai contoh, sebuah server dapat mengalami kerusakan, aplikasi mengalami kesalahan, atau koneksi jaringan terputus sehingga komunikasi antarserver terganggu.

Semakin penting suatu aplikasi, semakin tinggi pula tuntutan agar aplikasi tersebut tetap berfungsi dengan baik. Hal ini berkaitan dengan kebutuhan *high availability*, yaitu kemampuan sistem untuk tetap menyediakan layanan ketika terjadi gangguan.

Oleh karena itu, *fault tolerance* diperlukan agar kegagalan pada satu komponen tidak selalu menyebabkan seluruh sistem berhenti beroperasi.

### 3. Jenis-Jenis Fault

Berdasarkan materi perkuliahan, terdapat beberapa jenis *fault* yang dapat terjadi dalam suatu sistem.

#### a. Transient Fault

*Transient fault* merupakan kegagalan yang terjadi sementara dan tidak berlangsung secara permanen. Gangguan ini dapat muncul akibat kondisi tertentu, kemudian menghilang setelah penyebabnya tidak lagi terjadi.

Contoh yang diberikan dalam materi adalah gangguan akibat petir.

#### b. Intermittent Fault

*Intermittent fault* merupakan kegagalan yang muncul dan menghilang secara berulang. Artinya, suatu komponen terkadang dapat bekerja normal, tetapi pada kondisi tertentu kembali mengalami gangguan.

Contohnya adalah perangkat keras yang mengalami *overheat*. Ketika suhu meningkat, perangkat dapat mengalami gangguan, kemudian kembali bekerja setelah suhunya turun.

#### c. Permanent Fault

*Permanent fault* merupakan kegagalan yang bersifat tetap atau berlangsung terus-menerus. Komponen yang mengalami kegagalan ini tidak dapat kembali berfungsi secara normal tanpa adanya perbaikan atau penggantian.

#### d. Byzantine Fault

*Byzantine fault* merupakan kondisi ketika suatu komponen memberikan hasil yang acak atau tidak konsisten. Kondisi ini lebih sulit ditangani karena komponen yang bermasalah tidak selalu berhenti bekerja, tetapi justru dapat mengirimkan informasi yang berbeda atau tidak dapat dipercaya kepada komponen lain.

**[MODIFIKASI]** Perbedaan utama dari keempat jenis *fault* tersebut terletak pada pola terjadinya kegagalan. *Transient fault* terjadi sementara, *intermittent fault* muncul berulang, *permanent fault* bersifat tetap, sedangkan *Byzantine fault* berkaitan dengan perilaku komponen yang memberikan informasi tidak konsisten.

### 4. Klasifikasi Fault Berdasarkan Sumbernya

Selain dibedakan berdasarkan jenisnya, *fault* juga dapat dikelompokkan berdasarkan sumber penyebabnya.

#### a. Hardware Faults

*Hardware faults* merupakan kegagalan yang berasal dari perangkat keras komputer atau infrastruktur fisik.

Contohnya:
- Kerusakan atau *crash* pada hard disk.
- Gangguan atau terputusnya sumber daya listrik (*power failure*).
- Kerusakan pada komponen perangkat keras server.

#### b. Software Faults

*Software faults* merupakan kegagalan yang berasal dari perangkat lunak atau program yang dijalankan oleh sistem.

Contohnya:
- *Bugs* atau kesalahan dalam kode program.
- *Memory leak*, yaitu kondisi ketika penggunaan memori terus bertambah karena memori yang tidak lagi diperlukan tidak dilepaskan dengan benar.
- *Race condition*, yaitu kondisi ketika hasil program dipengaruhi oleh urutan atau waktu eksekusi beberapa proses yang berjalan bersamaan.

#### c. Communication Faults

*Communication faults* merupakan kegagalan yang terjadi pada proses komunikasi antarbagian sistem melalui jaringan.

Contohnya:
- *Packet loss*, yaitu kondisi ketika paket data hilang dalam proses pengiriman.
- *Network partition*, yaitu kondisi ketika jaringan terpisah sehingga beberapa bagian sistem tidak dapat saling berkomunikasi.

Ketiga klasifikasi tersebut menunjukkan bahwa sumber kegagalan tidak hanya berasal dari perangkat keras, tetapi juga dapat muncul dari perangkat lunak dan komunikasi jaringan.

### 5. Teknik untuk Mencapai Fault Tolerance

Untuk mempertahankan operasional sistem ketika terjadi kegagalan, terdapat beberapa teknik yang dapat digunakan.

#### a. Redundansi dan Replikasi

Redundansi merupakan penyediaan sumber daya atau komponen cadangan agar sistem tidak hanya bergantung pada satu komponen. Salah satu cara menerapkannya adalah melalui replikasi, yaitu menyediakan salinan data atau layanan pada beberapa node.

Tujuan utamanya adalah menghindari *single point of failure*, yaitu kondisi ketika kegagalan pada satu komponen dapat menyebabkan seluruh layanan berhenti.

Sebagai contoh, sebuah aplikasi dapat memiliki beberapa server yang menyediakan layanan serupa. Ketika salah satu server mengalami gangguan, server lain dapat digunakan untuk membantu mempertahankan layanan.

Teknik ini berkaitan dengan materi pertemuan sebelumnya mengenai konsistensi dan replikasi data.

#### b. Load Balancing

*Load balancing* merupakan proses membagi beban permintaan ke beberapa *instance* aplikasi yang aktif.

Dalam materi dijelaskan bahwa satu *instance* merupakan satu proses aplikasi penuh yang sedang berjalan. Untuk mengatur pembagian permintaan tersebut, sistem dapat menggunakan *load balancer* seperti HAProxy dan Nginx.

Dengan beberapa *instance* aplikasi, permintaan pengguna tidak harus ditangani oleh satu server saja. Beban kerja dapat dibagi sehingga penggunaan sumber daya menjadi lebih seimbang.

**[MODIFIKASI]** Load balancing dapat membantu meningkatkan ketersediaan layanan apabila dikombinasikan dengan mekanisme pemeriksaan kondisi server. Namun, load balancing sendiri tidak otomatis menjamin *fault tolerance*, karena komponen load balancer juga perlu diperhatikan agar tidak menjadi titik kegagalan tunggal.

#### c. Checkpointing dan Rollback Recovery

*Checkpointing* adalah proses menyimpan status sistem secara berkala ke media penyimpanan.

Sementara itu, *rollback recovery* merupakan proses mengembalikan sistem ke status *checkpoint* yang telah disimpan sebelumnya setelah terjadi kegagalan.

Kedua teknik ini memungkinkan sistem melanjutkan pekerjaan dari kondisi yang pernah disimpan, bukan harus memulai seluruh proses dari awal.

Tujuannya adalah mengurangi kehilangan data dan meminimalkan waktu pemrosesan yang terbuang akibat kegagalan.

Contohnya, aplikasi yang sedang melakukan pemrosesan data dalam jumlah besar dapat menyimpan status pekerjaannya secara berkala. Jika terjadi gangguan, proses dapat dilanjutkan dari status penyimpanan terakhir yang tersedia.

#### d. Heartbeat dan Failure Detection

*Heartbeat* merupakan sinyal yang dikirim secara periodik antar-komponen untuk menunjukkan bahwa suatu komponen masih aktif.

Sedangkan *failure detection* merupakan proses untuk menentukan apakah suatu komponen mengalami kegagalan dengan memantau sinyal *heartbeat* tersebut.

Jika komponen pemantau tidak menerima *heartbeat* dari komponen lain dalam jangka waktu tertentu, komponen tersebut dapat diasumsikan mengalami kegagalan atau tidak responsif.

Pola ini penting dalam sistem terdistribusi karena memungkinkan sistem mendeteksi gangguan dan mengambil tindakan penanganan.

Dalam materi, dosen juga menyebutkan contoh program `check-server.py` untuk melakukan pengecekan komponen secara sederhana. Untuk kebutuhan diagnostik yang lebih lanjut, diperlukan program dengan kemampuan yang lebih kompleks.

#### e. Retry dan Library Tenacity

Dalam sistem terdistribusi, aplikasi sering berkomunikasi dengan komponen di luar aplikasi itu sendiri. Komunikasi tersebut memiliki kemungkinan gagal, misalnya karena jaringan terganggu atau layanan tujuan sementara tidak dapat diakses.

Salah satu pendekatan untuk menangani kondisi tersebut adalah *retry*, yaitu mencoba kembali suatu operasi setelah percobaan sebelumnya mengalami kegagalan.

Materi perkuliahan menyebutkan library **Tenacity** yang dapat digunakan untuk mengelola proses yang membutuhkan komunikasi dengan komponen eksternal.

Materi juga merujuk pada contoh file `check-retry.py` sebagai bahan untuk melihat penerapan mekanisme tersebut.

**[MODIFIKASI]** Retry sebaiknya digunakan secara terukur. Jika aplikasi terus mengulang permintaan tanpa batas, justru dapat menambah beban pada layanan yang sedang bermasalah. Oleh karena itu, penerapannya perlu mempertimbangkan jumlah percobaan dan jeda antarpercobaan.

#### f. Circuit Breaker

*Circuit breaker* merupakan pola desain yang digunakan dalam sistem, khususnya microservices, untuk mencegah kegagalan pada satu layanan menyebabkan kegagalan berantai pada layanan lainnya.

Pola ini bekerja seperti *state machine* yang memiliki tiga status utama:

1. **Closed**: Permintaan masih diizinkan dan kegagalan akan dipantau. Jika jumlah kegagalan mencapai batas yang ditentukan, sistem berpindah ke status *open*.
2. **Open**: Permintaan ke layanan yang bermasalah sementara ditolak agar layanan tersebut memiliki waktu untuk pulih.
3. **Half-Open**: Setelah waktu tertentu, sistem mengizinkan sejumlah permintaan terbatas untuk menguji apakah layanan sudah kembali normal.

Jika permintaan pengujian berhasil, *circuit breaker* kembali ke status *closed*. Namun, jika masih gagal, sistem kembali ke status *open*.

Dengan demikian, *circuit breaker* membantu mencegah aplikasi terus-menerus mengirim permintaan ke layanan yang sedang mengalami gangguan.

#### g. Consensus dan Coordination

*Consensus* merupakan proses ketika beberapa node menyepakati satu nilai, status, atau urutan operasi meskipun terdapat kegagalan dan keterlambatan jaringan.

Sementara itu, *coordination* merupakan praktik yang lebih luas dalam mengatur interaksi antar-node agar dapat bekerja sama secara efektif dan konsisten.

Dalam sistem terdistribusi, *coordination* sering melibatkan *consensus* sebagai salah satu komponen penting.

Contoh penerapannya berdasarkan materi:

- **Database Leader Election**: Dalam kluster basis data yang menggunakan replikasi, sistem perlu menentukan node yang bertugas sebagai *leader* untuk menangani operasi penulisan. Algoritma konsensus seperti Raft dapat digunakan dalam proses tersebut.
- **Cloud Storage File Updates**: Ketika sebuah file diperbarui pada layanan penyimpanan cloud seperti Google Drive, mekanisme konsensus dapat digunakan untuk memastikan perubahan disetujui oleh mayoritas server sebelum dianggap final. Setelah itu, perubahan dapat direplikasi ke server lainnya.
- **Cryptocurrency dan Blockchain**: Teknologi blockchain menggunakan mekanisme konsensus untuk memvalidasi dan menyepakati transaksi.

### 6. Actor Model untuk Supervisi Proses

*Actor Model* merupakan pendekatan dalam pemrograman konkuren dan sistem terdistribusi yang menggunakan aktor sebagai unit pemrosesan. Aktor dapat bekerja secara independen dan berkomunikasi melalui pengiriman pesan.

Dalam konteks *fault tolerance*, konsep ini berkaitan dengan mekanisme supervisi proses, yaitu pengawasan terhadap proses atau aktor lain agar kegagalan dapat diketahui dan ditangani.

Salah satu pola yang berkaitan dengan pendekatan ini adalah **Supervisor-Worker**. Pada pola tersebut, *worker* menjalankan tugas tertentu, sedangkan *supervisor* bertugas mengawasi proses yang dijalankan oleh *worker*.

Jika suatu proses mengalami kegagalan, supervisor dapat menjalankan strategi penanganan yang sesuai, misalnya memulai ulang proses yang bermasalah.

**[MODIFIKASI]** Sebagai gambaran sederhana, sebuah aplikasi dapat memiliki satu supervisor yang mengawasi beberapa worker. Jika salah satu worker berhenti akibat kesalahan, supervisor dapat mendeteksi kondisi tersebut dan menjalankan tindakan pemulihan tanpa harus menghentikan seluruh aplikasi. Penjelasan ini merupakan gambaran konsep, bukan rincian implementasi dari diagram pada slide.

### 7. Implementasi Fault Tolerance pada Berbagai Bahasa Pemrograman

Materi perkuliahan menjelaskan bahwa beberapa bahasa pemrograman telah menyediakan dukungan untuk membangun sistem yang memiliki mekanisme *fault tolerance*.

#### a. Erlang dan Elixir

Erlang dan Elixir memiliki mekanisme bawaan untuk menerapkan *Actor Model* serta pola **Supervisor-Worker**.

Dukungan tersebut dapat digunakan untuk membangun aplikasi yang terdiri dari banyak proses dan memiliki mekanisme pengawasan serta pemulihan ketika terjadi kegagalan.

#### b. Pony

Pony merupakan bahasa pemrograman yang secara khusus mengembangkan pendekatan *Actor Model*. Informasi mengenai bahasa ini dapat ditemukan melalui situs resminya, yaitu https://www.ponylang.io.

#### c. Python

Dalam materi disebutkan beberapa library Python yang dapat digunakan untuk mendukung *fault tolerance*, antara lain:

- **Xoscar**: Library yang berkaitan dengan penerapan sistem berbasis aktor.
- **Tenacity**: Library untuk mengelola mekanisme percobaan ulang (*retry*).
- **Circuit Breaker**: Pola atau library yang dapat digunakan untuk mengatur pemanggilan layanan ketika terjadi kegagalan.

#### d. Java

Beberapa perangkat pengembangan yang disebutkan dalam materi untuk bahasa Java adalah:

- **Apache Pekko**: Dapat digunakan untuk menerapkan *Actor Model* dan pola Supervisor-Worker.
- **Resilience4j**: Library yang menyediakan mekanisme untuk membantu membangun aplikasi yang lebih tahan terhadap kegagalan.

#### e. Bahasa Pemrograman Lain

Materi juga mendorong mahasiswa untuk mencari berbagai library pendukung *fault tolerance* pada bahasa pemrograman lainnya. Contohnya adalah melalui npm untuk JavaScript dan crates.io untuk Rust.

Dengan adanya berbagai library tersebut, pengembang dapat memilih mekanisme penanganan kegagalan sesuai kebutuhan aplikasi dan bahasa pemrograman yang digunakan.

---

## D. CONTOH PENERAPAN DAN ANALISIS

### 1. Contoh Penerapan

Berikut beberapa contoh penerapan konsep *fault tolerance* dalam bidang teknologi informasi.

#### a. Sistem Perbankan

Sistem perbankan membutuhkan layanan yang dapat diakses dan beroperasi dengan baik. Apabila satu server mengalami kerusakan, server lain yang memiliki salinan data atau layanan dapat membantu mempertahankan operasional sistem.

Konsep yang berkaitan adalah redundansi, replikasi, dan mekanisme pemulihan ketika terjadi kegagalan.

#### b. Aplikasi Berbasis Microservices

Dalam aplikasi yang menggunakan arsitektur microservices, satu layanan dapat bergantung pada layanan lainnya. Jika suatu layanan mengalami gangguan, permintaan yang terus dikirimkan dapat menyebabkan masalah pada layanan lain.

Pola *circuit breaker* dapat digunakan untuk menghentikan sementara permintaan ke layanan yang bermasalah. Sementara itu, mekanisme *retry* dapat digunakan untuk mencoba kembali operasi yang gagal secara terukur.

#### c. Aplikasi dengan Banyak Server

Sebuah aplikasi yang diakses banyak pengguna dapat dijalankan pada beberapa *instance* server. Load balancer kemudian membagikan permintaan pengguna ke beberapa instance tersebut.

Pendekatan ini membantu membagi beban kerja dan dapat mendukung ketersediaan layanan ketika salah satu instance mengalami gangguan, selama sistem memiliki mekanisme untuk mendeteksi dan menghindari instance yang bermasalah.

#### d. Sistem Pemrosesan Data

Aplikasi yang memerlukan waktu lama untuk memproses data dapat menerapkan *checkpointing*. Status pemrosesan disimpan secara berkala sehingga ketika terjadi kegagalan, proses dapat dilanjutkan dari status terakhir yang tersimpan.

#### e. Kluster Basis Data

Dalam kluster basis data, beberapa node bekerja sama untuk menyediakan layanan penyimpanan data. Sistem dapat menggunakan mekanisme *leader election* dan konsensus seperti Raft untuk menentukan node yang bertanggung jawab menangani operasi tertentu.

### 2. Analisis

Berdasarkan materi pertemuan ini, *fault tolerance* merupakan bagian penting dalam perancangan sistem terdistribusi karena sistem memiliki banyak komponen yang saling bergantung. Semakin banyak komponen yang digunakan, semakin banyak pula kemungkinan gangguan yang harus diantisipasi.

Setiap teknik memiliki fungsi yang berbeda. Redundansi dan replikasi menyediakan komponen atau sumber daya cadangan, sedangkan load balancing membantu membagi beban kerja. Checkpointing dan rollback recovery membantu memulihkan proses setelah kegagalan. Heartbeat digunakan untuk memantau kondisi komponen, sementara retry dan circuit breaker membantu menangani kegagalan komunikasi dengan layanan lain.

Di sisi lain, consensus dan coordination diperlukan ketika beberapa node harus menyepakati suatu keputusan atau urutan operasi. Actor Model dan pola Supervisor-Worker dapat membantu mengatur proses serta menangani kegagalan pada tingkat proses atau aktor.

Dari berbagai teknik tersebut, dapat dipahami bahwa tidak ada satu metode yang selalu cukup untuk semua jenis kegagalan. Pengembang perlu memilih dan menggabungkan beberapa pendekatan sesuai kebutuhan sistem. Dengan penerapan yang tepat, sistem dapat menjadi lebih andal, mengurangi dampak gangguan, dan mempertahankan ketersediaan layanan.

---

## E. PENGGUNAAN ARTIFICIAL INTELLIGENCE (AI)

### 1. AI yang Digunakan

- Nama AI: ChatGPT GPT-6.
- Tujuan penggunaan: Membantu memahami, menyusun, dan mengembangkan rangkuman materi perkuliahan.
- Sumber utama: Materi perkuliahan yang diberikan oleh dosen dalam bentuk PDF.
- Bentuk penggunaan: Membantu mengidentifikasi pokok bahasan, menyusun penjelasan, dan mengembangkan contoh penerapan berdasarkan materi.

### 2. Prompt yang Digunakan

Berikut prompt yang digunakan untuk menghasilkan rangkuman awal:

> Saya merupakan mahasiswa S1 Informatika yang sedang mengerjakan tugas rangkuman mata kuliah Teori Sistem Terdistribusi dan Terdesentralisasi pertemuan ke-5. Baca dan pelajari seluruh isi PDF yang saya lampirkan dengan teliti, kemudian buat rangkuman berdasarkan materi tersebut.
>
> Gunakan struktur berikut:
> A. Identitas Materi
> B. Tujuan Pembelajaran
> C. Rangkuman Materi
> D. Contoh Penerapan dan Analisis
> E. Penggunaan Artificial Intelligence (AI)
> F. Kesimpulan
> G. Daftar Referensi
>
> Pada bagian rangkuman materi, susun subbab berdasarkan pokok bahasan yang benar-benar terdapat dalam PDF. Jangan memaksakan jumlah subbab yang sama untuk setiap pertemuan.
>
> Jelaskan setiap konsep menggunakan bahasa Indonesia yang natural, jelas, dan mudah dipahami mahasiswa. Pertahankan istilah teknis yang digunakan dalam materi, kemudian berikan penjelasan tambahan jika diperlukan agar konsep lebih mudah dipahami.
>
> Sertakan contoh penerapan dan analisis yang relevan dengan bidang Informatika. Jangan mengarang informasi, kode program, hasil pengujian, atau detail implementasi yang tidak tersedia dalam sumber. Jika materi hanya menyebutkan nama file atau program pendukung tetapi file tersebut tidak dilampirkan, jelaskan keterbatasan tersebut.
>
> Berikan tanda **[MODIFIKASI]** pada bagian yang mendapatkan pengembangan penjelasan, tambahan contoh, atau analisis dari hasil awal AI. Pastikan isi rangkuman tetap sesuai dengan materi dosen dan tidak menggantikan pokok pembahasan aslinya.
>
> Buat hasil akhir dalam format Markdown yang siap disimpan sebagai README.md di GitHub.

### 3. Bagian yang Disesuaikan dari Keluaran AI

Bagian dari hasil AI yang dikembangkan atau disesuaikan meliputi:

1. **Pengertian dan Jenis Fault**: Penjelasan mengenai perbedaan *transient fault*, *intermittent fault*, *permanent fault*, dan *Byzantine fault* dikembangkan agar karakteristik setiap jenis kegagalan lebih mudah dipahami.
2. **Teknik Fault Tolerance**: Penjelasan mengenai redundansi, replikasi, load balancing, checkpointing, heartbeat, retry, dan circuit breaker dikembangkan dengan memberikan gambaran fungsi masing-masing teknik.
3. **Consensus dan Actor Model**: Penjelasan mengenai proses kesepakatan antar-node serta supervisi proses dikembangkan agar hubungannya dengan penanganan kegagalan lebih mudah dipahami.
4. **Contoh Penerapan dan Analisis**: Ditambahkan contoh penerapan dalam sistem perbankan, microservices, aplikasi dengan banyak server, pemrosesan data, dan kluster basis data untuk menghubungkan teori dengan penggunaan teknologi informasi.

Penyesuaian dilakukan untuk memperjelas pemahaman materi, mengembangkan penjelasan yang masih singkat pada slide, serta memberikan contoh penerapan yang relevan.

### 4. Penanda Hasil Modifikasi

Bagian yang mengalami pengembangan atau penyesuaian dari hasil awal AI diberikan tanda **[MODIFIKASI]** pada bagian terkait dalam rangkuman.

Keterangan:

- **[MODIFIKASI]**: Bagian yang mengalami pengembangan, penambahan penjelasan, perbaikan, atau penyesuaian.
- Bagian tanpa tanda: Bagian yang dipertahankan karena sudah sesuai dengan materi dan tidak memerlukan perubahan substantif.

---

## F. KESIMPULAN

Berdasarkan materi pertemuan ke-5, dapat disimpulkan bahwa *fault tolerance* merupakan kemampuan sistem untuk tetap beroperasi dengan baik meskipun terjadi kegagalan pada satu atau beberapa komponennya. Konsep ini sangat penting dalam sistem terdistribusi dan terdesentralisasi karena sistem tersebut melibatkan banyak komponen yang saling berkomunikasi dan memiliki kemungkinan mengalami gangguan.

Beberapa konsep penting yang perlu diperhatikan adalah jenis-jenis *fault*, klasifikasi kegagalan berdasarkan sumbernya, serta berbagai teknik untuk mencapai *fault tolerance*. Teknik tersebut meliputi redundansi dan replikasi, load balancing, checkpointing dan rollback recovery, heartbeat dan failure detection, retry, circuit breaker, consensus, serta Actor Model untuk supervisi proses.

Penerapan *fault tolerance* memberikan manfaat dalam meningkatkan keandalan sistem, mengurangi dampak kegagalan, dan mempertahankan ketersediaan layanan. Dalam bidang Informatika, pemahaman ini menjadi bekal penting bagi mahasiswa ketika merancang dan mengembangkan aplikasi, layanan berbasis microservices, kluster basis data, maupun sistem terdistribusi lainnya.

Dengan memahami berbagai teknik tersebut, pengembang dapat merancang sistem yang tidak hanya mampu menjalankan fungsi normalnya, tetapi juga memiliki mekanisme untuk menghadapi dan memulihkan diri ketika terjadi gangguan.

---

## G. DAFTAR REFERENSI

1. Purnomosidi D. P., Bambang. (Tanpa tahun). *Fault Tolerance: Materi Perkuliahan Teori Sistem Terdistribusi dan Terdesentralisasi*. Fakultas Teknologi Informasi, Universitas Teknologi Digital Indonesia.
2. Tenacity. (Tanpa tahun). *Tenacity – Retrying Library for Python*. https://github.com/jd/tenacity
3. Pony Language. (Tanpa tahun). *The Pony Programming Language*. https://www.ponylang.io
4. Resilience4j. (Tanpa tahun). *Resilience4j*. https://github.com/resilience4j/resilience4j
5. Xoscar. (Tanpa tahun). *Xoscar Documentation*. https://xoscar.dev

Catatan: Referensi nomor 2–5 merupakan sumber atau perangkat yang disebutkan dalam materi perkuliahan. Rangkuman utama disusun berdasarkan PDF yang diberikan oleh dosen.

---

**Dokumentasi Tugas**

- Repository: [disdec-teori](https://github.com/hendfirmsh/disdec-teori)
- Direktori: `05/`
- File: `README.md`

---
