# Mendeteksi-Serangan-DDoS-Web-serangan-denial-of-service-teknik-deteksi-dan-strategi-perlindungan.

# Perkenalan
Serangan Denial-of-Service ( DoS ) dapat mengambil banyak bentuk, tetapi tujuan utamanya adalah untuk mengganggu atau sepenuhnya memblokir akses ke situs web atau layanan web. Di ruangan ini, Anda akan menjelajahi bagaimana serangan DoS dan DDoS menargetkan lapisan aplikasi, teknik di baliknya, dan bagaimana Anda, sebagai pihak yang bertahan, dapat mendeteksi dan mengurangi ancaman umum ini.

Tujuan
Pelajari cara kerja serangan penolakan layanan (denial-of-service).
Pahami motif penyerang di balik serangan yang mengganggu.
Lihat bagaimana log web dapat membantu Anda mengungkap tanda-tanda serangan DoS dan DDoS web.
Dapatkan praktik menganalisis serangan penolakan layanan melalui analisis log.
Temukan teknik deteksi dan mitigasi yang dapat digunakan oleh para pembela.

# Serangan DoS dan DDoS
Pada intinya, serangan Denial-of-Service ( DoS ) bertujuan untuk membanjiri situs web atau aplikasi sehingga orang tidak dapat menggunakannya. Ketika ini terjadi, pelanggan tidak dapat masuk, berbelanja, atau mengakses layanan, dan bisnis kehilangan uang dan kepercayaan.

Pernahkah Anda mencoba mengunjungi situs web favorit Anda, hanya untuk melihatnya memuat tanpa henti atau memaksa Anda melalui tantangan CAPTCHA berulang kali? Situs tersebut mungkin sedang menghadapi serangan penolakan layanan (denial-of-service attack), di mana penyerang membanjirinya dengan lalu lintas yang berlebihan, memaksa pihak yang bertahan untuk berupaya keras menjaga ketersediaan situs.

Serangan DoS dapat dilancarkan terhadap berbagai lapisan sistem. Namun, di ruangan ini, kita akan fokus pada lapisan aplikasi (Lapisan 7) dari model OSI , di mana situs web dan aplikasi web sering menjadi sasaran.

Serangan Penolakan Layanan ( DoS )

<img width="760" height="220" alt="image" src="https://github.com/user-attachments/assets/2c974602-5b58-4dfd-b022-76fc106b11c9" />

Serangan DoS apa pun , baik skala kecil maupun besar, dianggap berhasil jika mencegah layanan web berfungsi sebagaimana mestinya. Mari kita mulai dengan melihat bagaimana serangan sederhana dan tertarget sekalipun dapat menyebabkan situs web menjadi tidak tersedia.

Bayangkan situs web Anda, situs e-commerce populer yang menjual suku cadang sepeda, memiliki formulir pencarian. Formulir ini menerima input pengguna, melakukan kueri ke basis data, dan mengembalikan hasil yang sesuai. Jika aplikasi gagal memvalidasi atau menangani input dengan benar, penyerang dapat mengirimkan data yang tidak terduga atau salah format yang menyebabkan aplikasi macet atau mengalami crash saat memproses permintaan. Dengan cara ini, kotak pencarian sederhana dapat disalahgunakan untuk melancarkan serangan penolakan layanan (DoS). Penyerang juga dapat membanjiri formulir pencarian yang sama dengan banyak permintaan atau bahkan satu permintaan besar untuk menyebabkan gangguan DoS jika formulir tersebut tidak memfilter atau memvalidasi pencarian dengan benar.

Serangan Penolakan Layanan Terdistribusi ( DDoS )

<img width="821" height="221" alt="image" src="https://github.com/user-attachments/assets/4b87622c-eca7-4a62-8b5d-51cf59cc9bf2" />

Keterbatasan serangan DoS dasar adalah bahwa serangan ini bergantung pada satu mesin dan satu koneksi internet. Meskipun satu komputer dapat menghasilkan banyak permintaan, dampaknya dibatasi oleh CPU , memori, bandwidth, dan jaringannya.

