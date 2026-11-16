# RANGKUMAN MATERI TEORI SISTEM TERDISTRIBUSI DAN TERDESENTRALISASI

# PERTEMUAN 1 — PENGENALAN SISTEM TERDISTRIBUSI DAN TERDESENTRALISASI

---

## A. IDENTITAS MATERI

| Keterangan | Informasi |
|---|---|
| Mata Kuliah | Teori Sistem Terdistribusi dan Terdesentralisasi |
| Program Studi | S1 Informatika |
| Kode Mata Kuliah | FIF25002T |
| SKS | 3 SKS |
| Pertemuan | 1 |
| Topik Materi | Pengenalan Sistem Terdistribusi dan Terdesentralisasi |
| Dosen Pengampu | Dr. Bambang Purnomosidi D. P. |
| Institusi | Universitas Teknologi Digital Indonesia (UTDI) |
| Sumber Materi | 01 - Pengenalan.pdf |
| AI yang Digunakan | ChatGPT GPT-6 |
| Format Dokumen | Markdown (.md) |

---

## B. TUJUAN PEMBELAJARAN

Berdasarkan materi perkuliahan, tujuan pembelajaran pada pertemuan pertama adalah:

1. Mampu menjelaskan konsep sistem terdistribusi.
2. Mampu menjelaskan konsep sistem terdesentralisasi.
3. Mampu menjelaskan perbedaan sistem terdistribusi dengan sistem terdesentralisasi.
4. Mampu menyebutkan berbagai contoh penerapan nyata dari sistem terdistribusi dan terdesentralisasi.
5. Mampu menyebutkan berbagai tantangan dan tren terbaru di dunia sistem terdistribusi dan terdesentralisasi.

---

## C. RANGKUMAN MATERI

### 1. Arti Penting Sistem Terdistribusi dan Terdesentralisasi

Perkembangan teknologi informasi menyebabkan jumlah data, pengguna, dan kebutuhan layanan digital semakin meningkat. Aplikasi modern tidak lagi hanya digunakan oleh beberapa orang, tetapi dapat diakses oleh jutaan hingga miliaran pengguna dari berbagai lokasi secara bersamaan. Kondisi tersebut membuat sistem komputer konvensional yang hanya mengandalkan satu komputer atau satu server memiliki keterbatasan dalam menangani beban kerja yang besar.

Sistem terdistribusi dan terdesentralisasi menjadi salah satu pendekatan untuk mengatasi permasalahan tersebut. Dengan membagi pekerjaan ke beberapa komputer atau node yang saling terhubung, sistem dapat memberikan layanan yang lebih fleksibel, memiliki kapasitas lebih besar, dan tetap beroperasi ketika sebagian komponennya mengalami gangguan.

Beberapa alasan pentingnya penerapan kedua sistem tersebut antara lain:

**a. Pertumbuhan Data dan Pengguna**

Jumlah data yang dihasilkan oleh aktivitas digital terus meningkat. Platform seperti media sosial, layanan streaming, dan penyimpanan cloud harus mampu mengelola data dalam jumlah besar sekaligus melayani banyak pengguna.

**b. Skalabilitas (Scalability)**

Skalabilitas merupakan kemampuan suatu sistem, jaringan, proses, atau organisasi untuk berkembang dan menangani peningkatan beban kerja, jumlah pengguna, atau permintaan tanpa mengorbankan kinerja maupun kualitas layanan.

Sebagai contoh, ketika jumlah pengguna sebuah aplikasi meningkat, kapasitas sistem dapat ditambah dengan menambahkan sumber daya komputasi atau server agar permintaan pengguna tetap dapat diproses.

**c. Fault Tolerance**

Fault tolerance adalah kemampuan sistem untuk tetap beroperasi meskipun sebagian komponennya mengalami kegagalan atau malfungsi, baik pada perangkat keras maupun perangkat lunak.

Sebagai contoh, apabila salah satu server mengalami kerusakan, server lain dapat mengambil alih sebagian tugas sehingga layanan tidak sepenuhnya berhenti.

**d. Performa dan Ketersediaan Layanan 24/7**

Layanan digital modern dituntut untuk dapat diakses kapan saja. Sistem terdistribusi memungkinkan pekerjaan dibagi ke beberapa komputer sehingga beban tidak hanya ditanggung oleh satu perangkat.

**[MODIFIKASI]**

Penerapan sistem terdistribusi juga membantu mengurangi ketergantungan terhadap satu server pusat. Misalnya, ketika sebuah platform streaming mengalami peningkatan jumlah penonton pada jam tertentu, permintaan dapat ditangani oleh beberapa server. Dengan pembagian beban tersebut, risiko server mengalami kelebihan beban dapat dikurangi.

Tanpa pendekatan distribusi dan desentralisasi, layanan berskala besar seperti Google, Netflix, dan teknologi Blockchain akan sangat sulit diwujudkan dan dikelola sesuai kebutuhan modern.

### 2. Pengertian Sistem Terdistribusi

Sistem terdistribusi atau *Distributed System* merupakan sekumpulan komputer independen yang saling terhubung dan bekerja sama melalui jaringan, tetapi bagi penggunanya terlihat sebagai satu kesatuan sistem yang utuh.

Menurut Andrew S. Tanenbaum dan Maarten van Steen (2007), sistem terdistribusi adalah:

> "A collection of independent computers that appears to its users as a single coherent system."

Artinya, meskipun sistem terdiri dari beberapa komputer yang bekerja secara terpisah, pengguna tidak harus mengetahui bagaimana pembagian pekerjaan maupun lokasi setiap komputer tersebut.

Beberapa konsep utama dalam sistem terdistribusi adalah:

**a. Komponen Independen**

Setiap komputer atau node memiliki sumber daya dan kemampuan pemrosesan sendiri. Node tersebut dapat menjalankan tugas tertentu secara mandiri, tetapi tetap berkoordinasi dengan node lainnya untuk mencapai tujuan sistem.

**b. Komunikasi Melalui Jaringan**

Setiap komponen saling bertukar informasi melalui jaringan komputer. Komunikasi dapat dilakukan untuk mengirimkan permintaan, memberikan respons, berbagi data, maupun mengoordinasikan pekerjaan.

**c. Transparansi (Transparency)**

Transparansi merupakan kemampuan sistem untuk menyembunyikan kompleksitas distribusi dari pengguna. Pengguna cukup menggunakan layanan tanpa harus mengetahui secara detail lokasi dan cara kerja komponen di belakangnya.

