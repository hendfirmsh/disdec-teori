# RANGKUMAN MATERI TEORI SISTEM TERDISTRIBUSI DAN TERDESENTRALISASI

## PERTEMUAN 06

---

## A. IDENTITAS MATERI

| Keterangan | Informasi |
|---|---|
| Mata Kuliah | Teori Sistem Terdistribusi dan Terdesentralisasi |
| Pertemuan | Pertemuan ke-6 |
| Topik Materi | Distributed File System |
| Sumber Materi | 06--distributed-filesystem (1).pdf |
| AI yang Digunakan | ChatGPT GPT-6 |
| Format Dokumen | Markdown (.md) |

---

## B. TUJUAN PEMBELAJARAN

Setelah mempelajari materi pertemuan ini, mahasiswa diharapkan mampu:

1. Memahami dan menjelaskan pengertian *file system*.
2. Menyebutkan berbagai jenis *file system*.
3. Menjelaskan cara kerja *file system* secara umum.
4. Memahami dan menjelaskan pengertian *distributed file system* (DFS).
5. Menyebutkan berbagai jenis DFS.
6. Menjelaskan cara kerja DFS secara umum.
7. Melakukan instalasi salah satu DFS sehingga dapat memahami cara kerjanya.
8. Memahami dan menjelaskan *cloud storage* serta hubungannya dengan DFS.
9. Melakukan instalasi salah satu *object storage* sebagai layanan *cloud storage*.

---

## C. RANGKUMAN MATERI

### 1. Pengertian File System

*File system* atau sistem berkas merupakan metode yang digunakan oleh sistem operasi untuk mengelola dan mengatur file pada media penyimpanan, seperti hard disk, USB flash disk, dan SSD.

File system bertugas mengatur bagaimana data disimpan, diberi nama, ditemukan, dan diakses oleh pengguna maupun aplikasi. Setiap sistem operasi dapat menggunakan jenis file system yang berbeda.

Beberapa contoh file system berdasarkan sistem operasi yang disebutkan dalam materi adalah:

- **Linux**: ext4, XFS, btrfs, dan ReiserFS.
- **DOS/Windows**: FAT16, FAT32, dan NTFS.
- **Mac**: APFS (Apple File System).

Dalam sistem operasi, file system dapat diakses melalui *file system driver*. Driver tersebut dikelola oleh kernel dan menyediakan mekanisme *Virtual File System* (VFS) agar aplikasi pada *user space* dapat mengakses file tanpa harus mengetahui detail implementasi setiap jenis file system.

Alur akses file secara umum berdasarkan materi adalah:

`Aplikasi → System Call Interface → Virtual File System → Driver Kernel → Hardware (Media Penyimpanan)`

Penjelasan alur tersebut:

1. **Aplikasi** mengajukan permintaan untuk membaca, menulis, atau mengelola file.
2. **System Call Interface** menjadi penghubung antara aplikasi dan layanan yang disediakan kernel.
3. **Virtual File System (VFS)** menyediakan antarmuka umum sehingga aplikasi dapat mengakses berbagai jenis file system dengan cara yang seragam.
4. **Driver Kernel** menerjemahkan operasi sesuai dengan jenis file system yang digunakan.
5. **Hardware** merupakan media penyimpanan tempat data disimpan secara fisik.

**[MODIFIKASI]** VFS membuat aplikasi tidak perlu memahami secara langsung apakah media penyimpanan menggunakan ext4, NTFS, atau jenis file system lainnya. Aplikasi cukup menggunakan antarmuka yang disediakan sistem operasi, sedangkan kernel menangani proses akses ke media penyimpanan.

Materi juga menjelaskan bahwa *file system* berbeda dengan hierarki file system. File system berkaitan dengan metode pengelolaan file pada media penyimpanan, sedangkan hierarki file system merupakan susunan file dan direktori dalam sistem operasi. Pengguna umumnya melihat susunan direktori tersebut tanpa harus mengetahui jenis file system yang digunakan.

