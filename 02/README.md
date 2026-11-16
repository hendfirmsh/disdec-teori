# RANGKUMAN MATERI TEORI SISTEM TERDISTRIBUSI DAN TERDESENTRALISASI

## PERTEMUAN 02

---

## A. IDENTITAS MATERI


| Keterangan | Informasi |
|---|---|
| Mata Kuliah | Teori Sistem Terdistribusi dan Terdesentralisasi |
| Program Studi | S1 Informatika |
| Kode Mata Kuliah | FIF25002T |
| Pertemuan | 2 |
| Topik Materi | Proses dan Komunikasi Antar Proses pada Sistem Terdistribusi |
| Dosen Pengampu | Dr. Bambang Purnomosidi D. P. |
| Institusi | Universitas Teknologi Digital Indonesia (UTDI) |
| Sumber Materi | Proses-dan-Komunikasi-Antar-Proses.pdf |
| AI yang Digunakan | ChatGPT GPT-6 |
| Format Dokumen | Markdown (.md) |
---

## B. TUJUAN PEMBELAJARAN

Setelah mempelajari materi pada pertemuan ini, mahasiswa diharapkan mampu:

1. Menjelaskan konsep proses (*process*) dan bagaimana proses dikelola dalam sistem operasi maupun sistem terdistribusi.
2. Memahami berbagai mekanisme komunikasi antarproses (*Inter-Process Communication*) seperti Message Passing, Remote Procedure Call (RPC), dan Middleware.
3. Menganalisis permasalahan yang dapat terjadi dalam komunikasi antarproses, khususnya sinkronisasi, reliabilitas, pengurutan pesan, keamanan, dan performa.
4. Memahami konsep sinkronisasi waktu dan penggunaan Logical Clock untuk menentukan urutan kejadian dalam sistem terdistribusi.
5. Menjelaskan pentingnya koordinasi antarproses serta menghubungkannya dengan teknologi seperti microservices, cloud computing, dan distributed messaging.

---

## C. RANGKUMAN MATERI

### 1. Konsep Dasar Proses (Process)

**[MODIFIKASI]**

Proses (*process*) merupakan sebuah program yang sedang dieksekusi oleh komputer. Program yang tersimpan di dalam media penyimpanan belum dapat dikatakan sebagai proses sebelum dijalankan. Ketika program dieksekusi, sistem operasi akan menyediakan sumber daya yang diperlukan agar program tersebut dapat bekerja.

Sumber daya yang digunakan oleh proses antara lain:

- **CPU:** digunakan untuk menjalankan instruksi program.
- **Memory (RAM):** menyimpan instruksi dan data yang sedang digunakan.
- **Process State:** menunjukkan kondisi proses selama menjalankan tugasnya.
- **Program Counter:** menyimpan posisi instruksi yang akan dijalankan berikutnya.
- **Register:** menyimpan data sementara yang diperlukan CPU.
- **I/O Resources:** digunakan untuk melakukan operasi input dan output.

Dalam satu komputer, beberapa proses dapat berjalan secara bersamaan. Sistem operasi mengatur penggunaan CPU dan sumber daya lainnya agar setiap proses memperoleh kesempatan untuk menjalankan pekerjaannya.

Salah satu mekanisme yang digunakan adalah *context switching*, yaitu proses pergantian penggunaan CPU dari satu proses ke proses lainnya. Ketika pergantian terjadi, sistem operasi menyimpan kondisi proses sebelumnya dan memulihkan kondisi proses berikutnya agar eksekusi dapat dilanjutkan.

**Contoh:**

Ketika seseorang membuka browser, aplikasi pemutar musik, dan editor kode secara bersamaan, masing-masing aplikasi dapat menjalankan proses tersendiri. Sistem operasi mengatur penggunaan CPU dan RAM agar aplikasi tersebut dapat bekerja tanpa harus menjalankan semuanya pada waktu yang benar-benar bersamaan.

### 2. Manajemen Proses (Process Management)

Materi menjelaskan tiga bagian utama dalam manajemen proses, yaitu *process creation*, *process migration*, dan *process monitoring*.

**a. Process Creation**

*Process creation* merupakan proses pembuatan atau pembentukan proses baru ketika suatu program mulai dijalankan atau ketika proses lain membutuhkan proses tambahan.
Sistem operasi akan menyiapkan informasi proses, menyediakan sumber daya yang diperlukan, dan mengatur proses agar dapat mulai dieksekusi.
Contohnya, ketika aplikasi server menerima banyak permintaan pengguna, sistem dapat membuat proses atau unit eksekusi tambahan untuk menangani pekerjaan tersebut.

**b. Process Migration**

*Process migration* merupakan perpindahan proses atau pelaksanaan pekerjaan dari satu komputer atau node ke node lainnya.
Dalam sistem terdistribusi, mekanisme ini dapat digunakan untuk membantu pemerataan beban kerja (*load balancing*), mendekatkan pemrosesan ke sumber daya yang dibutuhkan, atau mengoptimalkan penggunaan sumber daya komputasi.
Sebagai contoh, sebuah sistem cloud dapat mengatur ulang penempatan beban kerja dari satu mesin ke mesin lain ketika terjadi peningkatan penggunaan sumber daya.

**c. Process Monitoring**

*Process monitoring* merupakan kegiatan mengamati dan memantau proses yang sedang berjalan. Tujuannya untuk mengetahui kondisi proses, penggunaan sumber daya, serta mendeteksi masalah yang dapat mengganggu jalannya sistem.
Contohnya adalah pemantauan penggunaan CPU, RAM, status layanan, dan aktivitas proses pada server.
Ketiga bagian tersebut saling berhubungan. Proses perlu dibuat sebelum dijalankan, dapat dipindahkan sesuai kebutuhan sistem, dan perlu dipantau agar tetap berjalan sebagaimana mestinya.

### 3. Sistem Terdistribusi dan Komunikasi Antarproses

Sistem terdistribusi merupakan sekumpulan komputer atau *nodes* yang berdiri secara independen, tetapi bekerja sama dan berkoordinasi sehingga dapat dipandang sebagai satu kesatuan sistem secara logis.
Setiap node dapat menjalankan prosesnya sendiri. Namun, karena node tersebut tidak berada dalam satu lingkungan komputasi yang sama, diperlukan komunikasi agar masing-masing proses dapat saling bertukar informasi.

**[MODIFIKASI]**

Berbeda dengan sistem pada satu komputer yang memungkinkan proses berbagi sumber daya tertentu, proses pada sistem terdistribusi dapat berada di komputer yang berbeda dan terhubung melalui jaringan. Oleh sebab itu, komunikasi tidak dapat hanya mengandalkan akses langsung terhadap memori lokal.
Proses harus menggunakan mekanisme komunikasi melalui jaringan untuk mengirimkan permintaan, menerima informasi, dan memberikan respons kepada proses lain.

Sebagai gambaran:

1. Node A menjalankan proses untuk menerima permintaan pengguna.
2. Node B menjalankan proses untuk mengolah data.
3. Node C menjalankan proses untuk menyimpan hasil pengolahan.
4. Ketiga node saling berkomunikasi agar permintaan pengguna dapat diselesaikan.

