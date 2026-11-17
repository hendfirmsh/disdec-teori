# RANGKUMAN MATERI TEORI SISTEM TERDISTRIBUSI DAN TERDESENTRALISASI

## PERTEMUAN 3

---

## A. IDENTITAS MATERI

| Keterangan | Informasi |
|---|---|
| Mata Kuliah | Teori Sistem Terdistribusi dan Terdesentralisasi |
| Pertemuan | Pertemuan ke-3 |
| Topik Materi | Sinkronisasi dan Koordinasi pada Sistem Terdistribusi |
| Sumber Materi | 03--sinkronisasi-sistem-terdistribusi.pdf |
| AI yang Digunakan | ChatGPT GPT-6 |
| Format Dokumen | Markdown (.md) |

---

## B. TUJUAN PEMBELAJARAN

Setelah mempelajari materi pada pertemuan ini, mahasiswa diharapkan mampu:

1. Memahami pentingnya sinkronisasi dan koordinasi dalam sistem terdistribusi, termasuk berbagai tantangan yang dapat memengaruhi konsistensi dan keandalan sistem.
2. Memahami sinkronisasi waktu fisik dan waktu logis, serta menjelaskan protokol dan algoritma yang digunakan, seperti NTP, PTP, dan Vector Clocks.
3. Memahami permasalahan mutual exclusion dan pemilihan koordinator, termasuk pendekatan algoritma yang digunakan untuk mengatur akses sumber daya dan koordinasi antarproses.

---

## C. RANGKUMAN MATERI

### 1. Pengertian dan Pentingnya Sinkronisasi

Sinkronisasi merupakan proses koordinasi terhadap proses, data, dan sumber daya yang terdapat pada berbagai node dalam sistem terdistribusi. Tujuannya adalah memastikan seluruh bagian sistem dapat bekerja secara konsisten dan dapat diandalkan meskipun proses dijalankan pada komputer atau perangkat yang berbeda.

Dalam sistem terdistribusi, beberapa proses dapat berjalan secara bersamaan dan mengakses data yang sama. Kondisi tersebut dapat menimbulkan konflik apabila tidak terdapat mekanisme pengaturan yang tepat. Oleh karena itu, sinkronisasi dibutuhkan untuk mengendalikan proses yang berjalan secara konkuren, menjaga konsistensi data, dan memastikan setiap node memiliki kondisi sistem (*state*) yang sesuai.

**[MODIFIKASI]** Salah satu permasalahan yang berkaitan dengan sinkronisasi adalah *race condition* dan *data race*. Keduanya dapat menyebabkan hasil pemrosesan tidak sesuai dengan kondisi sebenarnya karena beberapa proses melakukan operasi secara bersamaan tanpa pengaturan yang memadai.

Contoh permasalahan dapat ditemukan pada sistem e-commerce. Misalnya, sebuah produk memiliki stok sebanyak 10 unit dan dua pengguna, yaitu A dan B, membeli produk tersebut secara bersamaan. Kedua proses membaca stok yang sama, yaitu 10 unit. Setelah itu, masing-masing proses mengurangi stok menjadi 9 unit. Akibatnya, sistem mencatat dua pembelian tetapi stok akhir tetap menunjukkan 9 unit, padahal seharusnya tersisa 8 unit.

Permasalahan tersebut menunjukkan bahwa operasi membaca dan memperbarui data perlu dikelola agar tidak terjadi kehilangan perubahan (*lost update*).

**Perbedaan Data Race dan Race Condition**

| Aspek | Data Race | Race Condition |
|---|---|---|
| Fokus utama | Akses memori secara bersamaan | Urutan dan waktu eksekusi instruksi |
| Tingkat | Lebih dekat dengan level memori dan thread | Berkaitan dengan alur logika program |
| Penyebab | Beberapa thread mengakses lokasi memori yang sama, setidaknya satu melakukan penulisan, tanpa sinkronisasi yang sesuai | Hasil program bergantung pada urutan eksekusi yang tidak dapat diprediksi |
| Dampak | Perilaku tidak terdefinisi, korupsi memori, atau data tidak konsisten | Hasil yang salah, kesalahan logika bisnis, atau eksekusi ganda |
| Solusi | Mutex, lock, atau operasi atomic | Perbaikan alur kontrol, pemeriksaan kondisi secara tepat, dan transaksi database |

Berdasarkan perbedaan tersebut, data race lebih berfokus pada akses memori yang tidak terkoordinasi, sedangkan race condition berkaitan dengan ketergantungan hasil program terhadap urutan eksekusi. Keduanya dapat menimbulkan masalah pada aplikasi yang menjalankan banyak proses secara bersamaan.

**Mengapa Sinkronisasi Penting?**