Beberapa bentuk transparansi yang disebutkan dalam materi meliputi:

1. **Location Transparency:** Pengguna tidak perlu mengetahui lokasi fisik suatu sumber daya atau server yang digunakan.
2. **Access Transparency:** Pengguna dapat mengakses sumber daya tanpa harus mengetahui perbedaan mekanisme akses yang digunakan.
3. **Replication Transparency:** Pengguna tidak perlu mengetahui bahwa suatu data atau layanan memiliki beberapa salinan pada node yang berbeda.
4. **Failure Transparency:** Sistem berusaha menyembunyikan kegagalan komponen tertentu agar tidak langsung mengganggu pengalaman pengguna.

**[MODIFIKASI]**

Contoh sederhana sistem terdistribusi adalah layanan Google Drive. Ketika pengguna mengunggah dokumen, pengguna cukup membuka aplikasi dan mengakses file tersebut. Proses penyimpanan, pengelolaan data, komunikasi jaringan, dan penyediaan layanan dapat melibatkan berbagai komponen komputasi di belakang layar.

Dengan demikian, konsep utama sistem terdistribusi bukan hanya menghubungkan beberapa komputer, tetapi juga mengatur komunikasi, koordinasi, dan pembagian pekerjaan agar seluruh komponen dapat memberikan layanan sebagai satu kesatuan.

### 3. Arsitektur Sistem Dasar

Arsitektur sistem menjelaskan bagaimana komponen-komponen komputer disusun dan berinteraksi dalam suatu sistem terdistribusi.

Dalam materi pertemuan pertama terdapat tiga bentuk arsitektur dasar, yaitu Client-Server, Peer-to-Peer, dan Hybrid.

#### 3.1 Client-Server

Arsitektur Client-Server merupakan model komunikasi yang membagi komponen sistem menjadi dua peran utama, yaitu client dan server.

- **Client:** Perangkat atau aplikasi yang mengirimkan permintaan layanan.
- **Server:** Komputer atau sistem yang menerima permintaan, memprosesnya, dan mengirimkan hasil kepada client.

Contoh penerapan:
- Browser yang meminta halaman website dari web server.
- Aplikasi mobile yang mengambil data dari server.
- Aplikasi perbankan yang meminta informasi saldo dari server bank.

**[MODIFIKASI]**

Sebagai contoh, ketika seseorang membuka sebuah website melalui browser, browser bertindak sebagai client yang mengirimkan permintaan kepada server. Server kemudian memproses permintaan tersebut dan mengirimkan halaman website untuk ditampilkan kepada pengguna.

Kelebihan arsitektur ini adalah pengelolaan data dan layanan dapat dilakukan secara terpusat sehingga pengaturan dan pemeliharaan relatif lebih mudah.

Namun, apabila server utama mengalami gangguan dan tidak tersedia mekanisme cadangan, layanan yang bergantung pada server tersebut dapat ikut terganggu. Kondisi ini dikenal sebagai *Single Point of Failure*.

#### 3.2 Peer-to-Peer (P2P)

Peer-to-Peer merupakan arsitektur jaringan yang memungkinkan setiap komputer atau node berkomunikasi secara langsung dan berbagi sumber daya dengan node lainnya.

Dalam model ini, setiap peer dapat berperan sebagai penyedia sekaligus penerima layanan. Dengan demikian, tidak semua aktivitas harus bergantung pada satu server pusat.

Contoh penerapan:
- BitTorrent untuk berbagi file.
- Pertukaran data secara langsung antarperangkat.
- Jaringan peer-to-peer dalam berbagai aplikasi terdistribusi.

**[MODIFIKASI]**

Sebagai contoh, dalam jaringan BitTorrent, sebuah file dapat dibagi menjadi beberapa bagian dan didistribusikan kepada banyak peer. Pengguna yang mengunduh file tidak hanya menerima data dari satu server, tetapi juga dapat memperoleh bagian file dari peer lain yang sudah memilikinya.

Model ini memungkinkan sumber daya jaringan dibagikan oleh para anggota jaringan sehingga beban distribusi tidak hanya ditanggung oleh satu penyedia layanan.

#### 3.3 Hybrid

Arsitektur Hybrid merupakan kombinasi dari beberapa pendekatan arsitektur, khususnya Client-Server dan Peer-to-Peer.

Dalam model ini, beberapa fungsi dapat dikelola oleh server pusat, sementara proses pertukaran data tertentu dapat dilakukan secara langsung antarpeer.

**[MODIFIKASI]**

Sebagai contoh, sebuah aplikasi dapat menggunakan server pusat untuk mengelola informasi pengguna, autentikasi, atau pencarian perangkat. Setelah perangkat saling ditemukan, pertukaran data tertentu dapat berlangsung secara langsung melalui koneksi peer-to-peer.

Pendekatan Hybrid menggabungkan kemudahan pengelolaan dari Client-Server dengan kemampuan berbagi sumber daya dari Peer-to-Peer.

### 4. Karakteristik Sistem Terdistribusi

Sistem terdistribusi memiliki beberapa karakteristik penting yang membedakannya dari sistem komputer yang hanya menggunakan satu perangkat.

#### 4.1 Transparansi Lokasi

Pengguna tidak perlu mengetahui lokasi fisik suatu data atau layanan. Sistem mengatur proses pencarian dan akses terhadap sumber daya tersebut.

#### 4.2 Skalabilitas

Sistem mampu berkembang untuk menangani peningkatan jumlah pengguna, data, maupun permintaan layanan.

Skalabilitas dapat dicapai dengan menambahkan sumber daya atau memperluas kapasitas sistem sesuai kebutuhan.

#### 4.3 Fault Tolerance

Sistem tetap berusaha beroperasi ketika sebagian komponennya mengalami kegagalan. Hal ini dapat didukung melalui replikasi data, redundansi, dan mekanisme pemulihan.

#### 4.4 Kinerja Tinggi

Pembagian beban kerja ke beberapa komputer memungkinkan proses dilakukan secara bersamaan sehingga kapasitas pemrosesan dapat meningkat.

Namun, peningkatan jumlah node tidak selalu menjamin kinerja yang lebih baik karena komunikasi jaringan dan koordinasi antarkomponen juga membutuhkan sumber daya.

#### 4.5 Heterogenitas