**Contoh penerapan:**

- **Multiplayer Games:** server permainan menerima informasi posisi dan tindakan pemain, kemudian menyebarkan informasi tersebut kepada pemain lain.
- **Gojek atau Grab:** antarmuka pengguna berkomunikasi dengan layanan pengemudi, pelacakan lokasi, dan perhitungan biaya perjalanan.
- **WhatsApp:** proses komunikasi memungkinkan pengiriman pesan dan panggilan melalui infrastruktur yang terdiri dari berbagai komponen sistem.
Dari contoh tersebut, dapat dipahami bahwa komunikasi antarproses merupakan bagian penting dalam sistem terdistribusi. Tanpa komunikasi, setiap node hanya akan bekerja secara terpisah dan tidak dapat menyelesaikan tugas yang membutuhkan koordinasi beberapa layanan.

### 4. Model Komunikasi Pesan

Dalam sistem terdistribusi, komunikasi antarproses dapat dilakukan melalui beberapa model. Materi membagi model komunikasi pesan menjadi komunikasi langsung dan tidak langsung.

**a. Komunikasi Langsung (Direct Communication)**

Komunikasi langsung merupakan mekanisme ketika satu proses berkomunikasi secara langsung dengan proses lain melalui saluran komunikasi tertentu.
Salah satu teknologi yang digunakan adalah *socket*. Socket menyediakan antarmuka komunikasi agar aplikasi dapat mengirim dan menerima data melalui jaringan.
Secara umum, proses komunikasinya adalah:

1. Server membuka socket dan menentukan alamat serta port komunikasi.
2. Server menunggu permintaan koneksi.
3. Client membuat koneksi menuju server.
4. Client mengirimkan pesan atau data.
5. Server menerima dan memproses data tersebut.
6. Server mengirimkan respons kepada client.

**Contoh:**

Aplikasi client mengirimkan permintaan login ke server melalui socket. Server menerima data tersebut, memeriksa informasi pengguna, kemudian mengirimkan hasil autentikasi kembali kepada client.

**b. Komunikasi Tidak Langsung (Indirect Communication)**

Komunikasi tidak langsung merupakan mekanisme pertukaran pesan yang tidak mengharuskan pengirim dan penerima berkomunikasi secara langsung. Pesan dapat disimpan terlebih dahulu melalui perantara seperti *mailbox* atau *message queue*.
Pengirim memasukkan pesan ke dalam saluran komunikasi, kemudian penerima mengambil dan memproses pesan tersebut.
Keuntugan pendekatan ini adalah pengirim dan penerima tidak harus selalu aktif pada waktu yang sama.

**Contoh:**

Sebuah aplikasi menerima pesanan dari pengguna, kemudian memasukkan informasi pesanan ke dalam message queue. Layanan lain mengambil pesan tersebut untuk memproses pembayaran atau menyiapkan pesanan.

**c. Publish/Subscribe (Pub/Sub)**

Publish/Subscribe merupakan pola komunikasi ketika pengirim pesan (*publisher*) mengirimkan informasi ke suatu *topic*, sedangkan penerima (*subscriber*) berlangganan pada topic yang dibutuhkan.
Publisher tidak perlu mengetahui secara langsung siapa saja yang menerima pesannya.
Mekanisme sederhananya:

1. Publisher menghasilkan sebuah pesan.
2. Pesan dikirimkan ke topic tertentu.
3. Sistem perantara mendistribusikan pesan kepada subscriber yang berlangganan.
4. Subscriber menerima dan memproses pesan sesuai kebutuhannya.

**Contoh:**

Dalam aplikasi transportasi online, perubahan status perjalanan dapat dipublikasikan ke sebuah topic. Layanan notifikasi dan layanan pemantauan perjalanan dapat menerima informasi tersebut tanpa harus saling memanggil secara langsung.

### 5. Proses pada Sistem Terdistribusi

Pada sistem terdistribusi, proses dapat berada pada node atau komputer yang berbeda. Setiap komputer mempunyai sumber daya dan memori lokal masing-masing.
Salah satu karakteristik penting yang dijelaskan dalam materi adalah tidak adanya *shared memory* secara langsung antara proses yang berada pada node berbeda.

**[MODIFIKASI]**

Shared memory merupakan mekanisme komunikasi yang memungkinkan beberapa proses membaca dan menulis pada area memori yang sama. Pendekatan ini dapat digunakan pada satu komputer, tetapi tidak cocok sebagai mekanisme komunikasi langsung antarproses pada komputer yang berbeda karena masing-masing node memiliki ruang memori lokal sendiri.
Oleh karena itu, sistem terdistribusi memerlukan IPC yang dapat bekerja melalui jaringan.
Misalnya, proses pada server A tidak dapat langsung membaca variabel yang berada di RAM server B. Jika membutuhkan data tersebut, proses harus mengirimkan permintaan melalui mekanisme komunikasi dan menerima hasilnya melalui jaringan.

### 6. Inter-Process Communication (IPC)

*Inter-Process Communication* atau IPC merupakan mekanisme yang memungkinkan dua proses atau lebih saling bertukar informasi dan berkoordinasi.
Dalam materi perkuliahan dijelaskan empat jenis IPC utama:

1. Shared Memory
2. Message Passing
3. Remote Procedure Call (RPC)
4. Middleware

**a. Shared Memory**

Shared memory memungkinkan beberapa proses mengakses area memori yang sama untuk membaca maupun menulis data.
Kelebihannya adalah pertukaran data dapat dilakukan secara efisien karena proses tidak harus selalu mengirimkan pesan melalui jaringan.
Namun, shared memory tidak cocok untuk komunikasi langsung antarproses pada node yang berbeda dalam sistem terdistribusi. Setiap node memiliki memori lokal masing-masing.

**b. Message Passing**

Message Passing merupakan mekanisme komunikasi dengan cara mengirimkan dan menerima pesan antarproses.
Setiap proses dapat mengirimkan informasi kepada proses lain tanpa harus mengakses memori internal proses tersebut.
Pendekatan ini sesuai dengan sistem terdistribusi karena pertukaran informasi dapat dilakukan melalui jaringan.

**c. Remote Procedure Call (RPC)**

RPC memungkinkan suatu proses meminta proses lain yang berada pada komputer berbeda untuk menjalankan prosedur atau fungsi tertentu.
Dengan pendekatan ini, pengembang dapat menggunakan pola pemanggilan fungsi yang lebih sederhana tanpa harus mengelola seluruh detail komunikasi jaringan secara manual.

**d. Middleware**

Middleware merupakan perangkat lunak perantara yang membantu aplikasi berkomunikasi dan bertukar informasi.
Middleware dapat menyediakan layanan seperti pengiriman pesan, pengelolaan antrean, dan penghubung antar aplikasi yang menggunakan teknologi berbeda.
Keempat pendekatan tersebut mempunyai kegunaan masing-masing. Dalam sistem terdistribusi, Message Passing, RPC, dan Middleware menjadi pendekatan yang relevan untuk komunikasi melalui jaringan, sedangkan Shared Memory lebih sesuai untuk lingkungan yang memiliki ruang memori bersama.