Sinkronisasi memiliki beberapa fungsi penting dalam sistem terdistribusi, yaitu:

1. **Menjaga integritas data:** Mencegah konflik perubahan data akibat proses yang berjalan secara bersamaan.
2. **Sinkronisasi state:** Memastikan kondisi aplikasi tetap sesuai di berbagai node. Contohnya, permainan multiplayer harus memperbarui posisi, kesehatan, dan inventaris pemain agar seluruh pengguna melihat kondisi permainan yang konsisten.
3. **Koordinasi tugas:** Mengatur urutan dan hubungan antarproses agar pekerjaan dapat berjalan sesuai kebutuhan.
4. **Pengelolaan sumber daya:** Mengatur penggunaan sumber daya bersama agar tidak terjadi perebutan akses.
5. **Mendukung mekanisme recovery:** Mempertahankan informasi kondisi sistem agar proses pemulihan dapat dilakukan ketika terjadi gangguan.
6. **Efisiensi penggunaan sumber daya:** Mengurangi operasi yang berulang atau tidak diperlukan.
7. **Load balancing:** Membantu pembagian beban kerja antarbagian sistem.
8. **Mencegah deadlock:** Membantu mengatur penggunaan sumber daya agar proses tidak saling menunggu tanpa penyelesaian.
9. **Mendukung skalabilitas:** Memungkinkan sistem tetap terkoordinasi ketika jumlah proses, pengguna, atau node bertambah.

### 2. Tantangan dalam Sinkronisasi

Penerapan sinkronisasi pada sistem terdistribusi tidak selalu mudah. Setiap node dapat memiliki kondisi jaringan, kemampuan perangkat, dan waktu pemrosesan yang berbeda. Materi perkuliahan mengidentifikasi beberapa tantangan berikut.

**a. Network Latency dan Network Partitioning**

*Network latency* merupakan keterlambatan waktu yang dibutuhkan data untuk berpindah dari satu node ke node lainnya. Perbedaan keterlambatan dapat menyebabkan pesan diterima pada waktu yang berbeda dari urutan pengirimannya.

Sementara itu, *network partitioning* terjadi ketika sebagian node tidak dapat berkomunikasi dengan node lainnya akibat gangguan jaringan. Kondisi ini dapat menyulitkan proses koordinasi dan penyamaan data.

**b. Skalabilitas**

Ketika jumlah node dan proses bertambah, jumlah komunikasi dan koordinasi yang diperlukan juga dapat meningkat. Mekanisme sinkronisasi yang awalnya berjalan baik pada sistem kecil belum tentu efisien ketika diterapkan pada sistem yang lebih besar.

**c. Fault-Tolerant System**

Sistem terdistribusi harus mampu menghadapi kegagalan node, perangkat, maupun koneksi jaringan. Sinkronisasi perlu tetap mendukung koordinasi dan pemulihan ketika sebagian komponen mengalami gangguan.

**d. Concurrency Control**

Banyak proses dapat berjalan secara bersamaan dan mengakses sumber daya yang sama. Tanpa pengendalian, operasi tersebut berpotensi menghasilkan konflik atau perubahan data yang tidak sesuai.

**e. Data Consistency**

Setiap node perlu memiliki informasi yang konsisten. Perbedaan kondisi data antar-node dapat menyebabkan aplikasi memberikan hasil yang berbeda untuk keadaan yang seharusnya sama.

**f. Sinkronisasi Waktu**

Setiap komputer memiliki jam internal yang dapat menunjukkan waktu berbeda. Perbedaan tersebut dapat menyulitkan pencatatan log, pengurutan kejadian, dan koordinasi proses yang bergantung pada waktu.

### 3. Sinkronisasi Waktu Fisik

Sinkronisasi waktu fisik merupakan proses menyelaraskan *real-time clock* atau jam nyata pada berbagai perangkat dalam sistem terdistribusi dengan standar waktu yang sama. Tujuannya adalah agar setiap perangkat memiliki acuan waktu yang konsisten.

Sinkronisasi waktu fisik penting karena sistem terdistribusi sering kali membutuhkan informasi waktu untuk mencatat aktivitas, mengatur jadwal proses, dan menjaga konsistensi operasi.

Contohnya, ketika beberapa server menangani permintaan pengguna yang sama, waktu pada log masing-masing server dapat membantu administrator memahami urutan kejadian. Apabila jam setiap server berbeda jauh, proses penelusuran masalah menjadi lebih sulit.

**a. Standar Waktu**

Materi perkuliahan menjelaskan beberapa standar waktu yang berkaitan dengan sinkronisasi, yaitu:

1. **GMT (Greenwich Mean Time):** Standar waktu yang dicantumkan dalam materi sebagai standar yang sudah tidak digunakan.
2. **UTC (Coordinated Universal Time):** Standar waktu universal yang digunakan sebagai acuan bersama. Materi menjelaskan bahwa UTC didefinisikan oleh ITU dan digunakan sebagai standar sejak tahun 1963.
3. **TAI (International Atomic Time):** Waktu atom internasional yang menjadi dasar bagi UTC. TAI berasal dari istilah bahasa Prancis *Temps Atomique International*.
4. **LTC (Coordinated Lunar Time):** Standar waktu yang berkaitan dengan kebutuhan penentuan waktu di lingkungan Bulan dan dalam materi disebut masih dalam proses pengembangan.

**b. Sumber Waktu dan Atomic Clock**

Sumber waktu yang akurat dapat berasal dari *atomic clock*. Jam atom memanfaatkan karakteristik atom untuk menghasilkan pengukuran waktu dengan tingkat kestabilan yang tinggi.

Materi menjelaskan bahwa sumber waktu atom terdapat pada beberapa lingkungan, antara lain:

- **GPS Satellites:** Satelit GPS membawa atomic clock dan digunakan sebagai bagian dari sistem penentuan posisi serta penyediaan sinyal waktu.
- **Deep Space Atomic Clock (DSAC):** Teknologi jam atom yang diluncurkan NASA pada tahun 2019 untuk menguji kestabilan waktu pada wahana antariksa.
- **International Space Station (ISS):** Materi mencantumkan misi Atomic Clock Ensemble in Space (ACES) untuk menempatkan jam atom jenis *cold-atom clock* pada orbit rendah Bumi.
- **Ground Control:** Pengelolaan dan pemantauan acuan waktu juga dilakukan dari stasiun pengendali di darat.

**c. Alur Distribusi Waktu**

Sinkronisasi waktu dapat dilakukan melalui rangkaian sumber waktu dan perangkat jaringan. Berdasarkan materi, gambaran alurnya adalah:

`Master Atomic Clock → Atomic Clock pada GPS → GPS Signal → GPS Dongle → NTP/PTP Server → Client`

Sumber waktu yang akurat digunakan sebagai acuan, kemudian sinyal waktu diterima melalui perangkat GPS. Server yang telah memperoleh acuan waktu tersebut dapat menyediakan layanan sinkronisasi kepada komputer atau perangkat klien, seperti Linux, Windows, Mac, dan telepon seluler.

Dengan alur tersebut, perangkat yang terhubung dapat menggunakan acuan waktu yang sama tanpa harus memiliki atomic clock sendiri.

**d. Network Time Protocol (NTP)**

Network Time Protocol (NTP) merupakan protokol yang digunakan untuk menyinkronkan waktu perangkat melalui jaringan komputer. NTP memungkinkan komputer klien menyesuaikan jam sistemnya dengan sumber waktu atau server NTP.

Dalam materi perkuliahan ditunjukkan penggunaan **Chrony** sebagai salah satu implementasi untuk sinkronisasi waktu berbasis NTP. Chrony dapat digunakan pada sistem Linux dan beberapa sistem operasi lainnya.

Beberapa hal yang ditunjukkan dalam materi terkait penerapan Chrony meliputi:

- Instalasi paket Chrony.
- Pengaturan layanan sinkronisasi waktu.
- Pemeriksaan status layanan.
- Pemeriksaan sumber waktu menggunakan perintah `chronyc sources`.
- Pemeriksaan informasi sinkronisasi menggunakan `chronyc tracking`.

**[MODIFIKASI]** Dalam penerapannya, NTP membantu menjaga keseragaman waktu pada komputer yang saling berkomunikasi. Misalnya, server aplikasi dan server database dapat menggunakan sumber waktu yang sama sehingga pencatatan aktivitas lebih mudah dibandingkan apabila setiap perangkat menggunakan waktu lokal yang berbeda.

**e. Precision Time Protocol (PTP)**

Precision Time Protocol (PTP) merupakan protokol sinkronisasi waktu yang dibahas dalam materi sebagai alternatif untuk kebutuhan sinkronisasi yang lebih presisi. PTP distandardisasi oleh IEEE melalui standar IEEE 1588.

Materi mencantumkan beberapa perkembangan standar PTP:

- IEEE 1588-2002.
- IEEE 1588-2008 yang dikenal sebagai PTP Version 2.
- IEEE 1588-2019 yang mencakup penyempurnaan terhadap standar sebelumnya.
- IEEE 802.1AS, yaitu adaptasi PTP yang disebut gPTP dan digunakan pada konteks Audio Video Bridging (AVB) serta Time-Sensitive Networking (TSN).

Materi juga memperkenalkan proyek Linux PTP yang menyediakan implementasi PTP pada sistem Linux.