Sistem terdistribusi dapat terdiri dari berbagai perangkat keras, sistem operasi, bahasa pemrograman, jaringan, dan teknologi yang berbeda.

**[MODIFIKASI]**

Sebagai contoh, suatu aplikasi dapat memiliki server berbasis Linux, aplikasi pengguna berbasis Android, serta layanan lain yang berjalan pada lingkungan Windows. Seluruh komponen tetap dapat bekerja sama selama memiliki mekanisme komunikasi dan standar pertukaran data yang sesuai.

Karakteristik heterogenitas membuat sistem lebih fleksibel dalam menggabungkan berbagai teknologi, tetapi juga meningkatkan kompleksitas integrasi dan pemeliharaan.

### 5. Pengertian Sistem Terdesentralisasi

Sistem terdesentralisasi atau *Decentralized System* merupakan sistem yang membagi kendali, pengambilan keputusan, atau pengelolaan sumber daya kepada beberapa pihak atau node, sehingga tidak seluruh kewenangan berada pada satu titik pusat.

Materi perkuliahan menjelaskan perbedaan antara sentralisasi dan desentralisasi sebagai berikut:

**a. Sentralisasi (Centralization)**

Sentralisasi merupakan model pengelolaan yang menempatkan kendali atau pengambilan keputusan pada satu titik pusat.

Dalam sistem ini, satu pihak atau server utama memiliki kewenangan untuk mengatur aktivitas sistem.

**b. Desentralisasi (Decentralization)**

Desentralisasi merupakan model yang membagi kendali kepada beberapa pihak atau node. Pengambilan keputusan tidak sepenuhnya bergantung pada satu titik pusat.

Dengan pembagian kendali tersebut, sistem dapat mengurangi ketergantungan terhadap satu pihak dan mengurangi risiko *Single Point of Failure*.

**c. Konsensus (Consensus)**

Konsensus merupakan mekanisme untuk mencapai kesepakatan di antara sejumlah node atau peserta jaringan mengenai suatu keputusan atau keadaan bersama.

Mekanisme ini penting dalam sistem terdesentralisasi karena tidak terdapat satu pengendali tunggal yang selalu menentukan keputusan untuk seluruh jaringan.

Contoh sistem terdesentralisasi dalam materi perkuliahan:
- Blockchain.
- Domain Name System (DNS).
- BitTorrent.

**[MODIFIKASI]**

Salah satu contoh penerapan desentralisasi adalah Blockchain. Dalam jaringan Blockchain publik, transaksi dapat diverifikasi oleh sejumlah peserta jaringan berdasarkan aturan protokol yang telah ditentukan.

Artinya, validitas transaksi tidak hanya ditentukan oleh satu perusahaan atau server pusat, tetapi melalui mekanisme validasi dan konsensus yang dijalankan oleh peserta jaringan.

Desentralisasi tidak berarti bahwa sistem sama sekali tidak memiliki aturan atau pengelolaan. Sistem tetap membutuhkan protokol, mekanisme koordinasi, dan tata kelola agar setiap peserta dapat bekerja berdasarkan aturan yang sama.

### 6. Perbedaan Sistem Terdistribusi dan Sistem Terdesentralisasi

Sistem terdistribusi dan sistem terdesentralisasi memiliki hubungan yang erat, tetapi keduanya mempunyai fokus yang berbeda.

Berdasarkan materi perkuliahan, perbedaan utamanya adalah:

- Sistem terdistribusi berfokus pada pembagian beban kerja.
- Sistem terdesentralisasi berfokus pada pembagian kontrol atau kendali.

Berikut perbandingan kedua sistem:

| Aspek | Sistem Terdistribusi | Sistem Terdesentralisasi |
|---|---|---|
| Fokus utama | Pembagian beban kerja | Pembagian kendali |
| Tujuan | Meningkatkan kapasitas dan kinerja sistem | Mengurangi ketergantungan terhadap pusat kendali |
| Pengelolaan | Dapat menggunakan kontrol terpusat | Kendali dibagikan kepada beberapa pihak |
| Komunikasi | Antar-komputer atau node | Antar-node atau peserta jaringan |
| Risiko utama | Kegagalan jaringan, server, dan sinkronisasi | Konsensus, keamanan, dan tata kelola |
| Contoh | Google File System, HDFS, MinIO | Blockchain |

**[MODIFIKASI] Analisis Perbedaan**

Perbedaan paling penting terletak pada tujuan pembagian yang dilakukan.

Pada sistem terdistribusi, beberapa komputer digunakan untuk membagi proses atau pekerjaan agar sistem mampu menangani beban yang besar. Walaupun komponen tersebar di berbagai lokasi, pengelolaan sistem masih dapat dikendalikan oleh satu organisasi atau pusat pengelolaan.

Sementara itu, sistem terdesentralisasi lebih menekankan pembagian kewenangan. Setiap peserta atau node memiliki peran dalam proses pengambilan keputusan sesuai dengan aturan yang berlaku.

Hal yang perlu dipahami adalah sistem terdistribusi belum tentu terdesentralisasi. Sebuah layanan dapat menggunakan banyak server yang tersebar di berbagai lokasi, tetapi seluruh server tetap dikendalikan oleh satu perusahaan.

Sebaliknya, desentralisasi berkaitan dengan distribusi kewenangan dan kontrol, bukan sekadar jumlah komputer yang digunakan.

Dengan demikian, keduanya dapat diterapkan secara bersamaan, tetapi tidak memiliki arti yang sama.

### 7. Studi Kasus Sistem Terdistribusi

Materi perkuliahan memberikan beberapa contoh penerapan sistem terdistribusi dalam teknologi informasi.

#### 7.1 Google File System dan HDFS

Google File System (GFS) dan Hadoop Distributed File System (HDFS) merupakan contoh teknologi penyimpanan terdistribusi yang digunakan untuk menangani data berukuran besar.

Keduanya memungkinkan data disimpan dan dikelola menggunakan beberapa komputer dalam sebuah lingkungan terdistribusi.

**[MODIFIKASI]**

Dalam penyimpanan terdistribusi, data dapat dibagi menjadi beberapa bagian dan disimpan pada node yang berbeda. Mekanisme tersebut membantu sistem menangani data berukuran besar yang sulit dikelola hanya menggunakan satu komputer.

HDFS, misalnya, menggunakan pendekatan pembagian file menjadi blok-blok data yang dikelola dalam sebuah cluster. Mekanisme replikasi juga dapat digunakan untuk membantu menjaga ketersediaan data ketika terjadi kegagalan node.