### 7. Message Passing dan Message Passing Interface (MPI)

Message Passing merupakan metode komunikasi antarproses dengan cara mengirimkan pesan dari satu proses ke proses lainnya.
Pesan dapat berisi data, instruksi, atau informasi yang dibutuhkan oleh proses penerima untuk melanjutkan pekerjaannya.

**[MODIFIKASI]**

Mekanisme Message Passing dapat digunakan ketika beberapa proses berjalan pada komputer yang sama maupun pada komputer berbeda. Dalam sistem terdistribusi, pesan menjadi sarana pertukaran informasi karena proses tidak dapat mengakses memori lokal node lain secara langsung.

Alur sederhananya:

1. Proses pengirim menyiapkan data.
2. Proses pengirim mengirimkan pesan melalui antarmuka komunikasi.
3. Pesan diteruskan melalui jaringan.
4. Proses penerima menerima pesan.
5. Proses penerima mengolah data yang diterima.

**Message Passing Interface (MPI)**

MPI merupakan standar yang digunakan untuk komunikasi antarproses, terutama pada lingkungan komputasi paralel dan *high-performance computing*.
MPI menyediakan antarmuka komunikasi yang memungkinkan beberapa proses bertukar data dan bekerja sama dalam menyelesaikan perhitungan.
Materi mencantumkan MPI versi 5.0 sebagai versi terakhir hingga Oktober 2026.
Salah satu implementasinya adalah `mpi4py`, yaitu pustaka Python yang menyediakan akses terhadap MPI sehingga programmer dapat membuat program paralel menggunakan bahasa Python.

**Contoh penerapan:**

Misalnya, sebuah perhitungan ilmiah membutuhkan pengolahan data dalam jumlah besar. Data dapat dibagi menjadi beberapa bagian dan diproses oleh sejumlah proses. Setelah selesai, hasil setiap proses dikirimkan kembali untuk digabungkan.
Dengan demikian, pekerjaan dapat diselesaikan secara paralel dan waktu pemrosesan berpotensi menjadi lebih efisien.

### 8. Remote Procedure Call (RPC)

Remote Procedure Call atau RPC merupakan mekanisme yang memungkinkan sebuah program memanggil prosedur atau fungsi yang berada pada komputer lain melalui jaringan.
Pada pemanggilan fungsi biasa, fungsi dijalankan dalam lingkungan program yang sama. Sementara itu, RPC memungkinkan pemanggilan dilakukan terhadap layanan yang berada di komputer berbeda.

**[MODIFIKASI] Mekanisme kerja RPC:**

1. Client memanggil fungsi atau prosedur yang disediakan oleh server.
2. Client Stub menerima pemanggilan tersebut dan menyiapkan data untuk dikirimkan.
3. Permintaan diteruskan melalui jaringan menuju server.
4. Server Stub menerima permintaan dan meneruskannya kepada prosedur yang sesuai.
5. Server menjalankan prosedur dan menghasilkan hasil pemrosesan.
6. Hasil dikirimkan kembali kepada client.
7. Client menerima hasil seolah-olah memperoleh nilai dari pemanggilan fungsi.

Stub berperan sebagai perantara yang membantu proses komunikasi antara aplikasi client dan server.

**Contoh: gRPC**

gRPC merupakan salah satu teknologi yang menerapkan konsep RPC. Teknologi ini memungkinkan aplikasi yang menggunakan bahasa pemrograman berbeda untuk saling berkomunikasi melalui layanan yang didefinisikan.
Contohnya, aplikasi Android dapat meminta layanan pada server yang dikembangkan menggunakan C++ atau bahasa lain yang didukung.
Client mengirimkan permintaan kepada metode layanan tertentu, kemudian server memproses permintaan dan mengirimkan respons.
RPC mempermudah komunikasi antar layanan karena pengembang dapat berfokus pada fungsi yang dipanggil tanpa harus menangani seluruh proses pertukaran data secara manual.

### 9. Message-Oriented Middleware (MOM)

Message-Oriented Middleware atau MOM merupakan infrastruktur perangkat lunak yang memfasilitasi komunikasi dan pertukaran data antar aplikasi melalui pesan.
Pesan menjadi unit informasi mandiri yang dikirimkan dari satu aplikasi ke aplikasi lainnya.
Berbeda dengan komunikasi langsung yang mengharuskan proses berinteraksi secara langsung, MOM memungkinkan pengiriman dan penerimaan pesan dilakukan secara asinkron.

**[MODIFIKASI] Mekanisme kerja MOM:**

1. Aplikasi pengirim menghasilkan pesan.
2. Pesan dimasukkan ke dalam sistem middleware.
3. Middleware mengelola pesan sesuai saluran atau antrean yang digunakan.
4. Aplikasi penerima mengambil pesan ketika siap memprosesnya.
5. Aplikasi penerima melakukan pengolahan terhadap pesan tersebut.

Pendekatan ini membantu mengurangi ketergantungan waktu antara aplikasi pengirim dan penerima.

**Standar dan Protokol MOM**

Materi menjelaskan beberapa standar dan protokol yang berkaitan dengan MOM:

| No. | Standar / Protokol | Penjelasan |
|---|---|---|
| 1 | XATMI | Spesifikasi dari X/Open Group yang berkaitan dengan komunikasi aplikasi dalam Distributed Transaction Processing. |
| 2 | AMQP | Advanced Message Queuing Protocol, protokol pertukaran pesan yang umum digunakan pada aplikasi enterprise. |
| 3 | HLA IEEE 1516 | High Level Architecture, standar untuk interoperabilitas dalam lingkungan simulasi. |
| 4 | MQTT | Message Queuing Telemetry Transport, protokol komunikasi pesan yang umum digunakan pada perangkat dengan sumber daya terbatas. |
| 5 | DDS | Data Distribution Service, standar komunikasi dan distribusi data dari Object Management Group (OMG). |
| 6 | XMPP | Extensible Messaging and Presence Protocol, protokol komunikasi berbasis pesan dan informasi kehadiran pengguna. |

Setiap protokol memiliki karakteristik dan kebutuhan penggunaan yang berbeda. MQTT, misalnya, sesuai untuk komunikasi perangkat IoT yang memiliki keterbatasan sumber daya, sedangkan AMQP sering digunakan pada sistem pertukaran pesan aplikasi enterprise.

### 10. Studi Kasus: Microservices

Microservices merupakan pendekatan arsitektur perangkat lunak yang membagi aplikasi menjadi beberapa layanan kecil yang memiliki tanggung jawab tertentu.

Setiap layanan dapat dikembangkan dan dijalankan secara relatif independen, tetapi tetap saling berkomunikasi untuk menyelesaikan kebutuhan aplikasi secara keseluruhan.

**[MODIFIKASI] Contoh penerapan:**

Misalnya, sebuah aplikasi toko online mempunyai beberapa layanan berikut:

- **User Service:** mengelola informasi dan akun pengguna.
- **Product Service:** mengelola data produk dan stok.
- **Order Service:** mengelola pesanan pelanggan.
- **Payment Service:** menangani proses pembayaran.
- **Notification Service:** mengirimkan pemberitahuan kepada pengguna.

