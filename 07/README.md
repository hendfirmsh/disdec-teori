:::writing{variant="document" id="82716"}
# RANGKUMAN MATERI TEORI SISTEM TERDISTRIBUSI DAN TERDESENTRALISASI

## PERTEMUAN 07

---

## A. IDENTITAS MATERI

| Keterangan | Informasi |
|---|---|
| Mata Kuliah | Teori Sistem Terdistribusi dan Terdesentralisasi |
| Pertemuan | Pertemuan ke-7 |
| Topik Materi | Cloud Computing |
| Sumber Materi | 07--cloud-computing.pdf |
| Dosen Pengampu | Dr. Bambang Purnomosidi D. P. |
| AI yang Digunakan | ChatGPT GPT-6 |
| Format Dokumen | Markdown (.md) |

---

## B. TUJUAN PEMBELAJARAN

Setelah mempelajari materi Cloud Computing, mahasiswa diharapkan mampu:

1. Menjelaskan pengertian, sejarah, karakteristik, serta konsep dasar Cloud Computing.
2. Memahami dan membedakan model layanan Cloud Computing, yaitu SaaS, PaaS, dan IaaS, serta model deployment-nya.
3. Menjelaskan arsitektur dan komponen yang membangun layanan Cloud Computing.
4. Memahami konsep scalability dan redundancy serta penerapannya untuk meningkatkan kemampuan dan keandalan sistem.
5. Menjelaskan konsep virtualisasi, Virtual Machine, dan teknologi Container beserta penggunaannya dalam lingkungan cloud.
6. Memahami konsep Serverless Computing dan Cloud Native Application beserta komponen pendukungnya.
7. Memahami penggunaan Docker maupun Podman untuk membangun aplikasi berbasis container.

---

## C. RANGKUMAN MATERI

### 1. Pengertian Cloud Computing

Cloud Computing atau komputasi awan merupakan model penyediaan sumber daya komputasi melalui jaringan internet yang dapat digunakan sesuai kebutuhan. Sumber daya tersebut meliputi server, jaringan, penyimpanan, aplikasi, dan berbagai layanan komputasi lainnya.

Menurut definisi National Institute of Standards and Technology (NIST), Cloud Computing merupakan model yang memungkinkan akses jaringan secara luas, mudah, dan sesuai permintaan terhadap kumpulan sumber daya komputasi yang dapat dikonfigurasi. Sumber daya tersebut dapat disediakan maupun dilepaskan dengan cepat tanpa membutuhkan banyak pengelolaan langsung dari pengguna.

Secara sederhana, Cloud Computing memungkinkan seseorang atau organisasi menggunakan fasilitas komputasi tanpa harus memiliki dan mengelola seluruh perangkat kerasnya sendiri.

**[MODIFIKASI] Cara Kerja Cloud Computing**

Pada penerapannya, Cloud Computing bekerja dengan memanfaatkan infrastruktur server yang dikelola oleh penyedia layanan cloud. Pengguna mengakses sumber daya tersebut melalui jaringan, kemudian menggunakan layanan sesuai kebutuhan.

Sebagai contoh, ketika seseorang menyimpan file menggunakan Google Drive, file tersebut tidak harus disimpan pada perangkat komputer miliknya. Data disimpan pada infrastruktur penyimpanan milik penyedia layanan dan dapat diakses kembali melalui internet menggunakan perangkat yang berbeda.

Secara umum, prosesnya dapat digambarkan sebagai berikut:

1. Pengguna mengakses layanan cloud melalui aplikasi atau browser.
2. Permintaan dikirim melalui jaringan menuju infrastruktur penyedia cloud.
3. Server memproses permintaan sesuai layanan yang digunakan.
4. Hasil pemrosesan atau data dikirim kembali kepada pengguna.

Dengan mekanisme tersebut, pengguna tidak harus mengetahui lokasi fisik server maupun bagaimana infrastruktur penyedia layanan mengelolanya.

**Cloud Computing dan On-Premise**

Dalam materi terdapat istilah On-Premise dan Off-Premise yang berkaitan dengan lokasi pengelolaan infrastruktur.

- **On-Premise:** Infrastruktur komputasi dimiliki dan dikelola langsung oleh organisasi pada lingkungan sendiri.
- **Off-Premise:** Infrastruktur fisik ditempatkan di lokasi penyedia layanan atau fasilitas pihak lain, misalnya melalui layanan colocation.

Perbedaan utamanya terletak pada lokasi dan pihak yang bertanggung jawab terhadap pengelolaan infrastruktur.

Pada sistem On-Premise, organisasi memiliki kontrol lebih besar terhadap perangkat keras dan pengelolaannya, tetapi juga harus menanggung kebutuhan biaya, pemeliharaan, dan pengembangan infrastruktur.

Sementara itu, Cloud Computing memberikan kemudahan karena sebagian besar pengelolaan infrastruktur dilakukan oleh penyedia layanan.

**Sejarah Perkembangan Cloud Computing**

Perkembangan Cloud Computing tidak terjadi secara langsung, melainkan melalui beberapa tahapan perkembangan teknologi komputasi.

| Tahun | Perkembangan |
|---|---|
| 1950-an | Era mainframe dan perkembangan konsep time-sharing system oleh John McCarthy. |
| 1961 | John McCarthy memprediksi komputer dapat digunakan seperti layanan listrik dan air. |
| 1969 | ARPANET menjadi salah satu perkembangan penting dalam komunikasi jaringan komputer. |
| 1990 | World Wide Web diperkenalkan oleh Tim Berners-Lee dan mendukung perkembangan komputasi client-server. |
| 1997 | Prof. Ramnath Chellappa menggunakan istilah Cloud Computing. |
| 1999 | Salesforce.com menjadi salah satu pelopor layanan aplikasi melalui internet. |
| 2002 | Amazon mulai mengembangkan layanan yang berkaitan dengan infrastruktur cloud. |
| 2006 | Amazon EC2 diperkenalkan. |
| 2009 | Google Cloud mulai berkembang sebagai layanan komputasi awan. |

**[MODIFIKASI]** Perkembangan tersebut menunjukkan perubahan cara penggunaan sumber daya komputasi. Pada awalnya, organisasi harus memiliki perangkat komputasi sendiri. Seiring perkembangan jaringan dan teknologi virtualisasi, sumber daya komputasi dapat disediakan secara terpusat dan digunakan oleh banyak pengguna melalui internet.

Beberapa perusahaan penyedia Cloud Computing yang disebutkan dalam materi antara lain:

- AWS (Amazon Web Services).
- Google Cloud.
- Microsoft Azure.
- Alibaba Cloud.
- Oracle Cloud.
- IBM.
- Heroku.
- Biznet Gio.
- Telkom Telstra.
- Lintas Arta.
- DCI Indonesia.

### 2. Karakteristik Cloud Computing

Cloud Computing mempunyai karakteristik khusus yang membedakannya dari penggunaan infrastruktur komputasi secara konvensional.

Menurut materi, terdapat enam karakteristik utama yang perlu dipahami.