#### 7.2 Apache Kafka dan Apache Pulsar

Apache Kafka dan Apache Pulsar merupakan teknologi yang digunakan untuk messaging dan data streaming.

Keduanya memungkinkan data atau pesan dikirim, diterima, dan diproses oleh berbagai komponen aplikasi.

**[MODIFIKASI]**

Sebagai contoh, pada sebuah aplikasi e-commerce, aktivitas pengguna seperti pembuatan pesanan dapat menghasilkan pesan yang dikirim ke sistem messaging. Komponen lain kemudian dapat memproses pesan tersebut untuk kebutuhan pembayaran, pencatatan pesanan, dan pembaruan informasi.

Dengan pendekatan ini, setiap komponen aplikasi tidak harus selalu berkomunikasi secara langsung satu sama lain.

#### 7.3 Netflix dan Twitch

Netflix dan Twitch merupakan contoh platform digital yang membutuhkan infrastruktur terdistribusi untuk melayani pengguna dalam jumlah besar.

Netflix menyediakan layanan streaming video, sedangkan Twitch menyediakan layanan streaming dan interaksi secara langsung.

Keduanya membutuhkan kemampuan pengelolaan data, jaringan, dan pemrosesan permintaan pengguna dalam skala besar.

#### 7.4 YouTube

YouTube merupakan platform berbagi video yang harus mengelola berbagai proses, seperti penyimpanan video, pemrosesan konten, dan distribusi video kepada pengguna.

**[MODIFIKASI]**

Sistem distribusi memungkinkan layanan video menangani permintaan dari banyak pengguna secara bersamaan. Pengguna yang berada di lokasi berbeda dapat mengakses konten tanpa harus seluruhnya dilayani oleh satu komputer yang sama.

#### 7.5 Instagram, Threads, Facebook, dan TikTok

Platform media sosial membutuhkan sistem yang mampu menangani data pengguna, unggahan konten, komentar, interaksi, dan distribusi informasi dalam jumlah besar.

Penggunaan sistem terdistribusi mendukung pengelolaan aktivitas tersebut dengan membagi beban kerja ke berbagai komponen infrastruktur.

### 8. Studi Kasus Sistem Terdesentralisasi

Materi perkuliahan menjelaskan tiga contoh sistem terdesentralisasi, yaitu Blockchain, DNS, dan BitTorrent.

#### 8.1 Blockchain

Blockchain merupakan teknologi pencatatan data digital yang menggunakan struktur blok dan mekanisme kriptografi untuk menghubungkan catatan transaksi.

Pada jaringan Blockchain publik, data transaksi dapat divalidasi oleh sejumlah node berdasarkan aturan protokol yang digunakan.

Contoh Blockchain yang disebutkan dalam materi:
- Bitcoin.
- Ethereum.
- Algorand.
- Sui.
- Near.
- Aptos.

**[MODIFIKASI]**

Salah satu keunggulan pendekatan Blockchain adalah pencatatan transaksi tidak harus bergantung pada satu server milik suatu perusahaan. Peserta jaringan dapat melakukan verifikasi sesuai mekanisme konsensus yang digunakan.

Namun, Blockchain juga memiliki tantangan seperti skalabilitas, biaya transaksi, keamanan, dan kecepatan pemrosesan.

#### 8.2 Domain Name System (DNS)

Domain Name System (DNS) merupakan sistem yang digunakan untuk menerjemahkan nama domain menjadi alamat IP yang dapat digunakan komputer untuk berkomunikasi melalui jaringan.

Contohnya, ketika pengguna mengakses sebuah website menggunakan nama domain, DNS membantu menemukan alamat IP yang sesuai.

**[MODIFIKASI]**

DNS memiliki struktur pengelolaan yang bersifat hierarkis dan tersebar. Informasi domain dikelola melalui berbagai server DNS yang memiliki tanggung jawab berbeda.

Oleh karena itu, DNS dapat menjadi contoh sistem dengan infrastruktur dan pengelolaan yang terdistribusi. Namun, perlu dipahami bahwa DNS tidak sepenuhnya terdesentralisasi dalam arti tidak memiliki hierarki atau otoritas pusat. Pengelolaan domain tetap melibatkan organisasi dan otoritas tertentu.

#### 8.3 BitTorrent

BitTorrent merupakan protokol berbagi file yang menggunakan pendekatan Peer-to-Peer.

Pengguna dapat mengunduh bagian file dari beberapa peer sekaligus, sementara pengguna yang sudah memiliki bagian file juga dapat membagikannya kepada peer lainnya.

**[MODIFIKASI]**

Berbeda dengan model pengunduhan konvensional yang sepenuhnya bergantung pada satu server, BitTorrent memungkinkan distribusi data dilakukan oleh banyak peserta jaringan.

Semakin banyak peer yang menyediakan bagian file, semakin banyak sumber yang dapat dimanfaatkan untuk proses pengunduhan. Namun, ketersediaan file tetap dipengaruhi oleh jumlah peer yang aktif dan memiliki data yang dibutuhkan.

### 9. CAP Theorem (Brewer's Theorem)

CAP Theorem merupakan konsep penting dalam perancangan sistem terdistribusi, khususnya pada sistem penyimpanan data yang menggunakan beberapa node.

Konsep ini diperkenalkan oleh Eric Brewer pada tahun 2000 dan dikenal sebagai Brewer's Theorem.

CAP merupakan singkatan dari tiga karakteristik berikut:

#### 9.1 Consistency

Consistency atau konsistensi merupakan kondisi ketika setiap operasi pembacaan mengembalikan hasil penulisan terbaru atau menghasilkan error.

Dalam konteks CAP, konsistensi berkaitan dengan keseragaman data yang terlihat oleh pengguna ketika melakukan operasi baca dan tulis.

#### 9.2 Availability

Availability atau ketersediaan merupakan kemampuan sistem untuk memberikan respons terhadap setiap permintaan yang diterima oleh node yang tidak mengalami kegagalan.

Respons tersebut harus berupa hasil yang tidak error, meskipun data yang diberikan belum tentu merupakan data paling terbaru.

#### 9.3 Partition Tolerance

Partition Tolerance merupakan kemampuan sistem untuk tetap beroperasi ketika terjadi gangguan komunikasi atau pemisahan jaringan antar-node.