Ketika pengguna melakukan pembelian, Order Service dapat berkomunikasi dengan Product Service untuk memeriksa ketersediaan barang. Selanjutnya, Payment Service menangani pembayaran dan Notification Service memberikan informasi mengenai status transaksi.
Komunikasi antarlayanan tersebut dapat menggunakan RPC maupun sistem messaging sesuai kebutuhan.
Keuntungan pendekatan microservices adalah setiap layanan dapat dikembangkan, diperbarui, dan diskalakan secara lebih independen.
Namun, semakin banyak layanan yang terlibat, semakin kompleks pula komunikasi, pemantauan, keamanan, dan pengelolaan konsistensi data yang diperlukan.

### 11. Komunikasi Sinkron dan Asinkron

Dalam sistem terdistribusi, komunikasi dapat dilakukan secara sinkron maupun asinkron.

**a. Komunikasi Sinkron (Synchronous Communication)**

Komunikasi sinkron merupakan pola komunikasi ketika proses pengirim menunggu respons dari proses penerima sebelum melanjutkan pekerjaan yang bergantung pada hasil komunikasi tersebut.

Alur sederhananya:

1. Client mengirimkan permintaan kepada server.
2. Client menunggu respons.
3. Server memproses permintaan.
4. Server mengirimkan hasil.
5. Client menerima respons dan melanjutkan pekerjaan.

**Contoh:**

Ketika pengguna melakukan login, aplikasi mengirimkan informasi autentikasi kepada server. Aplikasi kemudian menunggu hasil pemeriksaan sebelum menentukan apakah pengguna dapat masuk ke sistem.
Kelebihan komunikasi sinkron adalah alur permintaan dan respons mudah dipahami. Namun, proses yang menunggu dapat mengalami keterlambatan apabila server lambat atau jaringan bermasalah.

**b. Komunikasi Asinkron (Asynchronous Communication)**

Komunikasi asinkron memungkinkan proses pengirim melanjutkan pekerjaannya tanpa harus menunggu penerima menyelesaikan seluruh pemrosesan pesan.
Pesan dapat disimpan dalam antrean atau dikelola melalui middleware sebelum diproses oleh penerima.

Alur sederhananya:

1. Client atau aplikasi mengirimkan pesan.
2. Pesan diterima oleh sistem perantara.
3. Pengirim dapat melanjutkan pekerjaan.
4. Penerima mengambil pesan ketika siap.
5. Penerima memproses pesan secara terpisah.

**Contoh:**

Ketika pengguna melakukan pemesanan, sistem dapat menyimpan pesanan terlebih dahulu ke message queue. Proses pengiriman email konfirmasi kemudian dilakukan oleh layanan notifikasi tanpa harus membuat pengguna menunggu proses email selesai.

**Perbandingan:**

| Aspek | Sinkron | Asinkron |
|---|---|---|
| Respons | Pengirim menunggu respons | Pengirim tidak harus menunggu pemrosesan selesai |
| Ketergantungan waktu | Lebih tinggi | Lebih rendah |
| Mekanisme umum | Request-response | Message queue atau Pub/Sub |
| Kelebihan | Alur komunikasi lebih sederhana | Lebih fleksibel untuk pekerjaan latar belakang |
| Tantangan | Waktu tunggu dan keterlambatan | Pengelolaan antrean dan status pesan |

Pemilihan metode komunikasi harus disesuaikan dengan kebutuhan sistem. Operasi yang membutuhkan hasil langsung dapat menggunakan komunikasi sinkron, sedangkan pekerjaan yang dapat dilakukan di belakang layar lebih sesuai menggunakan komunikasi asinkron.

### 12. Permasalahan dalam Komunikasi Antarproses

Komunikasi antarproses tidak selalu berjalan dengan sempurna. Ada beberapa masalah yang perlu diperhatikan agar sistem terdistribusi tetap dapat beroperasi dengan baik.

**a. Reliability**

Reliability merupakan kemampuan sistem untuk memastikan pesan dapat dikirim dan diterima secara lengkap serta sesuai dengan kebutuhan komunikasi.
Permasalahan dapat muncul ketika terjadi kehilangan paket, gangguan jaringan, atau sistem mengalami crash.
Solusi yang dijelaskan dalam materi:

1. **Acknowledgement:** penerima memberikan konfirmasi bahwa pesan telah diterima.
2. **Retransmission:** pengirim mengirimkan ulang pesan ketika pesan sebelumnya tidak berhasil diterima.
3. **TCP:** menggunakan protokol transport yang menyediakan pengiriman data secara andal dan berurutan.

Perlu diperhatikan bahwa pengiriman ulang dapat menyebabkan pesan diterima lebih dari satu kali. Oleh karena itu, aplikasi yang memproses transaksi perlu mempertimbangkan penanganan duplikasi pesan.

**b. Ordering**

Ordering merupakan kemampuan sistem untuk menjaga agar pesan diproses berdasarkan urutan yang dapat diprediksi dan logis.
Permasalahan ini penting ketika urutan pesan memengaruhi hasil pemrosesan.
Contohnya, pada aplikasi perbankan, instruksi penyetoran dan penarikan harus diproses dengan memperhatikan urutan transaksi agar saldo tidak menghasilkan nilai yang keliru.
Beberapa mekanisme yang dicantumkan dalam materi meliputi:

- Pipes dengan prinsip FIFO (*First In, First Out*).
- Message queues.
- Shared memory.
- Sockets dan Message Passing.
- RPC.

Mekanisme tersebut dapat membantu pengaturan urutan komunikasi, tetapi tidak semuanya secara otomatis menjamin urutan global pada sistem terdistribusi. Pengaturan ordering tetap bergantung pada implementasi dan kebutuhan sistem.

**c. Security**

Security merupakan aspek yang berkaitan dengan perlindungan informasi selama komunikasi antarproses berlangsung.
Data yang dikirimkan melalui jaringan berpotensi diakses atau dimanipulasi oleh pihak yang tidak memiliki izin.
Solusi yang disebutkan dalam materi:

- **Encryption:** melindungi isi informasi agar tidak mudah dibaca oleh pihak yang tidak berwenang.
- **Authentication:** memastikan identitas pihak yang melakukan komunikasi.

**d. Performance**

Performance berkaitan dengan kemampuan komunikasi dalam memberikan layanan secara cepat dan efisien.
Dua faktor penting yang dibahas adalah:

- **Latency:** waktu yang dibutuhkan untuk mengirimkan data atau memperoleh respons.
- **Bandwidth:** kapasitas jaringan dalam mentransfer data.

Latensi yang tinggi dapat membuat aplikasi terasa lambat meskipun bandwidth jaringan cukup besar. Sebaliknya, bandwidth yang terbatas dapat menghambat pengiriman data dalam jumlah besar.

### 13. Protokol Komunikasi

Protokol komunikasi merupakan aturan yang mengatur bagaimana perangkat atau aplikasi saling bertukar informasi melalui jaringan.
Materi membahas beberapa protokol utama, yaitu TCP, UDP, dan HTTP.

**a. TCP (Transmission Control Protocol)**