**a. On-Demand Self-Service**

On-demand self-service merupakan kemampuan pengguna untuk mendapatkan sumber daya komputasi secara mandiri tanpa harus melakukan komunikasi langsung dengan penyedia layanan.

Contohnya, pengguna dapat membuat server virtual melalui dashboard penyedia cloud hanya dengan beberapa konfigurasi.

**[MODIFIKASI]** Karakteristik ini membuat proses penyediaan infrastruktur menjadi lebih cepat karena pengguna tidak perlu menunggu proses pembelian, pemasangan, dan konfigurasi perangkat keras secara manual.

**b. Broad Network Access**

Broad network access memungkinkan layanan cloud diakses melalui jaringan menggunakan berbagai jenis perangkat.

Pengguna dapat mengakses layanan melalui laptop, smartphone, tablet, maupun komputer lainnya selama memiliki koneksi jaringan yang sesuai.

Contohnya adalah penggunaan Google Drive yang memungkinkan seseorang membuka dokumen dari laptop maupun smartphone.

**c. Resource Pooling**

Resource pooling merupakan mekanisme pengelompokan sumber daya komputasi milik penyedia cloud untuk digunakan oleh banyak pelanggan.

Sumber daya seperti CPU, memori, jaringan, dan penyimpanan dikelola dalam satu kumpulan infrastruktur yang dapat dialokasikan sesuai kebutuhan pengguna.

Konsep ini berkaitan dengan multitenancy karena satu infrastruktur dapat melayani beberapa pelanggan secara bersamaan.

**[MODIFIKASI]** Resource pooling membuat penggunaan perangkat keras menjadi lebih efisien. Penyedia layanan tidak harus menyediakan satu server fisik khusus untuk setiap pengguna apabila kebutuhan komputasinya masih dapat dipenuhi melalui pembagian sumber daya.

**d. Rapid Elasticity**

Rapid elasticity merupakan kemampuan sistem cloud untuk menyesuaikan kapasitas sumber daya secara cepat mengikuti perubahan kebutuhan.

Contohnya, sebuah toko online mengalami peningkatan jumlah pengunjung ketika mengadakan promosi besar. Infrastruktur cloud dapat menambahkan kapasitas komputasi agar aplikasi tetap dapat melayani permintaan pengguna.

Ketika jumlah pengunjung kembali normal, sumber daya tambahan dapat dikurangi.

**e. Measured Service**

Measured service merupakan karakteristik yang memungkinkan penggunaan sumber daya cloud dipantau, diukur, dan dilaporkan secara otomatis.

Penggunaan CPU, penyimpanan, bandwidth, maupun kapasitas lainnya dapat dicatat oleh penyedia layanan.

Karakteristik ini mendukung sistem pembayaran berdasarkan penggunaan atau pay-as-you-go.

Contohnya, perusahaan hanya membayar kapasitas penyimpanan dan komputasi yang digunakan sesuai ketentuan layanan penyedia cloud.

**f. Multitenancy**

Multitenancy merupakan konsep ketika satu instance perangkat lunak atau perangkat keras melayani beberapa pelanggan atau tenant secara bersamaan.

Walaupun menggunakan infrastruktur yang sama, data dan aktivitas setiap pelanggan tetap dipisahkan.

**[MODIFIKASI]** Sebagai contoh, sebuah penyedia layanan cloud dapat menjalankan layanan untuk beberapa perusahaan pada infrastruktur fisik yang sama. Setiap perusahaan memiliki akun, data, dan pengaturan masing-masing sehingga tidak dapat mengakses data milik perusahaan lainnya tanpa izin.

Multitenancy membantu penyedia layanan menggunakan sumber daya secara efisien, tetapi tetap membutuhkan mekanisme keamanan dan isolasi yang baik.

### 3. Model Layanan Cloud Computing

Model layanan Cloud Computing menjelaskan jenis fasilitas yang disediakan oleh penyedia cloud serta bagian yang masih harus dikelola oleh pengguna.

Dalam materi terdapat tiga kelompok utama, yaitu SaaS, PaaS, dan IaaS. Selain itu, terdapat istilah XaaS yang merupakan konsep layanan yang lebih luas.

**a. Software as a Service (SaaS)**

SaaS merupakan model layanan cloud yang menyediakan perangkat lunak siap digunakan oleh pengguna akhir.

Pada model ini, penyedia layanan bertanggung jawab terhadap pengelolaan aplikasi hingga infrastruktur yang mendukungnya.

Pengguna cukup mengakses aplikasi melalui browser atau perangkat lainnya tanpa harus melakukan instalasi dan pengelolaan server secara langsung.

Contoh penerapan:

- Google Docs untuk membuat dan mengedit dokumen.
- Gmail untuk layanan surat elektronik.
- Microsoft 365 untuk produktivitas perkantoran.
- Salesforce untuk pengelolaan hubungan pelanggan.

**[MODIFIKASI]** SaaS cocok digunakan ketika pengguna membutuhkan aplikasi yang dapat langsung digunakan tanpa harus membangun sistem dari awal. Kekurangannya, pengguna memiliki kontrol yang lebih terbatas terhadap konfigurasi internal aplikasi dibandingkan model layanan lainnya.

**b. Platform as a Service (PaaS)**

PaaS merupakan model layanan cloud yang menyediakan platform untuk mengembangkan, menjalankan, dan mengelola aplikasi.

Penyedia layanan bertanggung jawab terhadap infrastruktur, sistem operasi, runtime, dan lingkungan pendukung aplikasi. Pengembang dapat lebih fokus pada penulisan kode dan pengembangan fitur.

Contohnya:

- Google App Engine.
- Heroku.
- Platform aplikasi berbasis cloud lainnya.

**[MODIFIKASI]** Sebagai contoh, seorang pengembang ingin membuat aplikasi berbasis web menggunakan Python. Dengan PaaS, pengembang dapat mengunggah aplikasi ke platform yang sudah menyediakan lingkungan eksekusi tanpa harus mengatur server dan sistem operasi secara manual.

PaaS mempercepat proses pengembangan, tetapi memberikan kontrol yang lebih terbatas terhadap infrastruktur dibandingkan IaaS.

**c. Infrastructure as a Service (IaaS)**

IaaS merupakan model layanan yang menyediakan infrastruktur komputasi virtual melalui internet.

Sumber daya yang disediakan dapat berupa:

- Virtual Machine.
- Penyimpanan.
- Jaringan.
- Kapasitas pemrosesan.
- Infrastruktur server virtual.

Pengguna memiliki kendali lebih besar terhadap sistem operasi, konfigurasi jaringan, dan aplikasi yang dijalankan.

Contohnya:

- Amazon EC2.
- Google Compute Engine.
- Azure Virtual Machines.

**[MODIFIKASI]** Sebagai contoh, sebuah perusahaan ingin menjalankan aplikasi dengan konfigurasi sistem operasi Linux tertentu. Perusahaan tersebut dapat menyewa Virtual Machine melalui IaaS, kemudian menginstal database, web server, dan aplikasi sesuai kebutuhan.