### 2. Pengertian Distributed File System (DFS)

*Distributed File System* atau DFS merupakan sistem file yang mengelola sekumpulan media penyimpanan yang tersebar pada beberapa node atau mesin, tetapi dari sisi pengguna terlihat sebagai satu sistem penyimpanan yang terintegrasi.

DFS bukan sekadar file system yang dipasang pada lebih dari satu komputer. Secara konseptual, DFS merupakan abstraksi terkoordinasi dari berbagai media penyimpanan yang mampu menangani perbedaan perangkat, kegagalan, dan akses secara bersamaan (*concurrency*).

Tujuannya adalah menghasilkan jaringan penyimpanan yang terintegrasi, andal, dan memiliki kinerja yang baik.

Dalam DFS, data dapat disimpan pada beberapa media penyimpanan atau node yang berbeda. Namun, pengguna tidak harus mengetahui lokasi fisik setiap data karena sistem menyajikannya sebagai satu media penyimpanan secara konseptual.

**[MODIFIKASI]** Sebagai gambaran, sebuah organisasi memiliki beberapa server penyimpanan yang berada di lokasi berbeda. Dengan DFS, pengguna dapat mengakses file melalui satu sistem penyimpanan yang terintegrasi tanpa harus membuka setiap server secara terpisah. Pengelolaan lokasi data dilakukan oleh sistem DFS.

### 3. Perbedaan DAS, DFS, NAS, dan SAN

Dalam materi, terdapat pembahasan mengenai perbedaan *Direct-Attached Storage* (DAS), DFS, *Network-Attached Storage* (NAS), dan *Storage Area Network* (SAN).

Materi secara khusus menjelaskan bahwa DFS merupakan abstraksi pada tingkat perangkat lunak yang mengelola data dalam bentuk file dan direktori. Data tersebut dapat didistribusikan ke banyak node.

Sementara itu, SAN menyajikan penyimpanan sebagai kumpulan perangkat penyimpanan pada tingkat blok (*block-level devices*) yang dapat dihubungkan langsung oleh server dan diformat menggunakan file system masing-masing.

Perbandingan konsep secara umum:

| Jenis Penyimpanan | Karakteristik |
|---|---|
| DAS (Direct-Attached Storage) | Media penyimpanan terhubung langsung ke komputer atau server yang menggunakannya. |
| DFS (Distributed File System) | Mengelola file dan direktori yang tersebar pada beberapa node, tetapi menyajikannya sebagai sistem penyimpanan terintegrasi. |
| NAS (Network-Attached Storage) | Menyediakan akses penyimpanan berbasis file melalui jaringan kepada perangkat lain. |
| SAN (Storage Area Network) | Menyediakan penyimpanan pada tingkat blok melalui jaringan khusus penyimpanan. |

**[MODIFIKASI]** Perbedaan utama DFS dan SAN terletak pada tingkat abstraksi yang disediakan. DFS mengelola data dalam bentuk file dan direktori, sedangkan SAN menyediakan perangkat penyimpanan berbasis blok yang dapat digunakan server untuk membangun file system sendiri.

Materi juga menjelaskan bahwa SAN secara konseptual dapat digunakan sebagai media penyimpanan untuk DFS, meskipun penggunaan tersebut tidak disarankan dalam konteks yang dibahas. Penggunaan SAN umumnya meliputi:

- Backend untuk database skala besar.
- Backend untuk proses penyuntingan video dan audio.
- Backend untuk kebutuhan virtualisasi skala besar.

DFS lebih mengarah pada penggunaan DAS di setiap node yang menjadi bagian dari sistem terdistribusi.

### 4. Berbagai Distributed File System yang Umum

Terdapat beberapa teknologi DFS yang disebutkan dalam materi perkuliahan, yaitu:

1. **Google File System (GFS)**: Sistem file terdistribusi yang dikembangkan untuk mendukung penyimpanan dan pengelolaan data dalam infrastruktur Google.
2. **Colossus**: Sistem yang disebut dalam materi sebagai pengganti Google File System dan digunakan pada layanan Google seperti YouTube, Gmail, dan Google Docs.
3. **CephFS**: Sistem file yang merupakan bagian dari ekosistem Ceph.
4. **Gluster**: Teknologi penyimpanan terdistribusi yang menyediakan pengelolaan penyimpanan dalam satu sistem.
5. **HDFS (Hadoop Distributed File System)**: Sistem file terdistribusi yang menjadi bagian utama Apache Hadoop dan digunakan untuk penyimpanan data skala besar.
6. **Lustre**: Salah satu teknologi distributed file system yang digunakan untuk kebutuhan penyimpanan dengan skala besar.

Teknologi-teknologi tersebut memiliki tujuan yang berkaitan, yaitu menyediakan mekanisme penyimpanan data yang dapat dikelola melalui beberapa perangkat atau node.

### 5. Cara Kerja Distributed File System

Secara umum, DFS bekerja dengan mengoordinasikan beberapa media penyimpanan yang berada pada node berbeda agar dapat digunakan sebagai satu sistem penyimpanan.

Ketika pengguna mengakses file, sistem DFS menangani proses pencarian lokasi data dan komunikasi dengan node penyimpanan yang sesuai. Dengan demikian, pengguna tidak harus mengelola setiap perangkat penyimpanan secara terpisah.

DFS juga dirancang untuk menghadapi perbedaan perangkat, kegagalan komponen, dan akses bersamaan. Hal tersebut menjadi bagian penting karena data tidak hanya berada pada satu media penyimpanan.

**[MODIFIKASI]** Sebagai contoh sederhana, apabila sebuah file disimpan pada sistem DFS yang memiliki beberapa node, sistem dapat mengatur lokasi penyimpanan dan proses akses file tersebut. Pengguna tetap berinteraksi dengan sistem penyimpanan yang sama meskipun data secara fisik dikelola oleh beberapa node.

### 6. Studi Kasus: Hadoop Distributed File System (HDFS)

*Hadoop Distributed File System* (HDFS) merupakan file system terdistribusi yang bersifat *open source*, *scalable*, dan *fault-tolerant*. HDFS dirancang untuk mengelola serta menyimpan dataset berukuran besar pada sekumpulan *commodity hardware*.

*Commodity hardware* adalah perangkat keras komputer yang diproduksi secara massal, memiliki harga relatif terjangkau, mudah dipertukarkan, dan tersedia secara luas dari berbagai vendor.

HDFS merupakan salah satu komponen utama Apache Hadoop dan digunakan untuk mendukung pemrosesan data skala besar.

Berdasarkan materi, cara kerja HDFS melibatkan beberapa proses utama:

1. File dibagi menjadi beberapa bagian yang disebut blok (*blocks*).
2. Blok-blok tersebut didistribusikan ke beberapa server dalam sebuah kluster.
3. Data direplikasi agar salinan data tersedia pada beberapa server.
4. Replikasi tersebut digunakan untuk membantu meningkatkan *high availability* dan ketahanan sistem terhadap kegagalan.

**[MODIFIKASI]** Pembagian file menjadi blok memungkinkan penyimpanan data berukuran besar dilakukan pada beberapa server, bukan hanya bergantung pada satu perangkat. Replikasi juga membantu ketika salah satu server mengalami gangguan karena sistem memiliki salinan data pada node lain.

Materi juga menyebutkan informasi versi Apache Hadoop dan Java sebagai berikut:

- Apache Hadoop 3.5.0 dikompilasi dengan JDK 17.
- Untuk server, Hadoop dapat dijalankan menggunakan Java 17.
- Untuk client, Hadoop dapat dijalankan menggunakan Java 17 maupun Java 21.

Untuk memahami cara kerja HDFS secara langsung, dosen mengarahkan mahasiswa melakukan praktik berdasarkan dokumen yang telah disertakan di EL-UTDI.