TCP merupakan protokol transport yang menyediakan komunikasi berorientasi koneksi.
TCP memastikan data diterima secara berurutan dan menyediakan mekanisme untuk menangani kehilangan data melalui pengiriman ulang.
TCP sesuai untuk komunikasi yang membutuhkan keandalan, seperti pengiriman data aplikasi, akses layanan web melalui HTTP/2, dan komunikasi client-server.

**b. UDP (User Datagram Protocol)**

UDP merupakan protokol transport yang mengirimkan data dalam bentuk datagram tanpa membangun koneksi seperti TCP.
UDP tidak menyediakan jaminan pengiriman dan pengurutan data seperti TCP. Oleh karena itu, aplikasi yang menggunakan UDP perlu mengatur kebutuhan keandalan sendiri apabila diperlukan.
UDP dapat digunakan pada aplikasi real-time yang lebih mengutamakan kecepatan dan toleransi terhadap kehilangan sebagian paket, seperti komunikasi suara dan video.

**c. HTTP (Hypertext Transfer Protocol)**

HTTP merupakan protokol pada lapisan aplikasi yang digunakan untuk pertukaran informasi antara client dan server.
HTTP banyak digunakan dalam komunikasi layanan web dan API.
Materi juga memperkenalkan beberapa teknologi komunikasi yang berjalan di atas HTTP:

- **gRPC:** pendekatan RPC untuk komunikasi antar layanan.
- **GraphQL:** pendekatan API yang memungkinkan client menentukan data yang dibutuhkan melalui query.
- **REST:** gaya arsitektur untuk membangun layanan web dengan prinsip komunikasi berbasis resource.

Ketiganya memiliki pendekatan yang berbeda. gRPC berfokus pada pemanggilan layanan, GraphQL berfokus pada permintaan data melalui query, sedangkan REST mengatur interaksi dengan resource melalui antarmuka API.

**[MODIFIKASI] Perkembangan HTTP/2 dan HTTP/3**

Ilustrasi pada materi memperlihatkan perbedaan susunan protokol HTTP/2 dan HTTP/3.

- HTTP/2 umumnya berjalan di atas TCP dan menggunakan TLS untuk koneksi HTTPS.
- HTTP/3 menggunakan QUIC yang berjalan di atas UDP serta mengintegrasikan mekanisme keamanan TLS.

Perubahan tersebut menunjukkan bahwa perkembangan protokol komunikasi tidak hanya berfokus pada pertukaran data, tetapi juga pada peningkatan efisiensi dan performa komunikasi jaringan.

### 14. Konsep Sinkronisasi Clock

Dalam sistem terdistribusi, setiap node mempunyai clock atau jam lokal masing-masing.
Permasalahan muncul karena jam pada setiap komputer tidak selalu menunjukkan waktu yang sama. Perbedaan tersebut dapat disebabkan oleh karakteristik perangkat keras, pergeseran clock, dan keterlambatan komunikasi jaringan.
Sinkronisasi clock merupakan proses menyelaraskan waktu pada beberapa komputer agar memiliki acuan waktu yang lebih konsisten.

**Mengapa sinkronisasi clock dibutuhkan?**

1. Membantu menentukan waktu terjadinya suatu peristiwa.
2. Mempermudah pengurutan aktivitas yang dicatat oleh beberapa server.
3. Mendukung konsistensi pencatatan data.
4. Membantu koordinasi proses yang berjalan pada node berbeda.

**Metode sinkronisasi waktu**

Materi menjelaskan beberapa sumber dan mekanisme sinkronisasi:

- **Atomic Clock:** digunakan sebagai sumber waktu yang memiliki tingkat ketelitian tinggi.
- **TAI (International Atomic Time):** standar waktu atomik internasional.
- **GPS (Global Positioning System):** dapat digunakan sebagai sumber acuan waktu.
- **UTC (Coordinated Universal Time):** standar waktu yang digunakan secara internasional.
- **NTP (Network Time Protocol):** protokol untuk menyinkronkan waktu perangkat melalui jaringan.
- **PTP (Precision Time Protocol):** protokol sinkronisasi waktu dengan presisi yang lebih tinggi dibandingkan NTP pada lingkungan yang mendukungnya.

**[MODIFIKASI]**

Sinkronisasi clock sangat penting untuk pencatatan aktivitas, tetapi waktu pada jam fisik tidak selalu dapat digunakan sebagai satu-satunya dasar untuk menentukan urutan kejadian.
Sebagai contoh, dua server dapat mencatat transaksi dengan timestamp yang berbeda karena perbedaan clock lokal. Akibatnya, urutan waktu yang tercatat belum tentu menggambarkan hubungan sebab-akibat sebenarnya.
Untuk mengatasi keterbatasan tersebut, sistem terdistribusi juga menggunakan pendekatan Logical Clock.

### 15. Logical Clock dan Lamport Logical Clock

Logical Clock merupakan pendekatan untuk menentukan urutan kejadian dalam sistem terdistribusi tanpa harus bergantung sepenuhnya pada waktu nyata dari jam fisik.
Salah satu pendekatan yang dijelaskan dalam materi adalah Lamport Logical Clock, yang diperkenalkan oleh Leslie Lamport.
Berbeda dengan jam biasa yang menunjukkan waktu seperti pukul 12.00.01, Logical Clock menggunakan nilai angka untuk menggambarkan urutan kejadian.

**Aturan Lamport Logical Clock**

Terdapat tiga aturan dasar:

1. Setiap terjadi suatu kejadian, nilai Logical Clock bertambah satu.
2. Ketika proses mengirimkan pesan, nilai Logical Clock disertakan bersama pesan tersebut.
3. Ketika menerima pesan, proses membandingkan nilai clock lokal dengan nilai clock yang diterima. Nilai terbesar diambil, kemudian ditambah satu.

Secara sederhana, pembaruan clock ketika menerima pesan dapat ditulis sebagai:

`C = max(C_lokal, C_pesan) + 1`

Keterangan:

- `C` merupakan nilai Logical Clock setelah menerima pesan.
- `C_lokal` merupakan nilai clock sebelum pesan diterima.
- `C_pesan` merupakan nilai clock yang dibawa oleh pesan.

**Contoh Kasus: Proses Transaksi Penjualan**

Materi memberikan contoh tiga layanan, yaitu Sales Service, Product Service, dan Invoice Service.
Urutan kejadian sebenarnya:

1. Pukul 12:00:01, transaksi penjualan terjadi dan dicatat oleh Sales Service.
2. Pukul 12:00:02, Product Service menerima informasi transaksi dan memperbarui jumlah produk terjual.
3. Pukul 12:00:03, Invoice Service membuat faktur berdasarkan transaksi tersebut.

Jika hanya mengandalkan real clock timestamp, keterlambatan jaringan, perbedaan jam komputer, atau masalah perangkat keras dapat menyebabkan urutan pencatatan terlihat tidak sesuai.
Untuk mengatasi hal tersebut, digunakan Lamport Logical Clock.

**Simulasi Logical Clock:**

Awalnya ketiga layanan memiliki nilai Logical Clock sebesar 0.