IaaS memberikan fleksibilitas yang tinggi, tetapi pengguna juga memiliki tanggung jawab lebih besar dalam mengelola sistem operasi, aplikasi, dan keamanan konfigurasi.

**Perbandingan SaaS, PaaS, dan IaaS**

| Komponen | On-Premise | IaaS | PaaS | SaaS |
|---|---|---|---|---|
| Applications | Pengguna | Pengguna | Pengguna | Provider |
| Data | Pengguna | Pengguna | Pengguna | Provider |
| Runtime | Pengguna | Pengguna | Provider | Provider |
| Middleware | Pengguna | Pengguna | Provider | Provider |
| Operating System | Pengguna | Pengguna | Provider | Provider |
| Virtualization | Pengguna | Provider | Provider | Provider |
| Servers | Pengguna | Provider | Provider | Provider |
| Storage | Pengguna | Provider | Provider | Provider |
| Networking | Pengguna | Provider | Provider | Provider |

Tabel tersebut menunjukkan pembagian tanggung jawab pengelolaan layanan. Semakin tinggi tingkat abstraksi layanan, semakin banyak komponen yang dikelola oleh penyedia cloud.

**d. Everything as a Service (XaaS)**

XaaS merupakan istilah yang menggambarkan perkembangan model layanan cloud yang menyediakan berbagai kebutuhan teknologi sebagai layanan.

Konsep ini tidak hanya terbatas pada perangkat lunak, platform, dan infrastruktur, tetapi dapat mencakup berbagai sumber daya dan layanan lainnya.

**[MODIFIKASI]** Contohnya adalah Database as a Service (DBaaS), Storage as a Service, dan Function as a Service (FaaS). Pengguna dapat memanfaatkan fasilitas tersebut tanpa harus membangun seluruh infrastruktur pendukungnya sendiri.

### 4. Model Deployment Cloud Computing

Model deployment menjelaskan bagaimana infrastruktur cloud ditempatkan, dimiliki, dan digunakan oleh organisasi atau pelanggan.

Dalam materi terdapat empat model deployment.

**a. Public Cloud**

Public cloud merupakan layanan cloud yang disediakan untuk digunakan oleh banyak pelanggan melalui infrastruktur milik penyedia layanan.

Pengguna dapat menyewa sumber daya sesuai kebutuhan tanpa harus membangun pusat data sendiri.

Contohnya adalah layanan AWS, Google Cloud, dan Microsoft Azure.

Kelebihannya adalah mudah digunakan, fleksibel, serta tidak membutuhkan investasi besar untuk membeli perangkat keras.

Namun, pengguna memiliki ketergantungan terhadap penyedia layanan dan perlu memperhatikan pengaturan keamanan serta privasi data.

**b. Private Cloud**

Private cloud merupakan infrastruktur cloud yang digunakan secara khusus oleh satu organisasi.

Infrastruktur tersebut dapat dikelola sendiri oleh organisasi atau melalui pihak penyedia layanan.

Contohnya adalah perusahaan atau institusi yang membangun lingkungan cloud internal untuk menjalankan sistem informasi dan menyimpan data penting.

Kelebihannya adalah organisasi mempunyai kontrol lebih besar terhadap infrastruktur dan kebijakan keamanan.

Kekurangannya adalah membutuhkan biaya serta tenaga teknis untuk pengelolaan dan pemeliharaan.

**c. Hybrid Cloud**

Hybrid cloud merupakan kombinasi penggunaan public cloud dan private cloud.

Model ini memungkinkan organisasi menggunakan kedua lingkungan tersebut sesuai kebutuhan.

**[MODIFIKASI]** Sebagai contoh, sebuah perusahaan menyimpan data penting pelanggan pada private cloud, sedangkan aplikasi publik dan layanan yang membutuhkan kapasitas besar dijalankan menggunakan public cloud.

Dengan pendekatan ini, organisasi dapat mempertahankan kontrol terhadap data tertentu sekaligus memanfaatkan fleksibilitas public cloud.

Tantangannya adalah integrasi jaringan, pengelolaan data, dan keamanan antara kedua lingkungan tersebut.

**d. Community Cloud**

Community cloud merupakan model cloud yang digunakan bersama oleh beberapa organisasi yang mempunyai kebutuhan, kepentingan, atau kebijakan yang serupa.

Contohnya adalah beberapa institusi pendidikan yang menggunakan infrastruktur cloud bersama untuk mendukung layanan akademik.

Model ini memungkinkan biaya dan sumber daya dibagi bersama, tetapi pengelolaan serta kebijakan akses harus disepakati oleh organisasi yang terlibat.

### 5. Arsitektur dan Komponen Cloud Computing

Arsitektur Cloud Computing terdiri dari beberapa komponen yang saling berhubungan untuk menyediakan layanan komputasi kepada pengguna.

Setiap komponen mempunyai fungsi masing-masing dalam proses penyediaan, pengelolaan, dan penggunaan sumber daya cloud.

Komponen utama yang terdapat dalam materi meliputi:

**a. Application**

Application merupakan lapisan aplikasi yang digunakan oleh pengguna. Komponen ini berkaitan dengan model layanan SaaS.

Contohnya adalah aplikasi pengolah dokumen, sistem informasi, dan layanan berbasis web.

**b. Services**

Services merupakan layanan yang disediakan oleh infrastruktur cloud, termasuk layanan PaaS dan IaaS.

Layanan tersebut dapat berupa platform pengembangan aplikasi, komputasi virtual, dan fasilitas pendukung lainnya.

**c. Cloud Runtime**

Cloud Runtime merupakan lingkungan eksekusi yang digunakan untuk menjalankan aplikasi atau Virtual Machine.

Komponen ini menyediakan lingkungan agar aplikasi dapat berjalan sesuai konfigurasi yang dibutuhkan.

**d. Storage**

Storage merupakan komponen yang digunakan untuk menyimpan data dalam lingkungan cloud.

Penyimpanan dapat digunakan untuk berbagai kebutuhan, seperti menyimpan dokumen, database, file aplikasi, dan data cadangan.

**e. Infrastructure**

Infrastructure merupakan bagian dasar yang mendukung seluruh operasi Cloud Computing.

Komponen infrastruktur meliputi:

1. **Hypervisor:** perangkat lunak yang berfungsi sebagai Virtual Machine Monitor untuk membuat dan mengelola Virtual Machine.
2. **Management Software:** perangkat lunak yang digunakan penyedia cloud untuk mengelola sumber daya dan layanan.
3. **Deployment Software:** perangkat atau tools yang membantu proses deployment aplikasi dan pengelolaan infrastruktur.
4. **Network:** menyediakan konektivitas komunikasi antarperangkat dan layanan.
5. **Server:** perangkat komputasi yang menjalankan aplikasi dan memproses permintaan.
6. **Security-related Tools:** komponen yang membantu melindungi sistem, data, dan akses terhadap layanan cloud.

**[MODIFIKASI] Hubungan Antarkomponen**