Salah satu persyaratan penting dalam penerapan PTP adalah dukungan **hardware timestamping** pada Network Interface Card (NIC). Fitur tersebut memungkinkan pencatatan waktu pada tingkat perangkat keras jaringan.

Apabila NIC tidak mendukung hardware timestamping, kemampuan sinkronisasi perangkat dapat terbatas. Karena itu, dukungan perangkat keras perlu diperiksa sebelum menerapkan PTP.

### 4. Sinkronisasi Waktu Logis dan Vector Clocks

Sinkronisasi waktu logis merupakan metode untuk menentukan urutan sebab-akibat dari kejadian (*causal order of events*) dalam sistem terdistribusi. Berbeda dengan sinkronisasi waktu fisik, waktu logis tidak bertujuan menyamakan jam perangkat dengan waktu dunia nyata.

Konsep ini berkaitan dengan hubungan antarperistiwa. Jika kejadian A terjadi sebelum B, kemudian B terjadi sebelum C, maka A juga terjadi sebelum C. Hubungan tersebut dikenal sebagai sifat transitif.

Materi menghubungkan sinkronisasi waktu logis dengan konsep yang diperkenalkan oleh Leslie Lamport.

**a. Vector Clocks**

Vector Clocks merupakan mekanisme untuk mencatat informasi urutan kejadian pada beberapa proses dalam sistem terdistribusi. Setiap proses memiliki sebuah vektor yang berisi penghitung kejadian dari masing-masing proses.

Materi memberikan contoh tiga proses, yaitu A, B, dan C. Masing-masing proses memiliki vektor awal:

- Proses A: `[0, 0, 0]`
- Proses B: `[0, 0, 0]`
- Proses C: `[0, 0, 0]`

Setiap posisi dalam vektor mewakili proses tertentu. Posisi pertama untuk A, posisi kedua untuk B, dan posisi ketiga untuk C.

**b. Aturan Pembaruan Vector Clocks**

Berdasarkan contoh pada materi, terdapat beberapa aturan dasar:

1. Setiap proses menambah nilai pada posisi vektornya sendiri ketika melakukan suatu kejadian (*event*).
2. Sebelum mengirim pesan, proses memperbarui penghitung lokal dan menyertakan nilai vector clock dalam pesan.
3. Ketika menerima pesan, proses menggabungkan informasi vector clock yang diterima dengan vektor lokal menggunakan nilai maksimum pada setiap posisi (*element-wise maximum*).
4. Setelah pembaruan penerimaan pesan, proses menambah penghitung lokalnya sendiri untuk mencatat kejadian penerimaan tersebut.

**c. Contoh Proses Vector Clocks**

Menggunakan tiga proses A, B, dan C seperti pada materi:

1. Pada awalnya, semua proses memiliki nilai `[0, 0, 0]`.
2. Proses A melakukan satu kejadian internal sehingga vektornya berubah menjadi `[1, 0, 0]`.
3. Sebelum mengirim pesan kepada B, A menambah penghitungnya menjadi `[2, 0, 0]`, kemudian mengirimkan nilai tersebut.
4. B menerima pesan dari A dan menggabungkan nilai yang diterima dengan vektor lokalnya. Hasilnya menjadi `[2, 0, 0]`.
5. Sebelum mengirim pesan kepada C, B menambah penghitung lokalnya sehingga pesan yang dikirim membawa nilai `[2, 1, 0]`.
6. C menerima pesan tersebut dan memperbarui vektornya menjadi `[2, 1, 0]`. Setelah mencatat kejadian penerimaan, nilai vektor C menjadi `[2, 1, 1]`.
7. C melakukan satu kejadian internal lagi sehingga nilainya berubah menjadi `[2, 1, 2]`.

Posisi akhir vector clock berdasarkan contoh tersebut adalah:

| Proses | Nilai Vector Clock |
|---|---|
| A | `[2, 0, 0]` |
| B | `[2, 1, 0]` |
| C | `[2, 1, 2]` |

**d. Menentukan Hubungan Antarperistiwa**

Untuk membandingkan dua vector clock, terdapat aturan berikut:

- Kejadian A mendahului B apabila seluruh komponen vector clock A bernilai lebih kecil atau sama dengan komponen yang bersesuaian pada vector clock B, dan setidaknya terdapat satu komponen yang lebih kecil.
- Dua kejadian dinyatakan konkuren atau independen apabila tidak terdapat hubungan urutan yang memenuhi aturan tersebut.

Contoh berdasarkan materi:

- `[0, 0, 0]` mendahului `[1, 0, 0]` karena semua komponen vektor pertama lebih kecil atau sama, dan terdapat satu komponen yang lebih kecil.
- `[2, 0, 0]` mendahului `[2, 1, 0]` karena kejadian pada A telah tercatat sebelum kejadian lanjutan pada B.
- `[2, 1, 2]` dan `[2, 0, 0]` tidak dapat dibandingkan sebagai hubungan sebab-akibat karena komponen pada vektor pertama tidak seluruhnya lebih kecil atau sama dengan komponen vektor kedua. Keduanya dinyatakan konkuren dalam perbandingan tersebut.