| Tahap | Proses | Clock Lokal Sebelum | Clock dari Pesan | Clock Setelah |
|---|---|---:|---:|---:|
| 1 | Sales Service mencatat transaksi | 0 | - | 1 |
| 2 | Product Service menerima pesan | 0 | 1 | 2 |
| 3 | Invoice Service menerima pesan | 0 | 2 | 3 |

Penjelasan:

- Sales Service mencatat transaksi dan menaikkan clock menjadi 1. Nilai tersebut dikirimkan kepada Product Service.
- Product Service menerima pesan dengan nilai 1. Karena clock lokalnya masih 0, sistem mengambil nilai terbesar, kemudian menambahkannya menjadi 2.
- Product Service mengirimkan pesan dengan nilai 2 kepada Invoice Service.
- Invoice Service menerima pesan tersebut dan memperbarui clock dari 0 menjadi 3.

Hasilnya menunjukkan urutan logis kejadian:

`Sales Service (1) → Product Service (2) → Invoice Service (3)`

**[MODIFIKASI] Kelebihan dan keterbatasan Lamport Logical Clock**

Kelebihan:

- Tidak bergantung pada kesamaan jam fisik setiap node.
- Membantu menentukan urutan kejadian yang memiliki hubungan sebab-akibat.
- Relatif sederhana untuk diterapkan dalam sistem terdistribusi.
- Dapat membantu pencatatan aktivitas dan analisis urutan komunikasi.

Keterbatasan:

- Nilai clock yang lebih kecil tidak selalu berarti kejadian tersebut benar-benar terjadi lebih dahulu dalam waktu nyata.
- Lamport Clock tidak selalu dapat mengetahui apakah dua kejadian saling berhubungan atau berjalan secara independen.
- Jika dibutuhkan informasi hubungan sebab-akibat yang lebih lengkap, diperlukan pendekatan lain seperti Vector Clock.

**Pengembangan Logical Clock**

Materi juga menyebutkan beberapa pengembangan setelah pendekatan Scalar Clock dari Lamport:

1. Vector Clocks — Colin Fidge dan Friedemann Mattern (1988).
2. Plausible Clocks — Torres-Rojas dan Ahamad (1999).
3. Chain Clocks — Agarwal dan Garg (2005).
4. Interval Tree Clocks — Almeida dan rekan-rekan (2008).
5. Blum Clocks — Lum Ramabaja (2019).

Pengembangan tersebut menunjukkan bahwa penentuan urutan kejadian dalam sistem terdistribusi merupakan persoalan penting yang terus diteliti.

### 16. Koordinasi Proses (Process Coordination)

Koordinasi proses merupakan mekanisme yang memungkinkan beberapa proses independen pada komputer berbeda bekerja sama untuk mencapai tujuan yang sama.
Koordinasi diperlukan karena setiap proses dapat berjalan secara mandiri, tetapi tetap membutuhkan pengaturan komunikasi, sinkronisasi, dan akses terhadap sumber daya.
Tanpa koordinasi yang baik, beberapa proses dapat mengalami konflik, seperti:

- **Race Condition:** kondisi ketika hasil program bergantung pada urutan atau waktu eksekusi beberapa proses yang mengakses sumber daya yang sama.
- **Deadlock:** kondisi ketika dua proses atau lebih saling menunggu sumber daya yang sedang dikuasai proses lainnya sehingga tidak dapat melanjutkan pekerjaan.

**[MODIFIKASI]**

Sebagai contoh, dua layanan pada sistem transaksi mencoba memperbarui data stok barang secara bersamaan. Jika akses data tidak dikelola dengan benar, hasil pembaruan dapat menjadi tidak konsisten.
Koordinasi dibutuhkan agar setiap proses memperoleh aturan yang jelas ketika berkomunikasi atau mengakses sumber daya.
Materi menyebutkan beberapa teknologi yang dapat digunakan untuk membantu koordinasi:

| Teknologi | Keterangan |
|---|---|
| Apache ZooKeeper | Layanan koordinasi untuk aplikasi terdistribusi. |
| etcd | Penyimpanan key-value terdistribusi yang dapat digunakan untuk konfigurasi dan koordinasi. |
| Consul | Sistem untuk service discovery dan pengelolaan konfigurasi layanan. |
| ClickHouse Keeper | Komponen koordinasi yang digunakan dalam ekosistem ClickHouse. |
| Oxia | Sistem penyimpanan terdistribusi yang mendukung kebutuhan koordinasi dan pengelolaan data. |
| KRaft | Mekanisme pengelolaan metadata dan konsensus pada Apache Kafka tanpa ZooKeeper. |

Teknologi tersebut mempunyai karakteristik berbeda, tetapi sama-sama berkaitan dengan kebutuhan pengelolaan sistem yang terdiri dari beberapa komponen.

### 17. Tantangan dan Solusi pada Sistem Terdistribusi

Sistem terdistribusi menghadapi berbagai tantangan karena proses berjalan pada node yang berbeda dan berkomunikasi melalui jaringan.
Materi merangkum empat tantangan utama beserta solusinya.

**a. Message Loss**

Message loss merupakan kondisi ketika pesan yang dikirimkan tidak berhasil sampai ke penerima.
Penyebabnya dapat berupa gangguan jaringan, kehilangan paket, atau kegagalan perangkat.

Solusi:

- Retransmission untuk mengirimkan ulang pesan.
- Acknowledgement untuk memastikan penerimaan pesan.

**b. Deadlock**

Deadlock terjadi ketika beberapa proses saling menunggu sumber daya sehingga tidak ada proses yang dapat melanjutkan eksekusinya.
Solusi:

- Timeout untuk membatasi waktu menunggu.
- Detection Algorithm untuk mendeteksi kondisi deadlock.

**c. Data Inconsistency**

Data inconsistency terjadi ketika beberapa node memiliki keadaan data yang berbeda sehingga sistem tidak mempunyai kondisi data yang konsisten.
Solusi yang disebutkan dalam materi adalah penggunaan consensus protocol, seperti:

- Raft.
- Paxos.

Consensus protocol membantu beberapa node mencapai kesepakatan mengenai suatu nilai atau urutan perubahan data.

**d. Security**

Keamanan menjadi penting karena komunikasi berlangsung melalui jaringan yang berpotensi diakses oleh pihak tidak berwenang.
Solusi yang disebutkan:

- **SSL/TLS:** melindungi komunikasi melalui mekanisme keamanan dan enkripsi.
- **OAuth2:** kerangka otorisasi yang memungkinkan aplikasi memperoleh akses terbatas terhadap sumber daya sesuai izin yang diberikan.

Penerapan solusi tersebut harus disesuaikan dengan jenis ancaman dan kebutuhan keamanan sistem.

### 18. Current Issues pada Sistem Terdistribusi

Materi juga membahas beberapa perkembangan dan isu yang saat ini berkaitan dengan sistem terdistribusi.

**a. Edge and Fog Computing**
Edge Computing merupakan pendekatan pemrosesan data yang dilakukan lebih dekat dengan sumber data atau perangkat yang menghasilkannya.
Tujuannya adalah mengurangi ketergantungan pada pusat data yang lokasinya jauh sehingga beberapa pemrosesan dapat dilakukan dengan latensi lebih rendah.
Fog Computing merupakan pendekatan yang memperluas kemampuan komputasi dan penyimpanan di antara perangkat edge dan cloud.
Contohnya, kamera pengawas dapat melakukan analisis awal terhadap rekaman video di dekat lokasi kamera sebelum mengirimkan informasi yang diperlukan ke server pusat.

