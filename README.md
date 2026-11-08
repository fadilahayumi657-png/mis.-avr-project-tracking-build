- Nama : SHERLY AYUMI FADILAH
- NIM : 2409020115
- Link demo : https://github.com/fadilahayumi657-png/mis.-avr-project-tracking-build.git


1. Perbedaan Image Tracking dan Face Tracking
Image Tracking berfokus pada pendeteksian dan pelacakan gambar datar dua dimensi (seperti poster, kartu, atau marker fisik) di dunia nyata. Sistem mendeteksi fitur visual seperti kontras, tepi, dan pola pada gambar tersebut untuk menempatkan objek virtual di atasnya.
Face Tracking berfokus secara khusus pada pendeteksian wajah manusia menggunakan titik-titik acuan wajah (facial landmarks). Sistem ini melacak bentuk, kontur, dan pergerakan wajah secara real-time agar objek virtual (seperti filter, kacamata, atau topeng) dapat menempel dan mengikuti ekspresi serta posisi kepala pengguna.

2. Faktor yang Paling Memengaruhi Kestabilan
Faktor utama yang paling memengaruhi kestabilan pelacakan adalah:
Pencahayaan: Pencahayaan yang terlalu gelap, terlalu terang, atau menghasilkan pantulan (glare) akan mengaburkan titik fitur (feature points) yang dibaca oleh kamera.
Kualitas Target: Target gambar yang memiliki banyak detail, kontras tinggi, dan tidak simetris jauh lebih stabil dibandingkan gambar yang polos atau berulang polanya.
Stabilitas Gerakan: Pergerakan kamera yang terlalu cepat dapat menyebabkan motion blur, membuat sistem kesulitan mempertahankan posisi objek virtual secara akurat.

3. Penanganan Target Hilang dalam Kode
Ketika target keluar dari jangkauan kamera atau terhalang, sistem akan kehilangan titik acuan (tracking lost), yang umumnya membuat objek virtual ikut menghilang dari layar.
Dalam kode pemrograman (seperti pada MindAR atau pustaka AR serupa), situasi ini ditangani menggunakan event listener seperti targetLost dan targetFound. Ketika targetLost dipicu, kode akan menjalankan perintah untuk menyembunyikan elemen 3D (visible = false), dan sebaliknya akan memunculkannya kembali saat targetFound aktif.

4. Penyebab Objek Virtual Bergeser Meskipun Kode dan Model Sama
Meskipun kode dan model 3D yang digunakan sama persis, objek virtual tetap bisa bergeser (jitter atau drift) karena faktor lingkungan fisik yang berbeda. Perbedaan sudut pandang kamera saat mengambil gambar, jarak perangkat ke target, perubahan bayangan pada permukaan target, atau resolusi kamera perangkat yang berbeda dapat memengaruhi cara algoritma mendeteksi ulang titik koordinat 3D, sehingga menimbulkan sedikit pergeseran posisi.

5. Batasan Pendekatan (MindAR vs Spatial Mapping)
Pendekatan seperti MindAR berbasis pada 2D image tracking dan tidak melakukan spatial mapping (pemetaan spasial lingkungan 3D). Artinya, sistem ini hanya mengenali gambar target datar yang telah didaftarkan dan tidak memiliki pemahaman tentang kedalaman ruangan, bentuk lantai, dinding, atau benda fisik lain di sekitar pengguna. Akibatnya, objek virtual tidak dapat berinteraksi secara fisik dengan dunia nyata, seperti terhalang oleh objek fisik lain atau menapak secara nyata di atas lantai ruangan.