Komponen tersebut bekerja secara berlapis dan saling mendukung. Pengguna berinteraksi dengan aplikasi, kemudian aplikasi memanfaatkan layanan yang tersedia. Layanan tersebut berjalan di atas lingkungan runtime dan infrastruktur cloud.

Sebagai contoh, ketika pengguna membuka aplikasi berbasis web, permintaan akan diterima melalui jaringan, diproses oleh server, kemudian aplikasi mengambil data dari storage atau database sebelum mengirimkan hasilnya kembali kepada pengguna.

Apabila salah satu komponen mengalami gangguan, layanan dapat ikut terpengaruh. Oleh karena itu, pengelolaan infrastruktur, keamanan, dan ketersediaan sumber daya menjadi bagian penting dari arsitektur cloud.

### 6. Scalability dan Redundancy

Scalability dan redundancy merupakan dua konsep penting dalam Cloud Computing untuk mendukung kemampuan sistem dalam menangani perubahan kebutuhan serta mengurangi risiko gangguan layanan.

**a. Scalability**

Scalability atau skalabilitas merupakan kemampuan sistem untuk menangani perubahan kebutuhan sumber daya komputasi, baik peningkatan maupun penurunan kapasitas.

Sumber daya yang dapat disesuaikan meliputi:

1. Disk I/O.
2. Memory.
3. Network I/O.
4. CPU.

Dalam materi juga dijelaskan bahwa scalability berbeda dengan elasticity.

Scalability lebih mengarah pada kemampuan sistem untuk ditingkatkan atau dikurangi kapasitasnya, sedangkan elasticity menekankan penyesuaian kapasitas secara dinamis mengikuti perubahan beban kerja.

**[MODIFIKASI]** Contohnya, sebuah aplikasi akademik digunakan oleh mahasiswa untuk melakukan pengisian KRS. Ketika periode KRS dibuka, jumlah pengguna yang mengakses sistem meningkat secara signifikan.

Apabila kapasitas server tidak mencukupi, aplikasi dapat mengalami perlambatan atau bahkan tidak dapat diakses.

Dengan scalability, kapasitas komputasi dapat ditingkatkan agar aplikasi tetap mampu melayani permintaan pengguna.

**Karakteristik scalable cloud:**

- Sizeable Difference: kapasitas dapat bertambah atau berkurang secara signifikan.
- Grow or Shrink: sumber daya mengikuti kebutuhan organisasi.
- Speed: perubahan kapasitas dapat dilakukan dengan cepat.
- Easy: proses penyesuaian kapasitas relatif mudah.
- Non-disruptive: perubahan kapasitas diupayakan tanpa mengganggu layanan atau menyebabkan downtime.

**b. Tipe Scalability**

Terdapat tiga tipe scalability yang dibahas dalam materi.

1. **Vertical Scaling**

   Vertical scaling merupakan penambahan kapasitas pada satu server yang sama.

   Contohnya adalah meningkatkan kapasitas RAM, CPU, atau sumber daya komputasi pada sebuah Virtual Machine.

   Keuntungannya adalah pengelolaan relatif sederhana karena tidak perlu menambahkan banyak server.

   Keterbatasannya adalah kapasitas tetap dibatasi oleh kemampuan maksimum server tersebut.

2. **Horizontal Scaling**

   Horizontal scaling merupakan penambahan jumlah server untuk menangani beban kerja yang lebih besar.

   Contohnya, sebuah aplikasi yang sebelumnya dijalankan pada satu server kemudian dijalankan pada beberapa server tambahan.

   Permintaan pengguna dapat didistribusikan menggunakan load balancer.

   Keuntungannya adalah beban kerja dapat dibagi ke beberapa server, tetapi sistem membutuhkan pengelolaan komunikasi dan koordinasi antarmesin.

3. **Diagonal Scaling**

   Diagonal scaling merupakan kombinasi vertical scaling dan horizontal scaling.

   Pendekatan ini dilakukan dengan meningkatkan kapasitas satu server terlebih dahulu. Ketika kapasitas tersebut sudah mencapai batas tertentu, sistem menambahkan server baru.

   Pendekatan ini menggabungkan peningkatan kemampuan server dengan penambahan jumlah server.

**c. Pengaturan Scaling**

Berdasarkan materi, scaling dapat dilakukan melalui tiga pendekatan:

- **Manual:** perubahan kapasitas dilakukan secara manual berdasarkan hasil pemantauan.
- **Scheduled:** perubahan kapasitas dilakukan berdasarkan jadwal atau pola penggunaan yang sudah diketahui.
- **Automatic:** perubahan kapasitas dilakukan secara otomatis berdasarkan kondisi dan kebutuhan sistem.

Contoh layanan automatic scaling:

- AWS Auto Scaling.
- Google Cloud Load Balancing and Auto Scaling.
- Azure Autoscale.

**d. Redundancy**

Redundancy atau redundansi merupakan mekanisme menyediakan duplikasi sumber daya agar sistem tetap dapat berjalan ketika salah satu komponen mengalami kegagalan.

Pada Cloud Computing, redundansi dapat diterapkan pada:

- Data.
- Server.
- Sistem.
- Konfigurasi.
- Infrastruktur penyimpanan.

Contohnya, sebuah database memiliki salinan data pada node penyimpanan lain. Ketika salah satu node mengalami kerusakan, salinan data yang tersedia dapat membantu proses pemulihan.

Beberapa layanan yang disebutkan dalam materi:

- AWS Backup.
- Microsoft Azure Backup.

**[MODIFIKASI] Hubungan Redundancy dengan Distributed Database**

Redundancy juga menjadi salah satu fitur penting dalam distributed database management systems.

Contohnya:

1. PostgreSQL sebagai database relasional SQL.
2. Apache Cassandra sebagai database NoSQL.
3. YugabyteDB dan TiDB sebagai database NewSQL.

Dalam database terdistribusi, data dapat direplikasi ke beberapa node agar ketersediaan data lebih terjaga.

Namun, redundansi bukan berarti sistem sepenuhnya bebas dari kegagalan. Pengelolaan replikasi, konsistensi data, dan proses pemulihan tetap diperlukan.

### 7. Virtualisasi dan Teknologi Container

Virtualisasi merupakan teknologi yang memungkinkan sumber daya perangkat keras atau komputasi dibuat menjadi lingkungan virtual.

Virtualisasi menjadi salah satu teknologi utama Cloud Computing karena memungkinkan satu perangkat keras fisik digunakan untuk menjalankan beberapa lingkungan komputasi secara terpisah.

**a. Virtualization**

Virtualisasi memungkinkan sumber daya fisik seperti CPU, RAM, penyimpanan, dan jaringan dialokasikan kepada beberapa lingkungan virtual.

Sebagai contoh, satu server fisik dapat menjalankan beberapa Virtual Machine dengan sistem operasi dan konfigurasi yang berbeda.

Teknologi ini memungkinkan pemanfaatan sumber daya perangkat keras menjadi lebih efisien.

**b. Hypervisor**

Hypervisor atau Virtual Machine Monitor merupakan perangkat lunak yang berfungsi membuat dan mengelola Virtual Machine.