**[MODIFIKASI]** Vector Clocks berguna ketika sistem perlu mengetahui apakah suatu kejadian dipengaruhi oleh kejadian lain atau berlangsung secara independen. Informasi ini penting dalam sistem terdistribusi karena urutan pesan yang diterima tidak selalu sama dengan urutan kejadian yang sebenarnya terjadi pada setiap proses.

### 5. Mutual Exclusion pada Sistem Terdistribusi

Mutual Exclusion merupakan prinsip yang memastikan hanya satu proses atau thread yang dapat mengakses sumber daya bersama pada satu waktu. Tujuannya adalah mencegah konflik ketika beberapa proses membutuhkan akses terhadap sumber daya yang sama.

Contoh sumber daya bersama antara lain printer, file, dan database. Bagian program yang mengakses sumber daya bersama disebut **Critical Section (CS)**.

Apabila lebih dari satu proses memasuki critical section secara bersamaan tanpa pengaturan yang tepat, sistem dapat mengalami inkonsistensi atau kerusakan data.

**a. Critical Section**

Critical Section adalah bagian dari kode program yang melakukan akses terhadap sumber daya bersama. Dalam penerapan mutex, tujuan utamanya adalah mencegah terjadinya eksekusi critical section secara bersamaan oleh proses yang tidak diizinkan.

**b. Prinsip Mutual Exclusion**

Materi menjelaskan empat prinsip penting:

1. **Mutual Exclusion:** Hanya satu proses yang boleh menggunakan sumber daya bersama pada satu waktu.
2. **Progress:** Jika tidak ada proses yang sedang berada di critical section, proses yang membutuhkan akses harus dapat memperoleh kesempatan untuk masuk.
3. **Bounded Waiting:** Tidak boleh ada proses yang menunggu tanpa batas waktu untuk memperoleh akses.
4. **Fairness:** Permintaan akses harus dilayani secara wajar agar tidak ada proses yang terus-menerus diabaikan.

**c. Pendekatan Algoritma Mutual Exclusion**

Terdapat beberapa pendekatan yang dapat digunakan untuk mengatur akses terhadap critical section.

**1. Centralized Algorithm**

Pada algoritma terpusat, terdapat satu node yang bertindak sebagai koordinator untuk mengatur akses ke sumber daya bersama.

Tahapan kerjanya:

- Proses mengirimkan permintaan izin kepada koordinator.
- Koordinator memeriksa apakah critical section sedang digunakan.
- Jika tidak ada proses yang menggunakannya, koordinator memberikan izin.
- Setelah proses selesai, izin dilepaskan dan koordinator dapat memberikan akses kepada proses berikutnya.

Kelebihan:
- Mekanisme relatif sederhana.
- Biaya komunikasi relatif rendah karena koordinasi dilakukan melalui satu node.

Kekurangan:
- Koordinator menjadi *single point of failure*.
- Koordinator berpotensi menjadi bottleneck apabila menerima terlalu banyak permintaan.

**2. Ricart-Agrawala Algorithm**

Ricart-Agrawala merupakan algoritma mutual exclusion yang bekerja secara terdistribusi tanpa membutuhkan satu koordinator pusat.

Cara kerjanya adalah setiap proses mengirimkan pesan permintaan akses yang dilengkapi timestamp kepada proses lain. Proses hanya dapat memasuki critical section setelah mendapatkan balasan persetujuan dari seluruh proses yang diperlukan.

Menurut materi, setiap akses critical section membutuhkan komunikasi sebanyak:

`2 × (N − 1)`

Jumlah tersebut terdiri dari N−1 pesan permintaan dan minimal N−1 pesan balasan, dengan N sebagai jumlah proses.

Kelebihan:
- Tidak bergantung pada satu koordinator pusat.
- Koordinasi dilakukan secara terdistribusi.

Kekurangan:
- Membutuhkan banyak pesan komunikasi.
- Overhead komunikasi dapat meningkat ketika jumlah proses bertambah.

**3. Token-Based Algorithm**

Pada pendekatan ini, terdapat sebuah token unik yang beredar di antara proses. Proses hanya dapat memasuki critical section apabila memiliki token tersebut.

Karena token hanya satu, mekanisme ini membantu memastikan tidak ada dua proses yang menggunakan sumber daya bersama secara bersamaan melalui mekanisme token yang sama.

Kelebihan:
- Jumlah pesan untuk memasuki critical section dapat lebih sedikit.
- Kepemilikan token menjadi penanda hak akses.