### 7. Pengertian Cloud Storage

*Cloud storage* merupakan layanan penyimpanan data secara online yang memungkinkan pengguna menyimpan dan mengakses data melalui jaringan internet, tanpa harus menyimpan seluruh data pada hard disk lokal atau perangkat fisik milik pengguna.

Cloud storage menggunakan model penyimpanan data pada lingkungan cloud yang dikelola secara jarak jauh dalam suatu kumpulan penyimpanan secara logis (*logical pool*).

Secara fisik, penyimpanan cloud dapat terdiri dari beberapa server, bahkan berada di lokasi yang berbeda. Infrastruktur tersebut umumnya dimiliki dan dikelola oleh penyedia layanan *cloud computing*.

Beberapa contoh layanan cloud storage yang disebutkan dalam materi adalah:

- **Amazon S3**: Layanan penyimpanan objek dari Amazon Web Services.
- **Azure Blob Storage**: Layanan penyimpanan data berbasis objek dari Microsoft Azure.
- **Google Cloud Storage (GCS)**: Layanan penyimpanan data dari Google Cloud.

**[MODIFIKASI]** Cloud storage memudahkan pengguna dan aplikasi untuk menyimpan data tanpa harus mengelola seluruh infrastruktur penyimpanan fisik secara langsung. Pengguna mengakses layanan melalui jaringan, sedangkan pengelolaan server dan media penyimpanan dilakukan oleh penyedia layanan.

### 8. Hubungan Cloud Storage dengan Distributed File System

Cloud storage dan DFS memiliki hubungan dalam pengelolaan penyimpanan data, tetapi keduanya tidak selalu memiliki fungsi yang sama.

Dalam materi dijelaskan bahwa cloud storage dapat menjadi tempat penyimpanan data, sedangkan pengorganisasian dan operasi file system dapat dilakukan oleh DFS.

Contoh yang diberikan adalah penggunaan Amazon S3 dengan HDFS.

Pada contoh tersebut:

- **Amazon S3** berperan sebagai layanan cloud storage.
- **HDFS** menangani operasi file system.
- Konfigurasi hubungan antara keduanya dapat dilakukan melalui file `core-site.xml`.

Artinya, cloud storage dapat digunakan sebagai media penyimpanan yang diakses oleh sistem seperti Hadoop, sementara operasi file system dikelola melalui konfigurasi yang sesuai.

**[MODIFIKASI]** Hal yang perlu diperhatikan adalah cloud storage dan DFS bukan istilah yang dapat selalu dipertukarkan. Cloud storage menjelaskan model layanan penyimpanan berbasis cloud, sedangkan DFS menjelaskan sistem pengelolaan file yang mengoordinasikan penyimpanan pada beberapa node. Keduanya dapat digunakan bersama sesuai arsitektur yang dibangun.

### 9. Tipe Cloud Storage

Dalam materi perkuliahan, cloud storage dibagi menjadi tiga tipe utama, yaitu:

#### a. Object Storage

*Object storage* merupakan model penyimpanan yang mengelola data sebagai objek. Setiap objek dapat memiliki data, metadata, dan identitas tertentu.

Model ini umum digunakan untuk menyimpan data dalam jumlah besar, seperti gambar, video, dokumen, dan file cadangan.

Contoh layanan yang berkaitan dengan tipe ini adalah Amazon S3.

#### b. File Storage

*File storage* merupakan model penyimpanan yang mengatur data dalam bentuk file dan direktori atau folder.

Model ini memudahkan pengguna dan aplikasi dalam mengelola data menggunakan struktur hierarki seperti file system pada umumnya.

#### c. Block Storage

*Block storage* merupakan model penyimpanan yang membagi data menjadi blok-blok berukuran tertentu. Blok tersebut dapat dikelola oleh sistem operasi atau aplikasi sebagai perangkat penyimpanan.

Model ini sering digunakan sebagai media penyimpanan untuk kebutuhan server, database, dan aplikasi yang membutuhkan akses pada tingkat blok.