Sebagai contoh, beberapa server yang berada di lokasi berbeda dapat kehilangan koneksi satu sama lain akibat gangguan jaringan.

#### 9.4 Prinsip CAP Theorem

CAP Theorem menjelaskan bahwa pada saat terjadi network partition, sistem penyimpanan data terdistribusi harus menentukan prioritas antara Consistency dan Availability.

Ketiga konsep tersebut tidak dapat dijamin secara bersamaan dalam kondisi partisi jaringan.

**[MODIFIKASI] Penjelasan Sederhana CAP Theorem**

Untuk memahami CAP Theorem, bayangkan sebuah aplikasi yang memiliki dua server, yaitu Server A dan Server B. Keduanya menyimpan data saldo rekening pengguna.

Dalam kondisi normal, kedua server dapat saling berkomunikasi dan memperbarui data.

Namun, ketika terjadi gangguan jaringan, komunikasi antara Server A dan Server B terputus.

Pada kondisi tersebut muncul dua pilihan:

1. Sistem tetap melayani permintaan pengguna meskipun data pada kedua server mungkin belum sama.
2. Sistem membatasi atau menolak sebagian permintaan agar tidak menghasilkan data yang berbeda.

Situasi tersebut menggambarkan trade-off antara Availability dan Consistency ketika Partition Tolerance harus dipertahankan.

#### 9.5 AP (Availability + Partition Tolerance)

AP merupakan pendekatan yang mengutamakan ketersediaan layanan dan kemampuan menghadapi gangguan jaringan.

Ketika terjadi partition, sistem tetap berusaha melayani permintaan pengguna, meskipun terdapat kemungkinan data antar-node belum sinkron.

Konsekuensinya adalah konsistensi data dapat dikorbankan sementara.

Contoh yang dicantumkan dalam materi perkuliahan adalah MongoDB.

#### 9.6 CP (Consistency + Partition Tolerance)

CP merupakan pendekatan yang mengutamakan konsistensi data dan kemampuan menghadapi gangguan jaringan.

Ketika terjadi partition, sistem dapat menolak atau membatasi permintaan baca maupun tulis pada bagian tertentu agar data tetap konsisten.

Konsekuensinya adalah sebagian layanan mungkin tidak tersedia selama gangguan berlangsung.

Contoh yang dicantumkan dalam materi perkuliahan adalah Apache Cassandra.

**[MODIFIKASI] Analisis AP dan CP**

Perbedaan AP dan CP dapat dipahami melalui contoh aplikasi transaksi.

Pada sistem yang lebih mengutamakan Availability, pengguna tetap dapat melakukan permintaan meskipun terdapat kemungkinan informasi yang diterima belum diperbarui pada seluruh node.

Sementara itu, sistem yang lebih mengutamakan Consistency dapat memilih untuk menolak permintaan tertentu ketika tidak dapat memastikan kebenaran data terbaru.

Pemilihan pendekatan harus disesuaikan dengan kebutuhan aplikasi.

Misalnya:
- Aplikasi media sosial dapat lebih toleran terhadap keterlambatan sinkronisasi beberapa informasi.
- Sistem transaksi keuangan membutuhkan perhatian lebih besar terhadap konsistensi data agar tidak terjadi kesalahan pencatatan.

Catatan: Contoh MongoDB dan Apache Cassandra pada slide merupakan penyederhanaan untuk menggambarkan pendekatan AP dan CP. Perilaku aktual kedua teknologi bergantung pada konfigurasi, model konsistensi, dan mekanisme operasi yang digunakan. Keduanya tidak tepat dianggap selalu AP atau selalu CP dalam setiap kondisi.

### 10. Konsistensi Data (Data Consistency)

Konsistensi data merupakan kondisi yang menggambarkan kesesuaian informasi ketika data disimpan, diperbarui, dan dibaca oleh pengguna atau komponen sistem.

Dalam sistem terdistribusi, data dapat memiliki beberapa salinan pada node yang berbeda. Oleh karena itu, sistem membutuhkan mekanisme untuk menjaga agar perubahan data dapat dikelola dengan benar.

Materi perkuliahan membahas dua jenis konsistensi data:

#### 10.1 Strong Consistency

Strong Consistency merupakan model konsistensi yang memastikan operasi pembacaan memperoleh hasil sesuai dengan penulisan terbaru yang telah berhasil dilakukan berdasarkan jaminan konsistensi sistem.

Dengan model ini, pengguna memperoleh informasi yang konsisten meskipun data dikelola oleh beberapa node.

Contoh penerapan dalam materi adalah sistem perbankan.

**[MODIFIKASI]**

Dalam sistem perbankan, informasi saldo dan transaksi harus dikelola secara akurat. Apabila saldo rekening diperbarui setelah transaksi, sistem harus memiliki mekanisme untuk memastikan pembacaan saldo tidak menghasilkan informasi yang bertentangan dengan transaksi yang telah berhasil dicatat.

#### 10.2 Eventual Consistency

Eventual Consistency merupakan model konsistensi yang memungkinkan perbedaan data sementara antar-node. Namun, apabila tidak ada perubahan baru dan proses sinkronisasi berjalan dengan baik, data pada node-node tersebut pada akhirnya akan menjadi konsisten.

Contoh penerapan dalam materi adalah media sosial.

**[MODIFIKASI]**

Sebagai contoh, ketika seseorang mengunggah foto di media sosial, perubahan informasi mungkin tidak langsung terlihat secara bersamaan oleh seluruh pengguna karena data perlu didistribusikan dan disinkronkan ke berbagai komponen sistem.

Meskipun terdapat keterlambatan, data diharapkan menjadi konsisten setelah proses sinkronisasi selesai.

#### 10.3 Perbandingan Strong Consistency dan Eventual Consistency

| Aspek | Strong Consistency | Eventual Consistency |
|---|---|---|
| Kondisi data | Mengutamakan hasil terbaru yang konsisten | Dapat berbeda sementara |
| Sinkronisasi | Membutuhkan jaminan konsistensi yang lebih ketat | Dapat berlangsung secara bertahap |
| Respons | Dapat memerlukan koordinasi tambahan | Dapat lebih fleksibel terhadap keterlambatan sinkronisasi |
| Contoh dalam materi | Sistem perbankan | Media sosial |
| Kebutuhan utama | Ketepatan informasi | Ketersediaan dan fleksibilitas distribusi data |