Hypervisor mengatur pembagian sumber daya perangkat keras kepada setiap mesin virtual agar dapat berjalan secara terpisah.

Terdapat dua jenis arsitektur hypervisor yang ditampilkan dalam materi.

1. **Hosted Architecture**

   Pada Hosted Architecture, hypervisor berjalan di atas sistem operasi utama atau Host OS.

   Susunan sederhananya:

   - Hardware.
   - Host Operating System.
   - Hypervisor.
   - Virtual Machine.

   Contohnya adalah penggunaan QEMU dalam konfigurasi hosted.

2. **Bare-Metal Architecture**

   Pada Bare-Metal Architecture, hypervisor berjalan langsung di atas perangkat keras tanpa membutuhkan Host OS sebagai lapisan perantara.

   Susunannya:

   - Hardware.
   - Hypervisor.
   - Virtual Machine.

   Contohnya adalah Xen Project.

**[MODIFIKASI]** Perbedaan kedua arsitektur tersebut terletak pada posisi hypervisor dalam susunan sistem. Hosted Architecture memerlukan sistem operasi utama sebagai tempat hypervisor berjalan, sedangkan Bare-Metal Architecture menempatkan hypervisor langsung di atas perangkat keras.

**c. Virtual Machine**

Virtual Machine merupakan lingkungan komputer virtual yang memiliki sumber daya komputasi sendiri, seperti CPU, RAM, penyimpanan, dan sistem operasi.

Setiap Virtual Machine dapat menjalankan sistem operasi serta aplikasi yang berbeda meskipun menggunakan satu perangkat keras fisik yang sama.

Contohnya, sebuah server fisik dapat menjalankan Virtual Machine Linux untuk web server dan Virtual Machine lainnya untuk database.

**d. Container**

Container merupakan teknologi yang digunakan untuk mengemas aplikasi beserta library dan dependensi yang dibutuhkan agar dapat dijalankan dalam lingkungan yang konsisten.

Berbeda dengan Virtual Machine yang umumnya menjalankan sistem operasi masing-masing, container berbagi kernel dari Host OS melalui container runtime.

Container memiliki beberapa karakteristik:

- Lebih ringan dibandingkan Virtual Machine secara umum.
- Memiliki lingkungan aplikasi yang terisolasi.
- Mempermudah proses pemindahan aplikasi antarlingkungan.
- Membantu konsistensi aplikasi ketika dikembangkan, diuji, dan dijalankan.
- Mempermudah pengelolaan aplikasi dalam lingkungan cloud.

**[MODIFIKASI] Perbedaan Virtual Machine dan Container**

| Aspek | Virtual Machine | Container |
|---|---|---|
| Sistem Operasi | Memiliki Guest OS masing-masing | Berbagi kernel Host OS |
| Penggunaan Sumber Daya | Relatif lebih besar | Relatif lebih ringan |
| Isolasi | Isolasi pada tingkat mesin virtual | Isolasi pada tingkat proses |
| Waktu Menjalankan | Umumnya lebih lama | Umumnya lebih cepat |
| Penggunaan | Menjalankan lingkungan OS yang berbeda | Mengemas dan menjalankan aplikasi |

Perbedaan tersebut membuat container banyak digunakan dalam pengembangan aplikasi modern, terutama pada arsitektur microservices.

**e. Container Runtime dan Teknologi Pendukung**

Container Runtime merupakan komponen yang bertugas menjalankan dan mengelola container.

Dalam ilustrasi materi, susunan container terdiri dari:

1. Physical Infrastructure.
2. Host OS.
3. Container Runtime.
4. Container yang berisi aplikasi dan library.

Beberapa teknologi yang disebutkan dalam materi:

- **Docker:** platform yang digunakan untuk membangun, mengemas, dan menjalankan aplikasi dalam container.
- **Podman:** perangkat untuk mengelola dan menjalankan container.
- **runc:** teknologi runtime tingkat rendah untuk menjalankan container.

**[MODIFIKASI]** Sebagai contoh, seorang pengembang membuat aplikasi menggunakan Python dan membutuhkan library tertentu. Dengan Docker atau Podman, aplikasi beserta dependensinya dapat dikemas menjadi container sehingga lingkungan eksekusinya lebih konsisten ketika dipindahkan dari komputer pengembang ke server cloud.

### 8. Serverless Computing

Serverless merupakan model eksekusi dalam Cloud Computing ketika penyedia layanan bertanggung jawab terhadap pengelolaan dan penyediaan server secara dinamis.

Istilah serverless sering diterjemahkan sebagai komputasi nirserver.

Namun, istilah tersebut tidak berarti aplikasi benar-benar berjalan tanpa server.

Pada kenyataannya, server tetap digunakan untuk menjalankan proses komputasi. Perbedaannya adalah pengguna tidak perlu mengelola penyediaan dan pengelolaan server secara langsung karena tanggung jawab tersebut dilakukan oleh penyedia layanan cloud.

**[MODIFIKASI] Cara Kerja Serverless**

Pada model serverless, pengembang cukup menyiapkan fungsi atau kode yang ingin dijalankan. Ketika terdapat permintaan atau event tertentu, penyedia cloud akan menyediakan lingkungan eksekusi yang diperlukan.

Contoh alurnya:

1. Pengguna melakukan suatu tindakan pada aplikasi.
2. Aplikasi mengirimkan permintaan atau event.
3. Layanan serverless menerima event tersebut.
4. Fungsi dijalankan oleh infrastruktur penyedia cloud.
5. Hasil pemrosesan dikirimkan kembali kepada aplikasi.

Contoh penerapan:

Sebuah aplikasi memiliki fitur untuk mengirimkan email otomatis ketika pengguna melakukan pendaftaran. Pengembang dapat menggunakan fungsi serverless untuk menjalankan proses pengiriman email ketika terdapat event pendaftaran.

Dengan pendekatan ini, pengembang tidak perlu mengelola server khusus yang terus berjalan hanya untuk menangani fungsi tersebut.

Keuntungan serverless antara lain:

- Mengurangi pekerjaan pengelolaan infrastruktur.
- Mempermudah pengembangan fungsi tertentu.
- Mendukung penyesuaian kapasitas sesuai permintaan.
- Penggunaan sumber daya dapat disesuaikan dengan mekanisme layanan penyedia.

Keterbatasannya adalah ketergantungan terhadap penyedia layanan, batasan lingkungan eksekusi, dan potensi keterlambatan ketika fungsi harus memulai lingkungan eksekusi baru.

### 9. Cloud Native Application (CNA)

Cloud Native Application merupakan pendekatan pengembangan dan pengoperasian aplikasi yang memanfaatkan kemampuan serta fasilitas Cloud Computing.

Konsep ini berfokus pada kemampuan aplikasi untuk berjalan dalam lingkungan cloud yang dinamis, mendukung scalability, elasticity, dan sistem terdistribusi.

Istilah Cloud Native pertama kali dicetuskan oleh Matt Stine dari Pivotal pada tahun 2013.