Untuk meningkatkan skala serangan, penyerang beralih ke serangan Distributed Denial-of-Service ( DDoS ) dan menggunakan botnet, yaitu pasukan perangkat yang telah disusupi dan berada di bawah kendali mereka. Komputer, perangkat IoT , dan bahkan server sering kali terinfeksi malware dan dikendalikan secara diam-diam oleh penyerang. Ketika diperintahkan, bot akan membanjiri situs web atau aplikasi web target dengan lalu lintas, sehingga jauh lebih efektif daripada yang dapat dilakukan oleh satu mesin saja.

Sekarang bayangkan situs web suku cadang sepeda Anda. Situs ini populer dan menangani lalu lintas yang stabil setiap hari, tetapi tidak dirancang untuk menahan jutaan permintaan dalam waktu singkat. Seorang penyerang menginstruksikan botnet mereka untuk menyerbu situs Anda, dan lonjakan lalu lintas yang tiba-tiba dengan cepat menghabiskan sumber daya Anda, menyebabkan situs web tersebut down.

Jenis-jenis Serangan Penolakan Layanan (Denial-of-Service)
Mari kita periksa berbagai jenis serangan penolakan layanan (denial-of-service). Serangan ini dapat dilakukan oleh penyerang tunggal ( DoS ) atau didistribusikan melalui botnet (DDoS)

Jenis Serangan DoS	Keterangan
Slowloris	Mengirim banyak permintaan HTTP parsial yang akan membebani sumber daya server.
Banjir HTTP	Mengirimkan sejumlah besar permintaan HTTP untuk membanjiri server.
Melewati Cache	Melewati server tepi CDN dan memaksa server asal untuk merespons.
Kueri Berukuran Besar	Memaksa server untuk memproses permintaan besar yang membutuhkan banyak sumber daya.
Penyalahgunaan Login/Formulir	Membebani logika otentikasi dengan upaya login atau pengaturan ulang kata sandi
Penyalahgunaan Validasi Input yang Salah	Memanfaatkan penanganan input yang dirancang dengan buruk.
Jawablah pertanyaan-pertanyaan di bawah ini.
Jenis serangan apa yang bergantung pada terganggunya ketersediaan layanan web?

JAWABAN : Denial-of-Service


Apa sebutan untuk jaringan mesin yang diretas yang digunakan penyerang untuk melancarkan serangan DDoS?

JAWABAN :  Botnet

# MOTIF SERANGAN 
<img width="501" height="282" alt="image" src="https://github.com/user-attachments/assets/5f5b18e0-6fe4-4bd2-ab6c-275d649c74cd" />


Setelah mempelajari bagaimana penyerang melancarkan serangan DoS dan DDoS , mari kita lihat mengapa mereka melakukannya. Sekilas, gangguan layanan web yang singkat mungkin tampak sepele, tetapi bagi organisasi yang bergantung pada ketersediaan yang konstan, konsekuensinya bisa sangat serius, menyebabkan hilangnya pendapatan, pengguna yang frustrasi, dan kerusakan reputasi.

Kemungkinan Motif Serangan

Motif	Keterangan	Contoh Skenario
Kerugian Finansial	Mengganggu layanan untuk menghentikan atau mengurangi penjualan dan pendapatan.	Membanjiri situs web e-commerce selama puncak penjualan liburan.
Pemerasan	Tuntut pembayaran untuk menghentikan serangan yang sedang berlangsung.	Mengancam bank dengan serangan DDoS untuk meminta tebusan.
Aktivisme peretasan	Aksi unjuk rasa untuk tujuan sosial atau politik.	Menyerang situs web pemerintah selama musim pemilihan
Selingan	Alihkan perhatian para pemain bertahan sementara serangan lain terjadi.	Melancarkan serangan DDoS sambil menyerang infrastruktur lain.
Kompetisi	Mengganggu layanan pesaing untuk meningkatkan biaya mereka atau mendapatkan pangsa pasar.	Seorang pesaing melancarkan serangan DDoS selama peluncuran produk.
Penolakan Dompet	Memaksa korban untuk menanggung biaya penggunaan layanan.	Penyerang berulang kali mengakses data AWS S3 , sehingga menimbulkan biaya per permintaan.
Kerusakan Reputasi	Menyebabkan pelanggan kehilangan kepercayaan pada perusahaan.	Server game mengalami gangguan pada hari peluncuran.
Catatan: Ini bukan daftar lengkap motif penyerang. Tergantung pada sumber daya dan target mereka, penyerang dapat menggabungkan beberapa tujuan atau mengejar tujuan lainnya.