### 11. Tantangan Sistem Terdistribusi dan Terdesentralisasi

Meskipun memberikan banyak manfaat, penerapan sistem terdistribusi dan terdesentralisasi juga memiliki beberapa tantangan.

#### 11.1 Latency dan Throughput

Latency merupakan waktu yang dibutuhkan untuk memproses suatu permintaan atau memperoleh respons dari sistem.

Semakin tinggi latency, semakin lama pengguna harus menunggu hasil dari suatu proses.

Throughput merupakan jumlah pekerjaan atau permintaan yang dapat diproses sistem dalam suatu periode waktu.

**[MODIFIKASI]**

Contohnya, sebuah aplikasi dapat menerima ribuan permintaan dalam satu detik. Apabila server membutuhkan waktu terlalu lama untuk memproses permintaan tersebut, pengguna dapat mengalami keterlambatan respons.

Oleh karena itu, perancangan sistem perlu memperhatikan keseimbangan antara latency dan throughput.

#### 11.2 Keamanan Sistem

Sistem terdistribusi dan terdesentralisasi menghadapi berbagai ancaman keamanan karena melibatkan banyak perangkat, node, komunikasi jaringan, dan pengguna.

Materi perkuliahan menyebutkan dua contoh serangan:

- Distributed Denial of Service (DDoS).
- Sybil Attack.

**DDoS (Distributed Denial of Service)** merupakan serangan yang dilakukan dengan membanjiri suatu layanan menggunakan permintaan dalam jumlah besar sehingga layanan mengalami gangguan atau tidak dapat melayani pengguna yang sah.

**Sybil Attack** merupakan serangan yang dilakukan dengan membuat banyak identitas palsu, seperti akun, node, atau pseudonim, untuk memengaruhi jaringan.

Penyerang dapat menggunakan banyak identitas tersebut untuk mendominasi pengaruh, suara, atau reputasi dalam sistem.

Serangan ini dapat ditemukan sebagai ancaman pada sistem peer-to-peer dan Blockchain.

**[MODIFIKASI]**

Sebagai contoh, apabila suatu jaringan terdesentralisasi menggunakan mekanisme pemungutan suara, penyerang dapat mencoba membuat banyak identitas palsu untuk meningkatkan pengaruhnya dalam proses pengambilan keputusan.

Apabila sistem tidak memiliki mekanisme perlindungan identitas atau pembatasan pengaruh yang memadai, serangan tersebut dapat mengganggu integritas jaringan.

#### 11.3 Kompleksitas Manajemen Node

Sistem terdistribusi dapat terdiri dari banyak node yang harus saling berkomunikasi dan bekerja sama.

Semakin banyak node yang digunakan, semakin kompleks proses pemantauan, konfigurasi, pemeliharaan, sinkronisasi, dan penanganan kegagalan.

**[MODIFIKASI]**

Administrator sistem harus memastikan setiap node berjalan sesuai fungsinya, dapat berkomunikasi dengan node lain, serta memiliki konfigurasi yang sesuai. Gangguan pada satu node juga perlu dianalisis agar tidak memengaruhi keseluruhan layanan.

#### 11.4 Governance (Tata Kelola)

Governance merupakan mekanisme pengaturan dan pengambilan keputusan dalam suatu sistem.

Dalam sistem terdesentralisasi, tata kelola menjadi tantangan karena keputusan tidak selalu berada di tangan satu pihak.

Diperlukan aturan yang jelas mengenai bagaimana perubahan sistem dilakukan, bagaimana keputusan disepakati, dan bagaimana konflik antarpartisipan diselesaikan.

**[MODIFIKASI]**

Contohnya, dalam sebuah jaringan Blockchain, perubahan terhadap protokol dapat memerlukan persetujuan atau dukungan dari peserta jaringan sesuai mekanisme yang berlaku. Apabila terdapat perbedaan pendapat, proses pengambilan keputusan dapat menjadi lebih kompleks.

### 12. Tren Masa Depan Sistem Terdistribusi dan Terdesentralisasi

Perkembangan teknologi membuat sistem terdistribusi dan terdesentralisasi terus mengalami perubahan. Materi perkuliahan membahas beberapa tren yang berpotensi semakin berkembang.

#### 12.1 Cloud-Native

Cloud-Native merupakan pendekatan pengembangan dan pengoperasian aplikasi yang dirancang untuk memanfaatkan lingkungan cloud.

Teknologi yang disebutkan dalam materi antara lain:

- Docker.
- Kubernetes.

Docker digunakan untuk mengemas aplikasi beserta kebutuhan lingkungannya ke dalam container, sedangkan Kubernetes digunakan untuk mengelola dan mengorkestrasi container dalam suatu cluster.

**[MODIFIKASI]**

Pendekatan Cloud-Native membantu aplikasi berjalan lebih fleksibel karena komponen aplikasi dapat dikembangkan, dijalankan, dan dikelola dalam lingkungan yang terpisah sesuai kebutuhan.

#### 12.2 Edge Computing dan Fog Computing

Edge Computing merupakan pendekatan pemrosesan data yang dilakukan lebih dekat dengan sumber data atau perangkat pengguna.

Fog Computing merupakan pendekatan yang menyediakan lapisan komputasi dan pengelolaan sumber daya di antara perangkat edge dan infrastruktur cloud.

**[MODIFIKASI]**

Contohnya adalah sistem kamera pengawas pintar. Apabila seluruh data video harus dikirim ke cloud untuk dianalisis, proses tersebut dapat membutuhkan bandwidth besar dan menambah latency.

Dengan Edge Computing, sebagian pemrosesan dapat dilakukan langsung di perangkat atau komputer yang berada dekat dengan kamera. Hal ini memungkinkan sistem memberikan respons lebih cepat.

#### 12.3 Web3 dan DeFi

Web3 merupakan konsep pengembangan layanan internet yang memberikan perhatian terhadap kepemilikan aset digital, identitas, dan interaksi melalui teknologi terdesentralisasi.

DeFi atau Decentralized Finance merupakan layanan keuangan yang memanfaatkan teknologi Blockchain dan smart contract untuk menjalankan berbagai aktivitas keuangan tanpa sepenuhnya bergantung pada lembaga keuangan tradisional sebagai perantara.

**[MODIFIKASI]**

Contoh penerapannya adalah layanan pertukaran aset digital yang menggunakan smart contract untuk menjalankan aturan transaksi secara otomatis berdasarkan kode program.