**[MODIFIKASI]** Perbedaan ketiga tipe tersebut terletak pada cara data disimpan dan diakses. Object storage menggunakan objek, file storage menggunakan file dan direktori, sedangkan block storage menggunakan blok data. Pemilihan tipe penyimpanan perlu disesuaikan dengan kebutuhan aplikasi.

### 10. Studi Kasus Cloud Storage

Pada bagian akhir materi, terdapat pembahasan studi kasus cloud storage yang mengarah pada **CubeFS**. Materi menyertakan tautan dokumentasi arsitektur CubeFS:

https://cubefs.io/docs/master/overview/architecture.html#architecture

CubeFS menjadi salah satu contoh teknologi yang dapat dipelajari lebih lanjut dalam konteks sistem penyimpanan terdistribusi.

Namun, PDF yang diberikan tidak memuat uraian tekstual yang cukup mengenai komponen, mekanisme kerja, maupun langkah instalasi CubeFS. Oleh karena itu, bagian ini dibatasi pada pengenalan CubeFS sebagai studi kasus yang dirujuk oleh materi, tanpa menambahkan detail implementasi yang belum dibahas dalam bahan perkuliahan.

---

## D. CONTOH PENERAPAN DAN ANALISIS

### 1. Contoh Penerapan

Berikut beberapa contoh penerapan konsep *file system*, DFS, HDFS, dan cloud storage dalam bidang teknologi informasi.

#### a. Pengelolaan File pada Sistem Operasi

Pada komputer yang menggunakan sistem operasi Linux, file system seperti ext4 dapat digunakan untuk mengatur penyimpanan file pada hard disk atau SSD.

Ketika pengguna membuka sebuah file melalui aplikasi, sistem operasi menangani permintaan tersebut melalui mekanisme kernel, VFS, dan driver file system hingga data dapat dibaca dari media penyimpanan.

#### b. Penyimpanan Data Skala Besar Menggunakan HDFS

HDFS dapat digunakan untuk menyimpan dataset berukuran besar pada beberapa server dalam satu kluster.

File dibagi menjadi blok-blok, kemudian blok tersebut didistribusikan ke beberapa server dan direplikasi. Pendekatan ini mendukung penyimpanan data skala besar serta membantu mempertahankan ketersediaan data ketika terjadi kegagalan pada salah satu node.

#### c. Penyimpanan Data pada Cloud Storage

Layanan seperti Amazon S3, Azure Blob Storage, dan Google Cloud Storage dapat digunakan untuk menyimpan data melalui jaringan internet.

Contohnya, aplikasi dapat menyimpan file gambar, dokumen, atau file cadangan pada layanan cloud storage sehingga data dapat diakses melalui jaringan tanpa harus bergantung pada satu perangkat penyimpanan lokal.

#### d. Integrasi HDFS dengan Amazon S3

Sesuai contoh dalam materi, Amazon S3 dapat digunakan sebagai media penyimpanan yang terhubung dengan HDFS melalui konfigurasi pada file `core-site.xml`.

Pendekatan ini menunjukkan bahwa sistem pengelolaan file dan layanan penyimpanan cloud dapat digunakan bersama dalam satu arsitektur.

### 2. Analisis

Berdasarkan materi pertemuan ini, file system merupakan bagian penting dalam sistem operasi karena berfungsi mengatur penyimpanan dan akses data. Tanpa file system, aplikasi akan kesulitan melakukan pengelolaan file secara terstruktur.

Pada sistem yang lebih besar, kebutuhan penyimpanan tidak selalu dapat dipenuhi oleh satu perangkat. Oleh karena itu, DFS digunakan untuk mengoordinasikan beberapa media penyimpanan agar dapat diakses sebagai satu sistem yang terintegrasi.

HDFS menjadi salah satu contoh penerapan DFS untuk pengelolaan data skala besar. Pembagian file menjadi blok dan proses replikasi memungkinkan data disimpan pada beberapa server. Hal ini membantu meningkatkan skalabilitas dan ketersediaan penyimpanan.