Menurut Cloud Native Computing Foundation (CNCF), teknologi cloud native membantu organisasi membangun dan menjalankan aplikasi yang scalable pada lingkungan cloud modern, baik public, private, maupun hybrid cloud.

Teknologi tersebut mencakup:

- Containers.
- Service Meshes.
- Microservices.
- Immutable Infrastructure.
- Declarative APIs.
- Automation.

Teknologi tersebut memungkinkan sistem dibangun secara loosely coupled, tangguh, mudah dikelola, dan dapat diamati.

**[MODIFIKASI] Karakteristik Cloud Native Application**

Beberapa karakteristik penting CNA antara lain:

1. **Scalable:** aplikasi dapat menyesuaikan kapasitas berdasarkan kebutuhan.
2. **Distributed:** aplikasi dapat terdiri dari beberapa layanan yang berjalan pada lingkungan komputasi berbeda.
3. **Loosely Coupled:** setiap layanan memiliki ketergantungan yang lebih rendah terhadap layanan lainnya.
4. **Resilient:** sistem dirancang agar dapat menghadapi gangguan dan melakukan pemulihan.
5. **Observable:** kondisi aplikasi dapat dipantau melalui log, metrics, dan tracing.
6. **Automated:** proses pengembangan, pengujian, deployment, dan pengelolaan dapat diotomatisasi.

**a. Microservices**

Microservices merupakan pendekatan arsitektur yang membagi aplikasi menjadi beberapa layanan kecil yang mempunyai tanggung jawab tertentu.

Setiap layanan dapat dikembangkan, dijalankan, dan diperbarui secara lebih mandiri.

Contohnya adalah aplikasi e-commerce yang memiliki beberapa layanan:

- User Service untuk mengelola akun pengguna.
- Product Service untuk mengelola informasi produk.
- Order Service untuk mengelola pesanan.
- Payment Service untuk memproses pembayaran.
- Notification Service untuk mengirimkan pemberitahuan.

**[MODIFIKASI]** Pembagian tersebut membuat pengembangan aplikasi lebih fleksibel. Apabila fitur pembayaran mengalami perubahan, pengembang dapat memperbarui Payment Service tanpa harus mengubah seluruh aplikasi.

Namun, microservices juga menimbulkan tantangan baru, seperti komunikasi antarservice, pengelolaan data, keamanan API, dan pemantauan sistem secara keseluruhan.

**b. Containers**

Container digunakan untuk mengemas aplikasi beserta dependensinya sehingga aplikasi dapat berjalan dalam lingkungan yang konsisten.

Dalam arsitektur cloud native, container membantu proses deployment dan pengelolaan aplikasi yang terdiri dari banyak layanan.

Docker digunakan sebagai salah satu teknologi container, sedangkan Kubernetes digunakan untuk melakukan orchestration atau pengelolaan sekumpulan container.

**c. DevOps**

DevOps merupakan gabungan dari Development dan Operations.

DevOps adalah pendekatan kerja yang menyatukan proses pengembangan perangkat lunak dengan pengoperasian sistem.

Tujuannya adalah meningkatkan kolaborasi antara tim pengembang dan tim operasional sehingga proses pengembangan, pengujian, dan pengiriman aplikasi dapat berlangsung lebih cepat dan teratur.

Contohnya, ketika pengembang melakukan perubahan kode, tim operasional dan sistem otomatisasi dapat membantu memastikan perubahan tersebut diuji dan dipersiapkan untuk deployment.

**d. CI/CD**

CI/CD merupakan rangkaian proses otomatisasi dalam pengembangan dan pengiriman perangkat lunak.

CI adalah Continuous Integration, yaitu proses mengintegrasikan perubahan kode ke dalam repository secara rutin disertai proses pengujian.

CD adalah Continuous Delivery, yaitu proses mempersiapkan perubahan aplikasi agar dapat dirilis melalui pipeline pengiriman yang terotomatisasi.

**[MODIFIKASI]** Secara umum, alur CI/CD dapat dijelaskan sebagai berikut:

1. Developer menulis dan mengubah kode program.
2. Perubahan kode dikirim ke repository.
3. Sistem CI menjalankan proses build dan pengujian.
4. Apabila pengujian berhasil, aplikasi dipersiapkan untuk deployment.
5. Sistem CD membantu mengirimkan aplikasi ke lingkungan tujuan.

Contoh teknologi yang dapat digunakan adalah GitHub Actions, Jenkins, dan GitLab CI/CD.

**e. Teknologi Pendukung Cloud Native**

Selain komponen utama tersebut, materi juga menyebutkan teknologi pendukung dari ekosistem CNCF.

Contohnya:

- etcd untuk penyimpanan data konfigurasi terdistribusi dan koordinasi.
- Teknologi service mesh untuk membantu pengelolaan komunikasi antarlayanan.
- Kubernetes untuk orchestration container.

Komponen tersebut membantu aplikasi cloud native berjalan secara lebih terstruktur dan mudah dikelola.

**f. Arsitektur Cloud Native Application**

Ilustrasi dalam materi memperlihatkan bahwa arsitektur CNA dapat terdiri dari beberapa lapisan.

1. **User Interface Layer:** bagian yang digunakan pengguna untuk berinteraksi dengan aplikasi, misalnya web client, mobile client, dan perangkat IoT.
2. **API Gateway Layer:** menjadi pintu masuk permintaan dari pengguna menuju layanan yang tersedia.
3. **Business Logic Layer:** berisi microservices yang menjalankan proses bisnis aplikasi.
4. **Data Access Layer:** menangani komunikasi antara layanan dengan penyimpanan data.
5. **Database Layer:** menyediakan penyimpanan data dan message queue untuk mendukung pertukaran informasi.

Pada contoh diagram lain, terdapat API Gateway yang menghubungkan aplikasi pengguna dengan beberapa microservices. Setiap microservice dapat mempunyai database sendiri atau menggunakan teknologi penyimpanan yang sesuai dengan kebutuhannya.

Event Bus juga dapat digunakan untuk mendukung komunikasi berbasis pesan antarservice.

**[MODIFIKASI]** Arsitektur tersebut memperlihatkan bahwa aplikasi cloud native tidak harus dibangun sebagai satu program besar. Sistem dapat dibagi menjadi layanan-layanan yang mempunyai fungsi khusus dan berkomunikasi melalui API maupun mekanisme pertukaran pesan.

Pendekatan tersebut mendukung pengembangan independen dan scalability pada masing-masing layanan.

**g. Tahapan Pembangunan Cloud Native Application**

Berdasarkan diagram dalam materi, pembangunan CNA dapat dilakukan melalui beberapa tahapan.

1. **Define Architecture**

   Menentukan arsitektur aplikasi, lingkungan cloud yang digunakan, kebutuhan sistem, scalability, resiliency, dan teknologi pendukung.

2. **Define Microservices**

   Membagi aplikasi menjadi layanan-layanan yang mempunyai fungsi dan tanggung jawab masing-masing.

3. **Containerize Services**

   Mengemas setiap layanan beserta dependensinya ke dalam container agar mudah dijalankan dan dipindahkan.