Di Alam Liar
Pada malam Tahun Baru 2015, BBC menjadi korban serangan DDoS yang menyebabkan situs webnya offline. Para pembaca situs tersebut tidak dapat mengakses artikel selama beberapa jam karena permintaan mereka mengalami timeout atau menampilkan pesan kesalahan internal. Kelompok yang mengaku bertanggung jawab, New World Hacking , mengatakan bahwa mereka melakukan serangan DDoS hanya sebagai uji kemampuan mereka.

Pada tahun 2023, Microsoft mengalami serangan DDoS skala besar lapisan 7 yang menyebabkan gangguan pada Azure, OneDrive, dan Outlook. Kelompok aktivis peretas Anonymous Sudan mengaku bertanggung jawab. Para penyerang menggunakan teknik seperti HTTP flooding dan Slowloris untuk membanjiri server web, menyebabkan gangguan besar bagi pelanggan Microsoft di seluruh dunia.

Jawablah pertanyaan-pertanyaan di bawah ini.
Motif penyerang apa yang bertujuan membuat pelanggan kehilangan kepercayaan pada suatu perusahaan?

JAWABAN : Reputational Damage


Motif apa yang paling mungkin mendorong serangan DDoS tahun 2023 terhadap Microsoft?

JAWABAN : Hacktivism

# Analisis Log
Log server web merupakan sumber bukti yang berharga saat menyelidiki serangan penolakan layanan (denial-of-service/DoS). Setiap layanan web utama, baik Apache , NGINX, atau Microsoft IIS, mencatat permintaan web dalam format log yang agak terstandarisasi. Dengan memeriksa log ini, analis dan penanggung jawab dapat mengungkap pola yang membantu membedakan antara lalu lintas pengguna normal dan aktivitas berbahaya. Dalam tugas ini, kita akan melihat beberapa indikator utama dari potensi serangan DoS dan DDoS , dan menyoroti kekuatan dan keterbatasan mengandalkan log untuk deteksi.

Dari tugas-tugas sebelumnya, kita tahu bahwa serangan penolakan layanan (denial-of-service) sering kali mengandalkan pengiriman sejumlah besar permintaan HTTP ke target, tetapi juga dapat memanfaatkan permintaan web yang dirancang khusus secara individual untuk menghentikan suatu layanan.

Perhatikan indikator-indikator di bawah ini:

Indikator	Contoh	Keterangan
Tingkat Permintaan Tinggi	10.10.10.100→ 1000GET /login	Halaman yang membutuhkan banyak sumber daya seperti ini  /loginakan dibanjiri permintaan yang dapat membebani proses otentikasi. Halaman login adalah target umum karena setiap permintaan dapat memicu pemeriksaan kata sandi dan kueri basis data.
Agen Pengguna Aneh	curl/7.6.88→ /indexberulang kali	Penyerang memalsukan User-Agent yang usang atau tidak biasa untuk menyamarkan diri atau melewati filter. Mendeteksi lalu lintas dengan alat seperti curlatau Python-urllib/3.x, misalnya, dapat menjadi tanda bahaya untuk serangan otomatis.
Anomali Geografis	Asal usul alamat IP tersebar di seluruh dunia	Lalu lintas yang sah biasanya berasal dari beberapa wilayah tempat pengguna sebenarnya berada. Botnet yang tersebar secara global dapat menggunakan alamat IP dari seluruh dunia.
Stempel Waktu Ledakan	50 permintaan dalam 1 detik →/search	Lonjakan permintaan yang tiba-tiba terjadi dalam detik yang sama menciptakan pola lalu lintas yang tidak wajar yang mengindikasikan adanya otomatisasi.
Kesalahan Server ( 5xx )	Peningkatan 503 Service Unavailablekesalahan yang signifikan	Lonjakan respons kesalahan server secara tiba-tiba ( 500- 511) menunjukkan bahwa sumber daya telah mencapai batas maksimal dan layanan sedang kesulitan menangani lalu lintas serangan.
Penyalahgunaan Logika	GET /products?limit=999999	Para penyerang membuat kueri yang membebani server, memaksa server untuk memuat sejumlah besar informasi dan memperlambatnya bagi semua orang.
Analis harus mencari berbagai sinyal berlapis yang membentuk gambaran upaya DDoS. Misalnya, bayangkan seorang penyerang mengendalikan botnet global yang ditujukan ke satu situs. Anda mungkin melihat permintaan dari berbagai alamat IP di berbagai wilayah geografis. Permintaan ini dapat menyerang beberapa endpoint yang membutuhkan banyak sumber daya dengan string User-Agent yang sama atau berbagai string agar tampak lebih sah. Memelihara daftar pantauan indikator umum yang perlu diwaspadai dapat menjadi alat yang berharga dalam persenjataan seorang analis.

Sumber Daya yang Ditargetkan
Jika penyerang bertujuan untuk mengganggu layanan web seperti yang telah kita bahas, mereka kemungkinan akan fokus pada titik akhir yang mengonsumsi sumber daya server paling banyak per permintaan atau yang paling penting untuk menjaga fungsionalitas situs. Halaman seperti /loginformulir pencarian adalah target utama karena setiap permintaan memaksa server untuk melakukan kueri ke basis data, memvalidasi input, dan mengembalikan hasilnya. Hal ini membuat permintaan jauh lebih mahal untuk diproses daripada konten statis seperti halaman produk atau gambar. 

Titik akhir yang umum ditargetkan dan alasannya: 

/login- melibatkan proses otentikasi 
/search- memerlukan kueri basis data yang kompleks
/apiTitik akhir - penting untuk pengiriman konten dinamis
/registeratau /signup- memerlukan penulisan dan validasi basis data
/contactatau /feedback- memerlukan entri basis data dan dapat memicu notifikasi email.
/cartatau /checkout- memerlukan manajemen sesi, pengecekan inventaris, dan pemrosesan pembayaran
Contoh Log
Mari kita periksa contoh log akses ringkas untuk melihat bagaimana serangan DoS mungkin muncul dalam skenario pasca-insiden. 

Lalu Lintas Pengguna Normal - Setiap beberapa detik, pengguna meminta halaman dan menerima respons seperti yang diharapkan.
Serangan DoS - Dimulai pada 10:01:10, Anda dapat melihat alamat IP 203.0.113.55mulai mengirimkan GETpermintaan berulang ke/login.php
Server Web Sedang Tidak Aktif - Pengguna meminta halaman dan menerima 503respons yang menunjukkan bahwa layanan tidak tersedia.
Cuplikan log ini sangat ringkas, dan serangan DoS atau DDoS dapat menyebabkan ratusan atau ribuan permintaan membanjiri log secara bersamaan.

<img width="690" height="330" alt="image" src="https://github.com/user-attachments/assets/b55cab96-0263-4f0b-8e76-c21198c2cb88" />

HANDS ON
Situs web suku cadang sepeda Anda telah mengalami serangan penolakan layanan (denial-of-service). Buka access.logfile di Desktop pengguna untuk memulai penyelidikan Anda. Log tersebut mencakup campuran lalu lintas normal yang dihasilkan pengguna dan lalu lintas penyerang. Saat Anda meneliti log, perhatikan permintaan berulang ke halaman yang sama dan ingat indikator yang telah Anda pelajari dalam tugas ini. Semoga berhasil!