Kekurangan:
- Jika token hilang, sistem membutuhkan mekanisme pemulihan.
- Deteksi kehilangan token dapat menjadi tantangan.

**[MODIFIKASI]** Ketiga algoritma tersebut memiliki pendekatan yang berbeda. Centralized Algorithm mengutamakan kemudahan pengelolaan melalui koordinator, Ricart-Agrawala mengandalkan komunikasi antarproses, sedangkan Token-Based menggunakan kepemilikan token sebagai syarat masuk ke critical section. Pemilihan pendekatan perlu mempertimbangkan jumlah proses, kebutuhan komunikasi, serta kemampuan sistem menghadapi kegagalan.

### 6. Pemilihan Koordinator

Dalam sistem terdistribusi, beberapa node atau proses terkadang membutuhkan satu koordinator untuk mengatur operasi bersama. Koordinator berperan dalam mengelola sumber daya, menyinkronkan operasi, dan membantu pengambilan keputusan yang berlaku bagi sistem.

Permasalahan muncul ketika koordinator mengalami kegagalan atau terdapat node baru yang bergabung. Sistem perlu memiliki mekanisme untuk menentukan koordinator pengganti agar koordinasi tetap dapat berlangsung.

**a. Algoritma Pemilihan Koordinator**

Materi memperkenalkan beberapa algoritma yang dapat digunakan:

1. **Bully Algorithm:** Algoritma pemilihan koordinator yang digunakan untuk menentukan proses yang berhak menjadi koordinator baru.
2. **Ring Algorithm:** Algoritma yang menggunakan pola komunikasi berbentuk cincin untuk mengoordinasikan proses pemilihan pemimpin.
3. **Raft atau Paxos:** Pendekatan berbasis konsensus yang digunakan untuk mencapai kesepakatan antaranggota sistem mengenai keputusan bersama.

Materi juga memberikan contoh teknologi yang berkaitan dengan pemilihan dan koordinasi koordinator:

- **Apache ZooKeeper:** Menggunakan protokol Zab (*ZooKeeper Atomic Broadcast*) yang dalam materi dijelaskan memiliki kemiripan dengan Paxos.
- **Kubernetes:** Materi mencantumkan penggunaan Raft melalui etcd untuk mendukung koordinasi dan penyimpanan kondisi klaster.

**[MODIFIKASI]** Pemilihan koordinator penting karena sistem terdistribusi tidak dapat selalu mengandalkan satu node yang sama. Ketika node utama mengalami gangguan, mekanisme pemilihan pemimpin membantu sistem menentukan pihak yang akan melanjutkan fungsi koordinasi. Dengan demikian, kegagalan satu komponen tidak harus langsung menghentikan seluruh aktivitas sistem.

---

## D. CONTOH PENERAPAN DAN ANALISIS

### 1. Contoh Penerapan

Beberapa penerapan konsep sinkronisasi dan koordinasi dalam bidang teknologi informasi dapat ditemukan pada kasus berikut.

**a. Sinkronisasi Stok Produk pada E-Commerce**

Sistem e-commerce harus mengatur proses pembelian ketika beberapa pengguna membeli produk yang sama pada waktu bersamaan. Jika setiap proses langsung mengubah stok tanpa pengaturan, hasil pembaruan dapat menjadi tidak konsisten.

Mekanisme sinkronisasi dan pengendalian akses dapat digunakan agar proses pembelian dilakukan secara terkoordinasi. Dengan demikian, jumlah stok yang tercatat dapat mencerminkan jumlah produk yang benar-benar tersisa.

**b. Sinkronisasi Waktu pada Server**

Sebuah aplikasi dapat menggunakan beberapa server untuk menangani permintaan pengguna. Server-server tersebut perlu memiliki acuan waktu yang konsisten agar pencatatan log dan penelusuran aktivitas dapat dilakukan dengan lebih mudah.

NTP dapat digunakan untuk menyelaraskan waktu perangkat melalui jaringan. Pada materi perkuliahan, Chrony ditampilkan sebagai salah satu implementasi yang dapat digunakan untuk kebutuhan tersebut.

**c. Sinkronisasi pada Sistem yang Membutuhkan Presisi Waktu**

PTP dapat digunakan pada lingkungan yang membutuhkan sinkronisasi waktu dengan dukungan perangkat jaringan yang sesuai. Materi menjelaskan pentingnya dukungan hardware timestamping pada NIC agar penerapan PTP dapat berjalan sesuai kebutuhan.

Contoh konteks yang disebutkan dalam materi adalah Audio Video Bridging (AVB) dan Time-Sensitive Networking (TSN) melalui adaptasi gPTP.

**d. Pengurutan Aktivitas Antarproses**