4. **Redesign Datastore**

   Merancang penyimpanan data berdasarkan kebutuhan aplikasi, jenis data, serta pola akses baca dan tulis.

5. **Build and Deploy**

   Membangun aplikasi, melakukan pengujian, dan menjalankan deployment menggunakan pendekatan DevOps dan CI/CD.

6. **Verify**

   Melakukan validasi terhadap aplikasi, termasuk pengujian keandalan, performa, dan kemampuan sistem menghadapi gangguan.

Tahapan tersebut menunjukkan bahwa pembangunan aplikasi cloud native tidak hanya berfokus pada pembuatan kode, tetapi juga memperhatikan arsitektur, pengelolaan data, otomatisasi, dan keandalan sistem.

**h. Platform Cloud Native Application**

Beberapa platform yang dicantumkan dalam materi antara lain:

- AWS.
- Choreo.
- Google Cloud.
- Microsoft Azure.

Platform tersebut menyediakan layanan dan teknologi yang dapat digunakan untuk membangun serta menjalankan aplikasi cloud native.

---

## D. CONTOH PENERAPAN DAN ANALISIS

### 1. Contoh Penerapan

**Studi Kasus: Sistem Informasi Akademik Berbasis Cloud Computing**

Sebuah perguruan tinggi mempunyai sistem informasi akademik yang digunakan oleh mahasiswa, dosen, dan bagian administrasi.

Sistem tersebut digunakan untuk berbagai aktivitas, seperti pengisian KRS, melihat nilai, mengelola data mahasiswa, dan mengakses informasi perkuliahan.

Apabila seluruh sistem hanya dijalankan pada satu server fisik, peningkatan jumlah pengguna dapat menyebabkan server mengalami beban yang tinggi.

Untuk mengatasi permasalahan tersebut, perguruan tinggi dapat menerapkan Cloud Computing.

Penerapannya dapat dijelaskan sebagai berikut:

**a. Penggunaan IaaS**

Perguruan tinggi menyewa Virtual Machine dari penyedia cloud untuk menjalankan aplikasi akademik dan database.

Dengan demikian, perguruan tinggi tidak harus membeli seluruh perangkat keras server sendiri.

**b. Penggunaan Scalability**

Ketika periode pengisian KRS berlangsung, jumlah pengguna meningkat. Sistem dapat menggunakan horizontal scaling dengan menambahkan beberapa server aplikasi.

Load balancer kemudian mendistribusikan permintaan pengguna ke server yang tersedia.

**c. Penggunaan Redundancy**

Data akademik direplikasi atau dicadangkan pada media penyimpanan lain agar dapat dipulihkan apabila terjadi kegagalan pada salah satu komponen.

**d. Penggunaan Container**

Aplikasi akademik dikemas menggunakan Docker agar lingkungan pengembangan dan produksi memiliki konfigurasi yang konsisten.

**e. Penggunaan Microservices**

Sistem dapat dibagi menjadi beberapa layanan, seperti:

- Authentication Service untuk autentikasi pengguna.
- Student Service untuk pengelolaan data mahasiswa.
- Academic Service untuk pengelolaan KRS dan nilai.
- Notification Service untuk mengirimkan pemberitahuan.

**f. Penggunaan CI/CD**

Setiap perubahan aplikasi dapat melalui proses build dan pengujian otomatis sebelum diterapkan ke lingkungan produksi.

Dengan pendekatan ini, perguruan tinggi dapat mengembangkan sistem akademik yang lebih fleksibel, mudah dikelola, dan mampu menyesuaikan kapasitas sesuai jumlah pengguna.

### 2. Analisis

Cloud Computing mempunyai peran penting dalam pembangunan sistem terdistribusi karena memungkinkan sumber daya komputasi digunakan melalui jaringan tanpa harus seluruhnya dimiliki oleh pengguna.

Berdasarkan materi yang telah dipelajari, terdapat beberapa hal yang dapat dianalisis.

**a. Hubungan Cloud Computing dengan Sistem Terdistribusi**

Cloud Computing mempunyai hubungan erat dengan sistem terdistribusi karena infrastruktur cloud dapat terdiri dari banyak server, penyimpanan, dan komponen jaringan yang bekerja bersama untuk menyediakan layanan.

Pengguna melihat layanan sebagai satu kesatuan, meskipun proses di belakangnya dapat berlangsung pada beberapa mesin yang berbeda.

Hal tersebut memungkinkan aplikasi menangani permintaan dari banyak pengguna secara bersamaan.

**b. Pentingnya Scalability dan Redundancy**

Scalability dibutuhkan agar sistem mampu menyesuaikan kapasitas ketika jumlah pengguna atau beban kerja berubah.

Sementara itu, redundancy dibutuhkan untuk mengurangi risiko kehilangan data dan gangguan layanan akibat kegagalan komponen.

Kedua konsep ini mempunyai fungsi berbeda tetapi saling melengkapi. Scalability berfokus pada kemampuan menangani perubahan beban kerja, sedangkan redundancy berfokus pada ketersediaan dan perlindungan terhadap kegagalan.

**c. Peran Virtualisasi dan Container**

Virtualisasi memungkinkan satu perangkat keras menjalankan beberapa mesin virtual sehingga penggunaan sumber daya menjadi lebih efisien.

Container kemudian membantu pengembang mengemas aplikasi beserta dependensinya dalam lingkungan yang konsisten.

Keduanya menjadi teknologi penting dalam infrastruktur cloud modern, meskipun memiliki cara kerja dan tingkat isolasi yang berbeda.

**d. Peran Cloud Native dalam Pengembangan Aplikasi**

Cloud Native Application memberikan pendekatan pengembangan aplikasi yang memanfaatkan karakteristik cloud, seperti scalability, distributed processing, dan automation.

Dengan menggunakan microservices, container, DevOps, serta CI/CD, pengembangan aplikasi dapat dilakukan secara lebih fleksibel.

Namun, penerapan cloud native juga membutuhkan pengelolaan yang baik karena semakin banyak layanan berarti semakin kompleks komunikasi, keamanan, monitoring, dan pengelolaan datanya.

**e. Keterbatasan Cloud Computing**

Meskipun memberikan banyak keuntungan, Cloud Computing juga mempunyai beberapa keterbatasan yang perlu diperhatikan.

1. **Ketergantungan pada jaringan:** layanan cloud membutuhkan koneksi jaringan agar dapat diakses.
2. **Keamanan data:** organisasi perlu memastikan bahwa data dan akses pengguna dilindungi dengan baik.
3. **Ketergantungan penyedia layanan:** penggunaan layanan tertentu dapat menyebabkan ketergantungan terhadap teknologi dan kebijakan provider.
4. **Biaya penggunaan:** biaya dapat meningkat apabila sumber daya tidak dikelola dan dipantau dengan baik.
5. **Kompleksitas pengelolaan:** sistem yang menggunakan banyak layanan dan server membutuhkan monitoring serta koordinasi yang baik.