Sementara itu, cloud storage memberikan kemudahan dalam menyediakan penyimpanan melalui jaringan tanpa mengharuskan pengguna mengelola seluruh perangkat keras secara langsung. Cloud storage juga dapat diintegrasikan dengan sistem seperti HDFS sesuai kebutuhan arsitektur.

Dari pembahasan tersebut, dapat dipahami bahwa file system, DFS, dan cloud storage memiliki fungsi yang saling berkaitan, tetapi tidak sama. File system mengatur file pada media penyimpanan, DFS mengoordinasikan penyimpanan yang tersebar pada beberapa node, sedangkan cloud storage menyediakan layanan penyimpanan berbasis cloud.

Pemahaman mengenai konsep-konsep tersebut penting bagi mahasiswa Informatika, terutama ketika merancang aplikasi yang membutuhkan penyimpanan data dalam jumlah besar, akses melalui jaringan, skalabilitas, dan ketersediaan data.

---

## E. PENGGUNAAN ARTIFICIAL INTELLIGENCE (AI)

### 1. AI yang Digunakan

- Nama AI: ChatGPT GPT-6.
- Tujuan penggunaan: Membantu memahami, menyusun, dan mengembangkan rangkuman materi perkuliahan.
- Sumber utama: Materi perkuliahan yang diberikan oleh dosen dalam bentuk PDF.
- Bentuk penggunaan: Membantu mengidentifikasi pokok bahasan, menyusun penjelasan, dan mengembangkan contoh penerapan berdasarkan materi.

### 2. Prompt yang Digunakan

Berikut prompt yang digunakan untuk menghasilkan rangkuman awal:

> Saya merupakan mahasiswa S1 Informatika yang sedang mengerjakan tugas rangkuman mata kuliah Teori Sistem Terdistribusi dan Terdesentralisasi pertemuan ke-6. Baca dan pelajari seluruh isi PDF yang saya lampirkan dengan teliti, kemudian buat rangkuman berdasarkan materi tersebut.
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
> Bahas file system, cara kerja file system, distributed file system, perbedaan DAS, DFS, NAS, dan SAN, berbagai contoh DFS, HDFS, cloud storage, hubungan cloud storage dengan DFS, serta tipe-tipe cloud storage.
>
> Sertakan contoh penerapan dan analisis yang relevan dengan bidang Informatika. Jangan mengarang informasi, kode program, hasil pengujian, atau detail implementasi yang tidak tersedia dalam sumber. Jika materi hanya menyebutkan nama teknologi atau mengarahkan ke dokumen praktik yang tidak dilampirkan, jelaskan keterbatasan tersebut.
>
> Buat hasil akhir dalam format Markdown yang siap disimpan sebagai README.md di GitHub. Berikan tanda **[MODIFIKASI]** pada bagian yang mendapatkan pengembangan penjelasan atau tambahan contoh dari hasil awal AI.

### 3. Bagian yang Disesuaikan dari Keluaran AI

Bagian dari hasil AI yang dikembangkan atau disesuaikan meliputi:

1. **File System dan Alur Kerjanya**: Penjelasan mengenai hubungan aplikasi, system call interface, VFS, driver kernel, dan media penyimpanan dikembangkan agar alur akses file lebih mudah dipahami.
2. **Distributed File System**: Penjelasan mengenai abstraksi penyimpanan, distribusi data pada beberapa node, serta perbedaan DFS dengan penyimpanan lainnya dikembangkan untuk memperjelas konsep.
3. **HDFS dan Cloud Storage**: Penjelasan mengenai pembagian file menjadi blok, replikasi data, serta hubungan HDFS dengan layanan cloud storage dikembangkan dengan contoh penerapan.
4. **Tipe Cloud Storage dan Analisis**: Penjelasan mengenai object storage, file storage, dan block storage dikembangkan agar perbedaan cara penyimpanan dan penggunaannya lebih mudah dipahami.