Dalam sistem yang terdiri dari beberapa proses, informasi waktu fisik belum tentu cukup untuk mengetahui hubungan sebab-akibat antarperistiwa. Vector Clocks dapat digunakan untuk mencatat informasi kejadian pada setiap proses sehingga hubungan urutan dan kejadian konkuren dapat dianalisis.

**e. Pengaturan Akses Database**

Ketika beberapa proses melakukan perubahan terhadap database yang sama, mekanisme mutual exclusion dapat membantu mengatur akses ke bagian data yang sedang digunakan.

Dengan adanya pengaturan tersebut, proses yang mengubah data tidak saling menimpa perubahan yang dilakukan oleh proses lain.

**f. Koordinasi Klaster**

Pada sistem yang terdiri dari beberapa node, koordinator dapat membantu mengelola sumber daya dan mengatur keputusan bersama. Ketika node koordinator mengalami kegagalan, algoritma pemilihan koordinator dapat digunakan untuk menentukan pemimpin pengganti.

### 2. Analisis

Sinkronisasi dan koordinasi merupakan bagian penting dalam menjaga keandalan sistem terdistribusi. Hal ini disebabkan oleh karakteristik sistem yang terdiri dari banyak node, proses, dan sumber daya yang dapat bekerja secara bersamaan.

Permasalahan seperti data race dan race condition menunjukkan bahwa operasi yang tampak sederhana dapat menghasilkan kesalahan apabila tidak dikelola dengan benar. Pada sistem e-commerce, misalnya, dua proses pembelian yang membaca dan memperbarui stok secara bersamaan dapat menyebabkan jumlah persediaan tidak sesuai dengan kondisi sebenarnya.

Sinkronisasi waktu fisik dan waktu logis juga memiliki fungsi yang berbeda. Sinkronisasi waktu fisik digunakan untuk menyelaraskan jam perangkat dengan acuan waktu bersama, sedangkan waktu logis digunakan untuk memahami urutan sebab-akibat antarperistiwa. Oleh karena itu, kedua mekanisme tersebut tidak dapat dianggap saling menggantikan.

NTP dan PTP merupakan contoh protokol yang berkaitan dengan sinkronisasi waktu fisik. Sementara itu, Vector Clocks membantu menggambarkan hubungan kejadian antarproses tanpa bergantung pada kesamaan jam nyata.

Pada pengelolaan sumber daya bersama, mutual exclusion diperlukan agar proses tidak melakukan akses yang saling bertentangan. Pemilihan algoritma seperti Centralized, Ricart-Agrawala, atau Token-Based perlu mempertimbangkan kebutuhan sistem, biaya komunikasi, dan risiko kegagalan.

Selain itu, pemilihan koordinator menjadi penting ketika sistem membutuhkan pihak yang mengatur koordinasi antar-node. Mekanisme pemilihan pemimpin membantu sistem menentukan koordinator baru ketika terjadi kegagalan.

Secara keseluruhan, sinkronisasi bukan hanya berkaitan dengan penyamaan waktu, tetapi juga mencakup pengaturan proses, urutan kejadian, akses sumber daya, dan koordinasi antar-node. Penerapan mekanisme yang sesuai dapat membantu sistem terdistribusi menjaga konsistensi, mengurangi konflik, dan tetap beroperasi ketika menghadapi berbagai tantangan.

---

## E. PENGGUNAAN ARTIFICIAL INTELLIGENCE (AI)

### 1. AI yang Digunakan

- Nama AI: ChatGPT GPT-6
- Tujuan penggunaan: Membantu memahami, menganalisis, menyusun, dan mengembangkan rangkuman materi perkuliahan.
- Sumber utama: Materi perkuliahan yang diberikan oleh dosen, yaitu file 03--sinkronisasi-sistem-terdistribusi.pdf.

### 2. Prompt yang Digunakan

Berikut prompt yang digunakan untuk menghasilkan rangkuman awal:

> Analisis seluruh isi file PDF materi Teori Sistem Terdistribusi dan Terdesentralisasi pertemuan 3 yang saya lampirkan. Susun rangkuman lengkap dalam format Markdown dengan mengikuti template README bagian A sampai G yang telah saya berikan. Gunakan materi dosen sebagai sumber utama dan pertahankan istilah serta konsep sesuai materi. Kembangkan penjelasan agar mudah dipahami, tambahkan contoh penerapan yang relevan dengan bidang Informatika, serta berikan analisis terhadap konsep yang dibahas. Pastikan pembahasan mencakup tujuan pembelajaran, pengertian sinkronisasi, tantangan sinkronisasi, waktu fisik, NTP, PTP, waktu logis, Vector Clocks, mutual exclusion, dan pemilihan koordinator. Jangan mengarang informasi atau referensi. Gunakan bahasa Indonesia yang natural seperti laporan mahasiswa S1 Informatika dan hasilkan README lengkap yang siap dimasukkan ke GitHub.