Dari analisis tersebut, dapat dipahami bahwa keberhasilan penerapan Cloud Computing tidak hanya ditentukan oleh teknologi yang digunakan, tetapi juga oleh pemilihan model layanan, desain arsitektur, pengelolaan sumber daya, dan kebutuhan organisasi.

---

## E. PENGGUNAAN ARTIFICIAL INTELLIGENCE (AI)

### 1. AI yang Digunakan

- Nama AI: ChatGPT GPT-6.
- Tujuan penggunaan: Membantu memahami, menganalisis, menyusun, dan mengembangkan rangkuman materi perkuliahan.
- Sumber utama: Materi perkuliahan yang diberikan oleh dosen dalam bentuk PDF.
- File yang dianalisis: `07--cloud-computing.pdf`.

### 2. Prompt yang Digunakan

Berikut prompt yang digunakan untuk menghasilkan rangkuman materi:

> Amatilah dan pelajari seluruh isi Modul 07 dengan topik Cloud Computing pada mata kuliah Teori Sistem Terdistribusi dan Terdesentralisasi. Baca seluruh halaman PDF, termasuk diagram, tabel, ilustrasi, dan contoh yang diberikan dosen.
>
> Buat rangkuman materi pertemuan 7 menggunakan template README.md yang telah diberikan.
>
> Kembangkan setiap pokok bahasan dengan penjelasan teori yang lengkap, mekanisme kerja, karakteristik, contoh penerapan dalam bidang Informatika, serta analisis manfaat dan keterbatasannya.
>
> Pertahankan istilah teknis dan makna materi asli. Jangan mengarang informasi yang tidak tersedia dalam materi. Gunakan bahasa Indonesia yang natural seperti laporan mahasiswa S1 Informatika, formal tetapi mudah dipahami.
>
> Berikan tanda **[MODIFIKASI]** pada bagian yang mengalami pengembangan substantif. Pertahankan seluruh struktur A sampai G sesuai template, termasuk bagian identitas, tujuan pembelajaran, rangkuman materi, contoh penerapan dan analisis, penggunaan AI, kesimpulan, serta daftar referensi.
>
> Pastikan hasil akhir lengkap, sistematis, dan siap dimasukkan ke repository GitHub dalam format Markdown.

### 3. Bagian yang Disesuaikan dari Keluaran AI

Bagian dari hasil rangkuman yang mengalami pengembangan dan penyesuaian meliputi:

1. **Karakteristik dan Model Layanan Cloud Computing:** Penjelasan SaaS, PaaS, IaaS, XaaS, dan enam karakteristik cloud dikembangkan dengan contoh penggunaan agar perbedaan setiap konsep lebih mudah dipahami.

2. **Scalability dan Redundancy:** Penjelasan vertical, horizontal, dan diagonal scaling diperluas dengan contoh penerapan pada sistem informasi akademik serta hubungan redundansi dengan distributed database.

3. **Virtualisasi dan Teknologi Container:** Pembahasan hypervisor, Virtual Machine, Hosted Architecture, Bare-Metal Architecture, dan container dikembangkan dengan penjelasan perbedaan cara kerja dan penggunaannya.

4. **Cloud Native Application:** Pembahasan microservices, DevOps, CI/CD, API Gateway, dan tahapan pembangunan CNA diperluas agar hubungan antar komponen dan proses pengembangan aplikasi lebih mudah dipahami.

Penyesuaian juga dilakukan pada bagian contoh penerapan dan analisis agar materi tidak hanya berisi definisi, tetapi menunjukkan bagaimana konsep Cloud Computing digunakan dalam pembangunan sistem informasi.

### 4. Penanda Hasil Modifikasi

Bagian yang mengalami pengembangan atau penyesuaian diberikan tanda **[MODIFIKASI]** pada bagian terkait dalam rangkuman.

Keterangan:

- **[MODIFIKASI]**: Bagian yang mengalami pengembangan, penambahan penjelasan, perbaikan, atau penyesuaian.
- Bagian tanpa tanda: Bagian yang dipertahankan karena sudah sesuai dengan materi dan tidak memerlukan perubahan substantif.

---

## F. KESIMPULAN

Berdasarkan materi pertemuan 7, dapat dipahami bahwa Cloud Computing merupakan model penyediaan sumber daya komputasi melalui jaringan yang memungkinkan pengguna memanfaatkan server, penyimpanan, jaringan, dan aplikasi sesuai kebutuhan tanpa harus memiliki seluruh infrastruktur fisik sendiri.

Cloud Computing memiliki enam karakteristik utama, yaitu on-demand self-service, broad network access, resource pooling, rapid elasticity, measured service, dan multitenancy. Selain itu, terdapat tiga model layanan utama, yaitu SaaS, PaaS, dan IaaS, serta empat model deployment berupa public, private, hybrid, dan community cloud.

Dalam penerapannya, scalability dan redundancy menjadi dua konsep penting. Scalability membantu sistem menyesuaikan kapasitas terhadap perubahan beban kerja, sedangkan redundancy membantu menjaga ketersediaan data dan layanan ketika terjadi kegagalan pada komponen tertentu.

Virtualisasi dan teknologi container juga mempunyai peran besar dalam pengembangan cloud. Virtualisasi memungkinkan satu perangkat keras menjalankan beberapa lingkungan komputasi, sedangkan container membantu mengemas aplikasi beserta dependensinya agar dapat berjalan secara konsisten.

Selanjutnya, konsep Serverless dan Cloud Native Application menunjukkan perkembangan pendekatan pembangunan aplikasi berbasis cloud. Penggunaan microservices, containers, DevOps, dan CI/CD membantu aplikasi menjadi lebih fleksibel, mudah dikembangkan, serta mampu menyesuaikan kebutuhan sistem.

Menurut pemahaman saya, materi ini penting dalam bidang Informatika karena memberikan dasar untuk memahami bagaimana aplikasi modern dibangun dan dijalankan menggunakan infrastruktur terdistribusi. Konsep-konsep tersebut juga menjadi bekal untuk mempelajari pengembangan aplikasi berbasis cloud, pengelolaan server, database terdistribusi, dan teknologi container.

---

## G. DAFTAR REFERENSI

1. Dr. Bambang Purnomosidi D. P., Fakultas Teknologi Informasi, Universitas Teknologi Digital Indonesia. *Materi Perkuliahan Teori Sistem Terdistribusi dan Terdesentralisasi: Cloud Computing (Pertemuan 07).* File: `07--cloud-computing.pdf`.

2. National Institute of Standards and Technology (NIST). *The NIST Definition of Cloud Computing.* https://doi.org/10.6028/NIST.SP.800-145

3. Cloud Native Computing Foundation (CNCF). *Cloud Native Definition.* https://github.com/cncf/toc/blob/master/DEFINITION.md

4. Nagarro. *Cloud Native Development: Choosing the Right Architecture.* https://www.nagarro.com/en/blog/cloud-native-development-choosing-right-architecture

---

**Dokumentasi Tugas**

- Repository: [disdec-teori](https://github.com/hendfirmsh/disdec-teori)
- Direktori: `07/`
- File: `README.md`

---