<img width="378" height="329" alt="image" src="https://github.com/user-attachments/assets/52713cd2-f1fe-43a6-9ddb-1ce1bbd35fce" />

Jawablah pertanyaan-pertanyaan di bawah ini.
Berapakah alamat IP penyerang?

masuk terminal :  cd Desktop/ 
karena file ada di desktop 
kita pakai perintah vim untuk membuka file / vim namafile membuka 
lanjut ketik vim access.log - enter
<img width="1360" height="629" alt="image" src="https://github.com/user-attachments/assets/0e9d7691-77c7-4d6e-a177-34ed670dac6f" />


JAWABAN : 203.12.23.195

Jawaban yang Benar
Halaman mana yang berulang kali menjadi target permintaan penyerang?
cara sama seperti di atas dan kali ini lihat di bagian /login
<img width="1360" height="629" alt="image" src="https://github.com/user-attachments/assets/4ce3e2d5-04f7-4718-858e-c296052c7cae" />

JAWABAN : /login

Jawaban yang Benar
Setelah serangan tersebut, kode kesalahan apa yang diterima oleh pengguna yang sah?
cara sama seperti yang di atas 
lihat di bagian isi di baris setelah server 200 yaitu 503

203.12.23.195 - - [31/Aug/2025:01:59:08 +0000] "GET /login HTTP/1.1" 200 519 "-" "curl/7.88.1"
203.12.23.195 - - [31/Aug/2025:01:59:08 +0000] "GET /login HTTP/1.1" 503 267 "-" "curl/7.88.1"
203.12.23.195 - - [31/Aug/2025:01:59:08 +0000] "GET /login HTTP/1.1" 503 267 "-" "curl/7.88.1"
203.12.23.195 - - [31/Aug/2025:01:59:08 +0000] "GET /login HTTP/1.1" 503 267 "-" "curl/7.88.1"
203.12.23.195 - - [31/Aug/2025:01:59:08 +0000] "GET /login HTTP/1.1" 503 267 "-" "curl/7.88.1"
203.12.23.195 - - [31/Aug/2025:01:59:08 +0000] "GET /login HTTP/1.1" 503 267 "-" "curl/7.88.1"
203.12.23.195 - - [31/Aug/2025:01:59:08 +0000] "GET /login HTTP/1.1" 503 267 "-" "curl/7.88.1"
203.12.23.195 - - [31/Aug/2025:01:59:08 +0000] "GET /login HTTP/1.1" 503 267 "-" "curl/7.88.1"
203.12.23.195 - - [31/Aug/2025:01:59:08 +0000] "GET /login HTTP/1.1" 503 267 "-" "curl/7.88.1"
203.12.23.195 - - [31/Aug/2025:01:59:08 +0000] "GET /login HTTP/1.1" 503 267 "-" "curl/7.88.1"
203.12.23.195 - - [31/Aug/2025:01:59:08 +0000] "GET /login HTTP/1.1" 503 267 "-" "curl/7.88.1"
203.12.23.195 - - [31/Aug/2025:01:59:08 +0000] "GET /login HTTP/1.1" 503 267 "-" "curl/7.88.1"

JAWABAN : 503

# Memanfaatkan SIEM
Platform Security Information and Event Management ( SIEM ) membuat analisis log jauh lebih efisien dengan menyediakan kemampuan untuk menggabungkan beberapa sumber log dan melakukan kueri untuk bidang yang berguna. Alih-alih menelusuri entri mentah yang tak berujung dalam file log, Anda dapat memfilter dan mengurutkan log berdasarkan alamat IP, agen pengguna, atau kode respons. Kemampuan ini membuat identifikasi pola dalam lalu lintas jauh lebih mudah.

Pada tangkapan layar di bawah ini, Anda dapat melihat grafik waktu yang dibuat di Splunk berdasarkan semua permintaan ke server selama periode sepuluh menit.