Walaupun menawarkan pendekatan baru, Web3 dan DeFi tetap memiliki tantangan seperti keamanan smart contract, risiko ekonomi, skalabilitas, dan tata kelola.

#### 12.4 Federated Data dan Federated Learning

Federated Learning merupakan pendekatan pembelajaran mesin yang memungkinkan proses pelatihan model dilakukan pada beberapa perangkat atau lokasi tanpa harus selalu mengumpulkan seluruh data mentah ke satu server pusat.

Hasil pembelajaran dari masing-masing peserta dapat dikombinasikan untuk memperbarui model bersama.

**[MODIFIKASI]**

Sebagai contoh, beberapa perangkat dapat melakukan pelatihan model menggunakan data lokal masing-masing. Kemudian, hasil pembelajaran dikirim untuk digabungkan menjadi pembaruan model global.

Pendekatan ini berpotensi membantu menjaga privasi karena data mentah tidak harus selalu dipindahkan ke satu tempat.

Namun, Federated Learning tetap memiliki tantangan seperti keamanan proses pelatihan, kualitas data yang berbeda-beda, dan kebutuhan komunikasi antarperangkat.

---

## D. CONTOH PENERAPAN DAN ANALISIS

### 1. Contoh Penerapan dalam Kehidupan Nyata

Berdasarkan materi perkuliahan dan pengembangan pembahasan, berikut beberapa contoh penerapan sistem terdistribusi dan terdesentralisasi dalam teknologi informasi.

#### a. Google Drive

Google Drive merupakan contoh layanan penyimpanan cloud yang memanfaatkan infrastruktur terdistribusi untuk mengelola dan menyediakan akses terhadap file pengguna.

Pengguna tidak harus mengetahui lokasi fisik penyimpanan file karena sistem menyediakan akses melalui satu layanan.

Konsep yang berkaitan:
- Sistem terdistribusi.
- Transparansi lokasi.
- Skalabilitas.
- Ketersediaan layanan.

#### b. Netflix

Netflix merupakan contoh layanan streaming yang harus menangani permintaan video dari banyak pengguna di berbagai lokasi.

Sistem terdistribusi membantu mengelola distribusi konten dan permintaan pengguna agar layanan tetap dapat digunakan dalam skala besar.

Konsep yang berkaitan:
- Pembagian beban kerja.
- Skalabilitas.
- Kinerja.
- Ketersediaan layanan.

#### c. Blockchain Bitcoin

Bitcoin merupakan contoh penerapan sistem Blockchain yang menggunakan jaringan peer-to-peer dan mekanisme konsensus.

Transaksi diverifikasi oleh peserta jaringan berdasarkan aturan protokol, bukan hanya berdasarkan keputusan satu server pusat.

Konsep yang berkaitan:
- Desentralisasi.
- Peer-to-peer.
- Konsensus.
- Keamanan jaringan.

#### d. BitTorrent

BitTorrent memungkinkan pengguna berbagi file melalui jaringan peer-to-peer.

Setiap peer dapat mengunduh sekaligus membagikan bagian file kepada peer lain.

Konsep yang berkaitan:
- Arsitektur Peer-to-Peer.
- Distribusi sumber daya.
- Komunikasi antar-node.

#### e. Aplikasi Media Sosial

Platform media sosial seperti Instagram, Facebook, dan TikTok memanfaatkan infrastruktur komputasi terdistribusi untuk mengelola unggahan, interaksi, dan distribusi konten.

Konsep yang berkaitan:
- Sistem terdistribusi.
- Skalabilitas.
- Eventual Consistency.
- Pengelolaan data dalam skala besar.

### 2. Analisis Keseluruhan Materi

**[MODIFIKASI]**

Berdasarkan materi pertemuan pertama, dapat dipahami bahwa sistem terdistribusi dan terdesentralisasi merupakan dua pendekatan penting dalam membangun infrastruktur teknologi modern.

Keduanya muncul karena kebutuhan sistem digital semakin kompleks, terutama dalam menangani jumlah pengguna yang besar, pertumbuhan data, kebutuhan layanan yang tersedia sepanjang waktu, serta keamanan dan keandalan sistem.

Sistem terdistribusi lebih menekankan bagaimana beberapa komputer dapat bekerja sama untuk menyelesaikan pekerjaan. Sementara itu, sistem terdesentralisasi lebih menekankan bagaimana kewenangan dan pengambilan keputusan dibagikan kepada beberapa pihak.

Kedua konsep tersebut juga memiliki tantangan yang berbeda. Sistem terdistribusi harus memperhatikan komunikasi jaringan, latency, konsistensi data, dan kegagalan node. Sistem terdesentralisasi perlu memperhatikan mekanisme konsensus, keamanan identitas, dan tata kelola jaringan.

CAP Theorem menjadi salah satu dasar penting dalam memahami bahwa perancangan sistem terdistribusi melibatkan kompromi, khususnya ketika terjadi gangguan komunikasi antar-node.

Dari sudut pandang mahasiswa Informatika, pemahaman terhadap materi ini menjadi dasar untuk mempelajari teknologi yang lebih lanjut, seperti cloud computing, Big Data, Blockchain, distributed database, dan infrastruktur aplikasi modern.

---

## E. PENGGUNAAN ARTIFICIAL INTELLIGENCE (AI)

### 1. AI yang Digunakan

- Nama AI: ChatGPT GPT-6.
- Pengembang: OpenAI.
- Tujuan penggunaan: Membantu membaca, memahami, merangkum, mengembangkan, dan mengevaluasi materi perkuliahan.
- Sumber utama: File PDF pertemuan pertama yang diberikan oleh dosen.
- Format hasil: Markdown (.md).

### 2. Prompt yang Digunakan

Berikut prompt yang digunakan dalam proses penyusunan rangkuman:

**Prompt 1 — Analisis dan Rangkuman Materi**