### 3. Bagian yang Disesuaikan dari Keluaran AI

Bagian dari hasil rangkuman yang dikembangkan atau disesuaikan meliputi:

1. **Pengertian dan Pentingnya Sinkronisasi:** Penjelasan diperluas dengan membahas hubungan sinkronisasi terhadap data race, race condition, dan konsistensi data. Contoh pembelian produk pada e-commerce juga dijelaskan secara lebih terstruktur.
2. **Sinkronisasi Waktu Fisik dan Protokolnya:** Pembahasan mengenai UTC, TAI, atomic clock, GPS, NTP, Chrony, dan PTP dikembangkan agar alur sinkronisasi waktu lebih mudah dipahami.
3. **Sinkronisasi Waktu Logis dan Vector Clocks:** Contoh tiga proses A, B, dan C dijelaskan secara bertahap, termasuk aturan pembaruan vector clock dan cara menentukan hubungan antarperistiwa.
4. **Mutual Exclusion dan Pemilihan Koordinator:** Penjelasan mengenai Critical Section, prinsip mutual exclusion, serta algoritma Centralized, Ricart-Agrawala, Token-Based, Bully, Ring, Raft, dan Paxos dikembangkan dengan membahas fungsi, cara kerja, kelebihan, dan keterbatasannya sesuai informasi yang tersedia dalam materi.

Penyesuaian dilakukan untuk memperjelas pemahaman materi, memperbaiki penjelasan yang kurang lengkap, serta menambahkan contoh dan analisis yang relevan dengan bidang Informatika.

### 4. Penanda Hasil Modifikasi

Bagian yang mengalami pengembangan atau penyesuaian dari hasil awal AI diberikan tanda **[MODIFIKASI]** pada bagian terkait dalam rangkuman.

Keterangan:
- **[MODIFIKASI]**: Bagian yang mengalami pengembangan, penambahan penjelasan, perbaikan, atau penyesuaian.
- Bagian tanpa tanda: Bagian yang dipertahankan karena sudah sesuai dengan materi dan tidak memerlukan perubahan substantif.

---

## F. KESIMPULAN

Berdasarkan materi pertemuan ketiga, sinkronisasi dan koordinasi merupakan hal penting dalam sistem terdistribusi karena setiap node dapat menjalankan proses secara bersamaan dan mengakses sumber daya yang sama. Tanpa mekanisme yang tepat, sistem dapat mengalami konflik data, ketidakkonsistenan, maupun gangguan koordinasi.

Materi ini membahas sinkronisasi waktu fisik menggunakan standar waktu dan protokol seperti NTP serta PTP, kemudian sinkronisasi waktu logis menggunakan Vector Clocks untuk menentukan hubungan sebab-akibat antarperistiwa. Selain itu, mutual exclusion digunakan untuk mengatur akses terhadap sumber daya bersama, sedangkan algoritma pemilihan koordinator membantu menjaga koordinasi ketika terjadi perubahan atau kegagalan node.

Dengan memahami konsep-konsep tersebut, mahasiswa dapat mengetahui bagaimana sistem terdistribusi menjaga konsistensi data, mengatur proses yang berjalan bersamaan, dan mempertahankan koordinasi antar-node. Pengetahuan ini menjadi dasar penting dalam memahami pengembangan sistem jaringan, server, database terdistribusi, dan teknologi komputasi lainnya.

---

## G. DAFTAR REFERENSI

1. Purnomosidi, B. (Tanpa tahun). *03: Sinkronisasi dan Koordinasi pada Sistem Terdistribusi*. Materi Perkuliahan Teori Sistem Terdistribusi dan Terdesentralisasi, Program Studi Informatika, Fakultas Teknologi Informasi, Universitas Teknologi Digital Indonesia.
2. GeeksforGeeks. (Tanpa tahun). *Distributed System – Types of Distributed Deadlock*. https://www.geeksforgeeks.org/operating-systems/distributed-system-types-of-distributed-deadlock/
3. National Institute of Standards and Technology (NIST). (Tanpa tahun). *How UTC(NIST) and UTC Are Related*. https://www.nist.gov/pml/time-and-frequency-division/how-utcnist-related-coordinated-universal-time-utc-international
4. The Linux PTP Project. (Tanpa tahun). *Linux PTP Project*. https://linuxptp.nwtime.org/
5. Chrony Project. (Tanpa tahun). *Chrony: Introduction*. https://chrony-project.org/

---

**Dokumentasi Tugas**

- Repository: [disdec-teori](https://github.com/hendfirmsh/disdec-teori)
- Direktori: `03/`
- File: `README.md`

---