**b. Observability dan Tracing**

Observability merupakan kemampuan untuk memahami kondisi internal suatu sistem berdasarkan informasi yang dihasilkan ketika sistem berjalan.
Dalam sistem terdistribusi, observability penting karena satu permintaan pengguna dapat melewati beberapa layanan yang berbeda.
Salah satu pendekatan yang digunakan adalah telemetry, yaitu pengumpulan informasi mengenai aktivitas dan kondisi sistem.
Informasi yang dapat diamati meliputi:

- Logs: catatan aktivitas sistem.
- Metrics: data pengukuran seperti penggunaan CPU, memori, dan waktu respons.
- Traces: rekaman perjalanan suatu permintaan ketika melewati beberapa layanan.

Tracing membantu pengembang mengetahui bagian layanan mana yang menyebabkan keterlambatan atau kegagalan proses.

**c. Container Orchestration**

Container orchestration merupakan proses pengelolaan container secara otomatis, termasuk pengaturan deployment, scaling, jaringan, dan pemulihan ketika container mengalami kegagalan.
Materi menyebutkan dua teknologi:

- **Kubernetes:** platform untuk mengelola dan mengorkestrasi container.
- **Docker Swarm:** teknologi orkestrasi container yang terintegrasi dengan ekosistem Docker.

Sebagai contoh, aplikasi microservices dapat memiliki banyak container yang menjalankan layanan berbeda. Container orchestration membantu mengelola layanan tersebut agar dapat berjalan secara teratur.

---

## D. CONTOH PENERAPAN DAN ANALISIS

### 1. Contoh Penerapan

**Studi Kasus: Sistem Pemesanan pada Aplikasi Transportasi Online**
Sistem transportasi online seperti Gojek atau Grab dapat digunakan sebagai contoh penerapan komunikasi antarproses dalam sistem terdistribusi.
Ketika pengguna memesan kendaraan, beberapa layanan harus bekerja sama untuk menyelesaikan permintaan tersebut.
Gambaran prosesnya:

1. **User Interface:** menerima permintaan perjalanan dari pengguna.
2. **Order Service:** memproses informasi pemesanan.
3. **Location Service:** memperoleh dan mengelola informasi lokasi pengguna serta pengemudi.
4. **Driver Service:** membantu pencarian dan pengelolaan informasi pengemudi.
5. **Pricing Service:** melakukan perhitungan biaya perjalanan.
6. **Notification Service:** mengirimkan pemberitahuan mengenai status pemesanan.

Setiap layanan dapat dijalankan pada node yang berbeda. Agar dapat bekerja sama, layanan tersebut harus melakukan komunikasi melalui jaringan.
Misalnya, ketika pengguna membuat pesanan, Order Service membutuhkan informasi lokasi untuk menentukan pengemudi yang sesuai. Setelah pengemudi ditemukan, sistem dapat memperbarui status pesanan dan mengirimkan pemberitahuan kepada pengguna.
Dalam penerapannya, komunikasi antarlayanan dapat menggunakan RPC untuk permintaan yang membutuhkan respons langsung, serta Message-Oriented Middleware untuk pekerjaan yang dapat diproses secara asinkron.
Contoh lainnya adalah penggunaan Logical Clock atau mekanisme pengurutan kejadian untuk membantu memahami urutan perubahan status pesanan yang tercatat pada beberapa layanan.

### 2. Analisis

Berdasarkan studi kasus tersebut, dapat diketahui bahwa komunikasi antarproses merupakan bagian yang tidak terpisahkan dari sistem terdistribusi.
Sebuah aplikasi tidak harus dibangun sebagai satu program besar yang menjalankan seluruh pekerjaan dalam satu tempat. Tugas dapat dibagi menjadi beberapa layanan yang mempunyai fungsi masing-masing. Namun, pembagian tersebut juga menimbulkan kebutuhan komunikasi dan koordinasi yang lebih kompleks.
Beberapa hal yang dapat dianalisis adalah sebagai berikut.

**a. Pentingnya Pemilihan Model Komunikasi**

Tidak semua layanan membutuhkan pola komunikasi yang sama.
Permintaan yang membutuhkan hasil langsung, seperti pemeriksaan ketersediaan pengemudi, dapat menggunakan komunikasi sinkron. Sementara itu, pengiriman notifikasi atau pencatatan aktivitas dapat dilakukan secara asinkron.
Pemilihan model komunikasi yang tepat membantu sistem bekerja lebih efisien dan mengurangi ketergantungan antarlayanan.

**b. Keandalan Komunikasi**

Ketika suatu layanan mengalami gangguan, layanan lain yang bergantung padanya dapat ikut terdampak.
Sebagai contoh, jika layanan lokasi tidak memberikan respons, proses pencarian pengemudi dapat terhambat.
Penggunaan timeout, acknowledgement, retransmission, serta mekanisme penanganan kegagalan dapat membantu mengurangi dampak gangguan tersebut.

**c. Konsistensi dan Urutan Data**

Sistem yang melibatkan banyak layanan harus memastikan bahwa perubahan data diproses dengan benar.
Misalnya, perubahan status pesanan dari menunggu pengemudi menjadi perjalanan berlangsung harus tercatat secara tepat.
Logical Clock dapat membantu memahami urutan kejadian yang memiliki hubungan sebab-akibat, sedangkan consensus protocol dapat digunakan dalam sistem yang membutuhkan kesepakatan antar-node terhadap perubahan data.

**d. Keamanan Komunikasi**

Karena data pengguna dan informasi perjalanan dipertukarkan melalui jaringan, sistem perlu melindungi komunikasi dari akses yang tidak sah.
Penggunaan TLS dapat membantu melindungi data selama proses pengiriman, sedangkan mekanisme autentikasi dan otorisasi membantu memastikan hanya pihak yang memiliki izin yang dapat mengakses layanan tertentu.

**e. Monitoring dan Observability**

Semakin banyak layanan yang digunakan, semakin sulit pula menemukan penyebab suatu masalah jika tidak tersedia pemantauan yang baik.
Penggunaan logs, metrics, dan distributed tracing membantu pengembang mengikuti perjalanan suatu permintaan dari satu layanan ke layanan lainnya.
Dengan demikian, masalah dapat ditelusuri tanpa harus memeriksa setiap layanan secara terpisah secara manual.

**Kesimpulan Analisis**

Sistem terdistribusi memberikan fleksibilitas dalam membangun aplikasi yang terdiri dari banyak layanan. Akan tetapi, fleksibilitas tersebut harus didukung oleh komunikasi, sinkronisasi, keamanan, dan koordinasi yang baik.
Keberhasilan sistem tidak hanya ditentukan oleh kemampuan setiap layanan menjalankan tugasnya, tetapi juga oleh kemampuan seluruh layanan bekerja sama secara konsisten meskipun berada pada komputer dan lingkungan yang berbeda.

---

## E. PENGGUNAAN ARTIFICIAL INTELLIGENCE (AI)