Penyesuaian dilakukan untuk memperjelas pemahaman materi, mengembangkan penjelasan yang masih singkat pada slide, serta menambahkan contoh penerapan yang relevan dengan bidang Informatika.

### 4. Penanda Hasil Modifikasi

Bagian yang mengalami pengembangan atau penyesuaian dari hasil awal AI diberikan tanda **[MODIFIKASI]** pada bagian terkait dalam rangkuman.

Keterangan:

- **[MODIFIKASI]**: Bagian yang mengalami pengembangan, penambahan penjelasan, perbaikan, atau penyesuaian.
- Bagian tanpa tanda: Bagian yang dipertahankan karena sudah sesuai dengan materi dan tidak memerlukan perubahan substantif.

---

## F. KESIMPULAN

Berdasarkan materi pertemuan ke-6, dapat disimpulkan bahwa *file system* merupakan metode yang digunakan sistem operasi untuk mengelola file pada media penyimpanan. File system bekerja melalui beberapa komponen, mulai dari aplikasi, system call interface, Virtual File System, driver kernel, hingga media penyimpanan.

Dalam sistem terdistribusi, kebutuhan penyimpanan dapat melibatkan banyak perangkat atau node. Distributed File System digunakan untuk mengoordinasikan beberapa media penyimpanan tersebut agar dapat diakses sebagai satu sistem yang terintegrasi. Konsep ini membantu mengelola perbedaan perangkat, kegagalan, dan akses secara bersamaan.

HDFS merupakan salah satu contoh penerapan DFS yang dirancang untuk mengelola dataset berukuran besar. HDFS membagi file menjadi blok-blok, mendistribusikannya ke beberapa server, dan melakukan replikasi untuk membantu meningkatkan ketersediaan data.

Selain DFS, cloud storage juga menjadi bagian penting dalam teknologi penyimpanan modern. Cloud storage memungkinkan pengguna menyimpan dan mengakses data melalui jaringan. Terdapat tiga tipe utama cloud storage yang dibahas dalam materi, yaitu object storage, file storage, dan block storage.

Pemahaman mengenai file system, DFS, HDFS, dan cloud storage bermanfaat bagi mahasiswa Informatika dalam merancang serta mengembangkan aplikasi yang membutuhkan penyimpanan data berskala besar, akses jaringan, skalabilitas, dan ketersediaan data.

---

## G. DAFTAR REFERENSI

1. Purnomosidi D. P., Bambang. (Tanpa tahun). *Distributed File System: Materi Perkuliahan Teori Sistem Terdistribusi dan Terdesentralisasi*. Fakultas Teknologi Informasi, Universitas Teknologi Digital Indonesia.
2. Apache Software Foundation. (Tanpa tahun). *HDFS Architecture Guide*. https://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-hdfs/HdfsDesign.html
3. Apache Software Foundation. (Tanpa tahun). *Apache Hadoop*. https://hadoop.apache.org/
4. Amazon Web Services. (Tanpa tahun). *Amazon Simple Storage Service (Amazon S3)*. https://aws.amazon.com/s3/
5. Ceph. (Tanpa tahun). *Ceph*. https://ceph.io/en/
6. Gluster. (Tanpa tahun). *Gluster*. https://www.gluster.org/
7. Lustre. (Tanpa tahun). *Lustre*. https://www.lustre.org/
8. CubeFS. (Tanpa tahun). *CubeFS Architecture*. https://cubefs.io/docs/master/overview/architecture.html#architecture

Catatan: Rangkuman utama disusun berdasarkan PDF materi perkuliahan yang diberikan oleh dosen. Referensi tambahan di atas merupakan dokumentasi atau situs teknologi yang dicantumkan dalam materi.

---

**Dokumentasi Tugas**

- Repository: [disdec-teori](https://github.com/hendfirmsh/disdec-teori)
- Direktori: `06/`
- File: `README.md`

---