Permintaan Pengguna Normal - Beberapa permintaan ke berbagai halaman setiap menit.
Serangan DoS - 1.000 permintaan/login.phpdalam jangka waktu satu menit
Halaman yang Diminta
<img width="520" height="174" alt="image" src="https://github.com/user-attachments/assets/bde64232-5d1a-4911-a6b9-2946e1f56c87" />

Dengan meninjau permintaan yang sama tetapi memfilter berdasarkan kolom agen pengguna ( useragent) dan alamat IP ( clientip), Anda dapat melihat detail lebih lanjut tentang dari mana permintaan tersebut berasal.

<img width="520" height="232" alt="image" src="https://github.com/user-attachments/assets/18296c79-88f9-4129-a38b-513028b60b16" />

HANDS ON
Kali ini, situs web Anda diduga mengalami serangan DDoS. Anda akan menggunakan Splunk untuk menyelidiki apa yang terjadi!

Buka instance Splunk menggunakan pintasan di Desktop, atau akses langsung dihttp://MACHINE_IP:8000

Selama latihan ini, Anda akan menganalisis log akses web yang dikumpulkan selama periode dugaan serangan. Log ini berisi campuran lalu lintas pengguna normal dan permintaan yang berpotensi berbahaya. Untuk memulai, buka aplikasi Pencarian & Pelaporan di Splunk dan jalankan pencarian di indeks utama: index="main". Di sisi kiri GUI , Anda akan melihat kolom-kolom yang telah diekstrak dari file log. Ini akan sangat berguna saat Anda melakukan investigasi.

Jawablah pertanyaan-pertanyaan di bawah ini.
Apa yang paling sering diminta uri?

buka splunk ketik di pencarian : index="main" ini akan menapilkan semua event peristiwa 
ketik pencarian : 
index="main" 
| stats count AS request BY uri 
| sort - request

index="main"
Menentukan sumber data log yang akan dianalisis. 
| stats count AS request BY uri
“Hitung berapa kali setiap URI diakses, lalu tampilkan jumlahnya sebagai request”
| sort - request
Mengurutkan hasil dari yang PALING SERING diakses.

<img width="1364" height="678" alt="image" src="https://github.com/user-attachments/assets/53af0f6d-d57e-45fb-bcc4-1078ad0ae565" />



jawaban : /search


Manakah clientipyang mengajukan permintaan terbanyak ke target uri?

ketik di pencarian :  
index="main" uri="/search"
| top clientip

penjelasan
index="main"  Mengambil semua log event dari index main
uri="/search" “Ambil semua event log di index main yang mengakses endpoint /search”
| top clientip  Tampilkan IP yang paling sering mengakses /search


dan muncul hasilnya 

jawaban : 203.0.113.7



Berapa banyak alamat IP yang menjadi bagian dari botnet yang menyerang situs web Anda?

60

Jawaban yang Benar
Manakah useragentyang paling sering digunakan oleh lalu lintas penyerang?

Java/1.8.0_181

Jawaban yang Benar

Gunakan timechartperintah tersebut untuk memvisualisasikan permintaan.
Berapa jumlah permintaan puncak per detik selama serangan?

207

Jawaban yang Benar

Pihak mana yang sah (tidak menyerang) clientipyang menerima status respons pertama 503setelah serangan?

10.10.0.27

# PERTAHANAN /DEFENEDSE
Penyerang terus-menerus mencari titik lemah untuk dieksploitasi, tetapi pihak bertahan memiliki berbagai alat dan metode untuk menjaga sistem tetap tangguh. Dalam tugas ini, kita akan meneliti strategi pencegahan dan mitigasi yang tersedia untuk memastikan situs web dan aplikasi web kita terlindungi semaksimal mungkin dari serangan penolakan layanan (denial-of-service).

Pertahanan Tingkat Aplikasi
Praktik Pengembangan yang Aman