### 1. AI yang Digunakan

- **Nama AI:** ChatGPT (GPT-6).
- **Tujuan penggunaan:** Membantu memahami, menganalisis, menyusun, dan mengembangkan rangkuman materi perkuliahan.
- **Sumber utama:** Materi perkuliahan yang diberikan oleh dosen dalam bentuk PDF.
- **Bentuk bantuan:** Pengembangan penjelasan teori, penyusunan contoh penerapan, analisis konsep, serta perapian struktur Markdown.

### 2. Prompt yang Digunakan

Berikut prompt inti yang digunakan dalam penyusunan rangkuman ini:

> Kamu berperan sebagai mahasiswa S1 Informatika yang memahami mata kuliah Teori Sistem Terdistribusi dan Terdesentralisasi. Baca dan analisis seluruh halaman file PDF materi perkuliahan yang diberikan. Identifikasi tujuan pembelajaran, seluruh pokok bahasan, istilah teknis, konsep, mekanisme kerja, diagram, contoh, dan kesimpulan materi.
>
> Susun hasilnya dalam format README.md dengan struktur A sampai G sesuai template yang diberikan. Jangan hanya mengambil poin-poin dari materi atau melakukan parafrasa. Kembangkan teori, jelaskan mekanisme kerja, berikan contoh penerapan yang relevan dengan bidang Informatika, serta tambahkan analisis mengenai manfaat, keterbatasan, dan hubungan antarkonsep.
>
> Gunakan bahasa Indonesia yang natural seperti laporan mahasiswa S1 Informatika, formal tetapi mudah dipahami. Pertahankan istilah teknis dan makna materi asli. Jangan mengarang informasi atau referensi. B
>
> Pastikan seluruh materi tercakup, struktur README lengkap, dan hasil akhir siap dimasukkan ke repository GitHub.

### 3. Bagian yang Disesuaikan dari Keluaran AI

Bagian dari hasil rangkuman yang mengalami pengembangan atau penyesuaian meliputi:

1. **Konsep Proses dan Manajemen Proses:** Penjelasan diperluas dengan menguraikan fungsi process creation, process migration, process monitoring, serta hubungannya dengan pengelolaan sumber daya komputer.
2. **Inter-Process Communication (IPC):** Penjelasan dikembangkan dengan membandingkan Shared Memory, Message Passing, RPC, dan Middleware serta alasan Shared Memory tidak cocok untuk komunikasi langsung antar-node.
3. **Message Passing, RPC, dan MOM:** Ditambahkan uraian mengenai mekanisme komunikasi, peran setiap komponen, serta contoh penerapan pada aplikasi dan layanan terdistribusi.
4. **Komunikasi Sinkron dan Asinkron:** Penjelasan dilengkapi dengan alur kerja, perbandingan karakteristik, kelebihan, dan tantangan masing-masing pendekatan.
5. **Protokol Komunikasi:** Pembahasan diperjelas dengan membedakan fungsi TCP, UDP, HTTP, gRPC, GraphQL, dan REST.
6. **Logical Clock:** Contoh Sales Service, Product Service, dan Invoice Service dijabarkan secara bertahap menggunakan tabel agar mekanisme Lamport Logical Clock lebih mudah dipahami.
7. **Koordinasi dan Tantangan Sistem Terdistribusi:** Ditambahkan penjelasan mengenai race condition, deadlock, message loss, data inconsistency, serta hubungan solusi dengan kebutuhan sistem.
8. **Current Issues:** Pembahasan Edge Computing, Fog Computing, Observability, Tracing, dan Container Orchestration dikembangkan dengan contoh penerapan yang relevan.

### 4. Penanda Hasil Modifikasi

Bagian yang mengalami pengembangan atau penyesuaian dari hasil awal AI diberikan tanda **[MODIFIKASI]** pada bagian terkait dalam rangkuman.

Keterangan:

- **[MODIFIKASI]**: Bagian yang mengalami pengembangan, penambahan penjelasan, perbaikan, atau penyesuaian.
- Bagian tanpa tanda: Bagian yang dipertahankan karena sudah sesuai dengan materi dan tidak memerlukan perubahan substantif.

---

## F. KESIMPULAN

Berdasarkan materi pertemuan kedua, dapat dipahami bahwa proses dan komunikasi antarproses merupakan komponen penting dalam membangun sistem terdistribusi. Setiap komputer atau node dapat menjalankan proses secara independen, tetapi tetap membutuhkan mekanisme komunikasi agar seluruh bagian sistem dapat bekerja sama untuk mencapai tujuan yang sama.

IPC menjadi dasar pertukaran informasi antarproses melalui beberapa pendekatan, seperti Message Passing, RPC, dan Middleware. Setiap pendekatan memiliki karakteristik dan kegunaan masing-masing. Pemilihannya harus disesuaikan dengan kebutuhan aplikasi, terutama dalam hal kecepatan komunikasi, ketergantungan antarlayanan, dan pengelolaan pesan.

Selain komunikasi, sistem terdistribusi juga membutuhkan sinkronisasi dan koordinasi yang baik. Perbedaan waktu pada setiap node dapat menyebabkan kesulitan dalam menentukan urutan kejadian. Lamport Logical Clock menjadi salah satu solusi untuk menentukan urutan logis berdasarkan hubungan komunikasi antarproses tanpa harus bergantung sepenuhnya pada jam fisik.

Materi ini juga menunjukkan bahwa sistem terdistribusi menghadapi berbagai tantangan, seperti kehilangan pesan, deadlock, ketidakkonsistenan data, dan masalah keamanan. Oleh karena itu, diperlukan mekanisme seperti acknowledgement, retransmission, timeout, consensus protocol, TLS, serta monitoring dan tracing.

Menurut pemahaman saya, hal terpenting dari materi ini adalah bahwa membangun sistem terdistribusi bukan sekadar membagi aplikasi menjadi beberapa komputer atau layanan. Setiap komponen harus mampu berkomunikasi, menjaga urutan proses, menangani kegagalan, dan berkoordinasi dengan benar. Konsep tersebut menjadi dasar penting dalam memahami teknologi seperti microservices, cloud computing, database terdistribusi, dan aplikasi digital yang melibatkan banyak layanan.

---

## G. DAFTAR REFERENSI

1. Dr. Bambang Purnomosidi D. P. (Tanpa tahun). *Proses dan Komunikasi Antar Proses pada Sistem Terdistribusi*. Materi Perkuliahan Teori Sistem Terdistribusi dan Terdesentralisasi, Fakultas Teknologi Informasi, Universitas Teknologi Digital Indonesia (UTDI).

2. Lamport, L. (1978). *Time, Clocks, and the Ordering of Events in a Distributed System*. Communications of the ACM, 21(7), 558–565.

3. MPI Forum. *Message Passing Interface (MPI) Standard*. https://www.mpi-forum.org/

4. gRPC. *Introduction to gRPC*. https://grpc.io/docs/what-is-grpc/introduction/

---

**Dokumentasi Tugas**

- Repository: [disdec-teori](https://github.com/hendfirmsh/disdec-teori)
- Direktori: `02/`
- File: `README.md`

---