> Kamu adalah mahasiswa S1 Informatika yang sedang mempelajari mata kuliah Teori Sistem Terdistribusi dan Terdesentralisasi. Saya akan memberikan materi PDF dari dosen untuk pertemuan pertama.
>
> Baca dan analisis seluruh isi PDF secara menyeluruh. Identifikasi tujuan pembelajaran, agenda pembahasan, konsep utama, istilah teknis, contoh penerapan, dan kesimpulan dari materi.
>
> Buat rangkuman yang lengkap, sistematis, dan menggunakan bahasa Indonesia yang natural seperti mahasiswa Informatika.
>
> Ketentuan:
> 1. Gunakan materi PDF dosen sebagai sumber utama.
> 2. Jangan menghilangkan konsep penting dari materi.
> 3. Jangan mengarang informasi yang tidak didukung sumber.
> 4. Jelaskan setiap konsep dengan bahasa yang mudah dipahami.
> 5. Kembangkan penjelasan dari poin-poin slide menjadi paragraf yang informatif.
> 6. Sertakan contoh penerapan teknologi informasi jika relevan.
> 7. Jelaskan perbedaan sistem terdistribusi dan terdesentralisasi.
> 8. Berikan pembahasan mendalam tentang CAP Theorem, Strong Consistency, dan Eventual Consistency.
> 9. Susun hasil dalam format Markdown menggunakan heading dan subheading.
> Setelah rangkuman selesai, lakukan pemeriksaan ulang terhadap kesesuaiannya dengan materi PDF dosen. Jangan mengklaim seluruh hasil sebagai pekerjaan manual.

### 3. Bagian yang Disesuaikan dari Keluaran AI

Setelah proses analisis dan pengembangan terhadap rangkuman awal, beberapa bagian mendapatkan penyesuaian sebagai berikut:

1. **Pengertian Sistem Terdistribusi:** Penjelasan dikembangkan dengan menambahkan ilustrasi komunikasi antar-komputer, konsep transparansi, dan contoh penerapan pada layanan penyimpanan cloud.

2. **Arsitektur Sistem Dasar:** Pembahasan Client-Server, Peer-to-Peer, dan Hybrid dikembangkan dengan menambahkan mekanisme kerja, kelebihan, serta contoh penerapan masing-masing arsitektur.

3. **Karakteristik Sistem Terdistribusi:** Setiap karakteristik seperti skalabilitas, fault tolerance, transparansi, kinerja tinggi, dan heterogenitas dijelaskan lebih lanjut dengan contoh yang relevan.

4. **Sistem Terdistribusi dan Terdesentralisasi:** Ditambahkan tabel perbandingan berdasarkan fokus, tujuan, pengelolaan, dan contoh penerapan. Penjelasan juga dikembangkan untuk menunjukkan bahwa sistem terdistribusi tidak selalu bersifat terdesentralisasi.

5. **Studi Kasus:** Contoh GFS, HDFS, Kafka, Pulsar, Netflix, Twitch, YouTube, Blockchain, DNS, dan BitTorrent dikembangkan dengan penjelasan fungsi serta penerapan teknologinya.

6. **CAP Theorem:** Ditambahkan ilustrasi dua server yang mengalami gangguan komunikasi untuk mempermudah pemahaman hubungan Consistency, Availability, dan Partition Tolerance.

7. **Konsistensi Data:** Strong Consistency dan Eventual Consistency dikembangkan dengan penjelasan mekanisme serta perbandingan penerapannya pada sistem perbankan dan media sosial.

8. **Tantangan Sistem:** Pembahasan latency, throughput, keamanan, DDoS, Sybil Attack, kompleksitas manajemen node, dan governance dikembangkan menggunakan contoh situasi nyata.

9. **Tren Masa Depan:** Cloud-Native, Edge Computing, Fog Computing, Web3, DeFi, Federated Data, dan Federated Learning diberikan penjelasan tambahan mengenai fungsi dan penerapannya.

10. **Contoh Penerapan dan Analisis:** Ditambahkan pembahasan yang menghubungkan konsep perkuliahan dengan layanan teknologi yang digunakan dalam kehidupan sehari-hari.

### 4. Penanda Hasil Modifikasi

Penanda **[MODIFIKASI]** digunakan pada bagian yang memperoleh pengembangan substantif dari rangkuman awal AI.

Bagian tersebut meliputi penambahan penjelasan konsep, ilustrasi mekanisme kerja, contoh penerapan, perbandingan teknologi, serta analisis hubungan antar-konsep.

Bagian yang tidak diberi tanda tetap dipertahankan karena sudah sesuai dengan materi asli dosen atau tidak memerlukan pengembangan substantif.

---

## F. KESIMPULAN

Berdasarkan materi pertemuan pertama, sistem terdistribusi merupakan sistem yang terdiri dari beberapa komputer independen yang saling bekerja sama melalui jaringan dan terlihat sebagai satu kesatuan bagi pengguna. Sementara itu, sistem terdesentralisasi merupakan sistem yang membagi kendali dan pengambilan keputusan kepada beberapa pihak atau node.

Kedua konsep tersebut menjadi dasar berbagai teknologi modern seperti Cloud Computing, Blockchain, layanan streaming, dan penyimpanan data terdistribusi. Dalam penerapannya, terdapat tantangan yang perlu diperhatikan, seperti konsistensi data, latency, keamanan, kegagalan node, serta mekanisme pengambilan keputusan.

CAP Theorem juga memberikan pemahaman bahwa sistem terdistribusi perlu mempertimbangkan kompromi antara konsistensi dan ketersediaan ketika terjadi gangguan jaringan.

Dengan mempelajari materi ini, mahasiswa memperoleh dasar pemahaman mengenai cara kerja, arsitektur, karakteristik, manfaat, dan tantangan sistem terdistribusi maupun terdesentralisasi yang akan menjadi landasan untuk mempelajari teknologi tersebut pada pertemuan selanjutnya.

---

## G. DAFTAR REFERENSI

1. Bambang Purnomosidi D. P. (Tanpa tahun). *Pengenalan Sistem Terdistribusi dan Terdesentralisasi*. Materi Perkuliahan Teori Sistem Terdistribusi dan Terdesentralisasi, Program Studi Informatika, Universitas Teknologi Digital Indonesia.
2. Tanenbaum, A. S., & van Steen, M. (2007). *Distributed Systems: Principles and Paradigms*. Referensi definisi sistem terdistribusi sebagaimana dicantumkan dalam materi perkuliahan.
3. Baran, P. (1964). *On Distributed Communications*. Memorandum RM-3420-PR, sebagaimana dirujuk pada materi perkuliahan.

---

**DOKUMENTASI TUGAS**

- Repository: [disdec-teori](https://github.com/hendfirmsh/disdec-teori)
- Direktori: `01/`
- File: `README.md`
- Mata Kuliah: Teori Sistem Terdistribusi dan Terdesentralisasi
- Pertemuan: 1

---