Situs yang aman dimulai dengan kode yang aman. Kolom pencarian dan formulir harus memvalidasi input agar tidak dapat disalahgunakan. Bayangkan formulir pencarian seperti pustakawan yang mencari buku berdasarkan permintaan. Jika pustakawan memiliki aturan yang jelas, seperti "hanya cari judul di bawah 50 karakter", mereka dapat merespons dengan cepat. Tanpa aturan yang jelas, seseorang dapat meminta pustakawan untuk mencari judul yang terlalu panjang atau aneh dengan karakter khusus, yang akan memperlambat mereka dan menunda permintaan orang lain. Dengan cara yang sama, aplikasi web membutuhkan validasi input untuk mencegah penyerang mengirimkan kueri khusus yang bertujuan untuk membebani sistem.

Tantangan

Salah satu cara untuk menghentikan lalu lintas otomatis adalah dengan memberikan tantangan sebelum memberikan akses. Ini bisa berupa CAPTCHA, di mana pengguna memecahkan teka-teki, seperti mengklik gambar atau mencentang kotak. Bagi manusia, ini adalah langkah kecil, tetapi bagi bot, hal ini dapat memblokir atau memperlambat serangan.

Situs web juga dapat menggunakan tantangan JavaScript, yang berjalan diam-diam di latar belakang untuk memastikan apakah pengunjung adalah pengguna sungguhan atau lalu lintas otomatis. Pengguna yang sah biasanya tidak menyadarinya, tetapi alat otomatis dan botnet sering gagal, sehingga tantangan ini menjadi filter yang efektif terhadap lalu lintas berbahaya.

<img width="616" height="164" alt="image" src="https://github.com/user-attachments/assets/7c763154-a9c1-4fe3-9e04-304888e7bfc0" />

Pertahanan Jaringan dan Infrastruktur
Jaringan Pengiriman Konten (CDN)

CDN membantu mengelola beban server dengan melakukan caching dan menyajikan konten dari server edge yang paling dekat dengan pengguna. Hal ini mengurangi latensi dan memungkinkan server asal hanya menangani sebagian kecil permintaan, sementara CDN melayani sebagian besar permintaan. Akibatnya, CDN memikul sebagian besar beban dalam mitigasi serangan DDoS . Mereka juga menyediakan penyeimbangan beban untuk mendistribusikan lalu lintas di seluruh server, memastikan tidak ada satu server pun yang kelebihan beban dan mengalihkan permintaan jika salah satu server tidak tersedia.

Berikut contoh serangan DDoS sebesar 16 TB yang ditampilkan di dasbor Cloudflare CDN.

Total bandwidth selama periode 30 hari - Ini menunjukkan seluruh volume lalu lintas selama 30 hari terakhir. Jika situs Anda biasanya menerima beberapa ratus gigabyte per bulan, tiba-tiba melihat 16 TB menunjukkan ada sesuatu yang tidak normal.
Total bandwidth yang di-cache oleh server edge CDN - Ini menunjukkan seberapa banyak lalu lintas yang berhasil dikirimkan oleh server edge CDN. Hampir semua bandwidth yang di-cache menunjukkan bahwa Cloudflare menyerap lalu lintas serangan sebelum dapat membanjiri backend.
Lonjakan trafik akibat serangan DDoS - Lonjakan pada grafik merupakan ciri khas serangan DDoS . Tanpa CDN, banjir permintaan akan langsung mengenai server asal.

<img width="520" height="224" alt="image" src="https://github.com/user-attachments/assets/1435ef67-8b34-4847-bee2-de376abe21b7" />
Selain menyerap lalu lintas, CDN juga memberikan visibilitas yang kuat kepada analis, termasuk visualisasi dan diagnostik lalu lintas situs web yang bermanfaat. Hal ini memungkinkan Anda untuk dengan cepat menguraikan permintaan berdasarkan lokasi geografis, volume, dan pola sumber, membantu membedakan lalu lintas berbahaya dari pengguna yang sah.

<img width="520" height="248" alt="image" src="https://github.com/user-attachments/assets/0ade3adb-6c75-4a8e-ad28-8293d69d8294" />

Firewall Aplikasi Web (WAF)

CDN biasanya mengintegrasikan WAF dalam upaya melindungi server pelanggan mereka. WAF memeriksa lalu lintas masuk dan kemudian mengizinkan, menantang, atau memblokir permintaan. WAF bekerja berdasarkan aturan yang mengintegrasikan indikator serangan yang diketahui dan intelijen ancaman. Solusi WAF modern sudah sangat baik dalam mengurangi serangan DoS dan DDoS karena mereka tahu apa yang harus diwaspadai. Aturan khusus juga dapat dikembangkan untuk membantu dalam mempertahankan diri dari ancaman yang ditargetkan.

Sebagai contoh, Anda dapat menerapkan aturan firewall pembatas laju yang membatasi permintaan hingga /login.phplima kali per menit. Jika IP asal meminta halaman tersebut lebih dari lima kali, IP tersebut akan diblokir untuk melakukan permintaan di masa mendatang selama jangka waktu tertentu atau diberikan tantangan untuk membuktikan bahwa itu adalah permintaan yang dibuat oleh manusia. 

<img width="1357" height="240" alt="image" src="https://github.com/user-attachments/assets/e15523dc-6cbe-47e1-920f-92ad540bdef7" />

Mitigasi Skala Besar
Solusi pertahanan modern dapat memblokir serangan penolakan layanan (denial-of-service) dan juga memanfaatkan infrastruktur terdistribusi yang luas untuk menyerap dan menyeimbangkan volume lalu lintas yang besar. Pada tahun 2023, Google berhasil mengatasi serangan DDoS skala besar yang mencapai puncaknya pada 398 juta permintaan per detik. Cloudflare mengklaim telah mengatasi serangan DDoS terbesar yang pernah tercatat, yang mencapai puncaknya pada 11,5 Tbps dan hanya berlangsung selama 35 detik. Contoh-contoh ini menunjukkan bagaimana penyedia layanan menggunakan jaringan global dan penyaringan lalu lintas untuk mencegah bahkan serangan terbesar sekalipun agar tidak mengganggu layanan penting.

Melewati Langkah-Langkah Keamanan
Meskipun CDN, caching, dan WAF memberikan perlindungan yang kuat, penyerang sering mencoba untuk melewati pertahanan ini. Salah satu tekniknya adalah menambahkan parameter kueri acak. CDN Anda mungkin menyajikan URL yang di-cache di /products, tetapi jika penyerang menambahkan kueri dengan string acak seperti /products?a=abcd, CDN Anda tidak dapat menyajikan halaman yang di-cache, dan server asal terpaksa merespons. Demikian pula, mengubah agen pengguna, memalsukan halaman perujuk, atau meluncurkan permintaan dari berbagai wilayah geografis dapat membantu penyerang menghindari aturan pemfilteran WAF.

Jawablah pertanyaan-pertanyaan di bawah ini.
Jenis tantangan keamanan apa yang memblokir bot dengan meminta pengguna untuk memecahkan teka-teki sederhana?

CAPTCHA

Jawaban yang Benar
Fitur CDN manakah yang mendistribusikan lalu lintas ke beberapa server untuk mencegah kelebihan beban?

Load-balancing

# Kesimpulan
Di ruangan ini, Anda telah mempelajari berbagai jenis serangan Denial-of-Service (DoS) , cara kerjanya, dan motif di baliknya, yang didukung oleh beberapa contoh dunia nyata. Anda berlatih mengidentifikasi aktivitas DoS dan DDoS dalam log server web dengan menganalisis indikator umum dan mempelajari bagaimana platform SIEM membantu analis menyelidiki dan mengelola volume lalu lintas yang besar. Melalui latihan Splunk langsung , Anda menemukan bukti serangan DDoS . Terakhir, Anda mempelajari bagaimana CDN dan WAF dapat membantu melindungi situs web dan aplikasi dari serangan ini.
