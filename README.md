# Capstone3

**Business Problem Understanding :**


Asuransi perjalanan adalah asuransi yang melindungi kita jika terjadi masalah selama perjalanan, seperti perjalanan dibatalkan atau kecelakaan. Perusahaan akan menentukan biaya premi asuransi setiap individu berdasarkan berbagai faktor seperti perlindungan apa saja yang diinginkan, durasi perjalanan, dan faktor lainnya.

Tantangan yang dihadapi oleh perusahaan adalah alokasi dana yang akurat. Terkadang, dana yang dialokasikan tidak akurat sehingga ketersediaan dana menjadi tidak memadai saat menghadapi klaim. Alhasil, perusahaan tidak siap menanggapi nasabah yang melakukan klaim, yang pada akhirnya dapat mengakibatkan kerugian.

Untuk mengatasi tantangan ini, perusahaan berkeinginan untuk memprediksi lebih dini pemegang polis mana yang akan melakukan klaim asuransi.

Target:

0, Tidak Mengklaim asuransi <br>
1, Mengklaim asuransi

### **Problem Statement** 

Dalam menyetujui sebuah klaim, pihak perusahaan perlu melakukan investigasi secara menyeluruh agar terhindar dari penipuan dan kerugian. Semakin banyak pemegang polis maka proses ini akan menjadi semakin lama. Di sisi lain, pemegang polis juga memerlukan klaim asuransi mereka cepat ditanggapi jika masalah yang dihadapi sangat serius seperti kecelakaan. Setiap pihak memiliki kepentingannya masing-masing. Solusinya? "Mengetahui" pemegang polis akan klaim atau tidak. Jika tahu seseorang akan melakukan klaim maka perusahaan dapat menyiapkan dana secara akurat untuk nasabah tersebut. Selain itu perusahaan dapat meningkatkan efisiensi waktu untuk menyetujui suatu klaim. Nasabah juga akan lebih puas dengan pelayanan yang cepat, membangun kepercayaan mereka. 

Salah satu contoh krusialnya mengetahui lebih awal probabilitas seseorang akan melakukan klaim:
Terdapat badai yang menyebabkan semua penerbangan dibatalkan. Biaya yang besar ini perlu dipersiapkan dengan pertimbangan dalam waktu yang panjang. Dengan memprediksi lebih dahulu kemungkinan terjadi bencana seperti ini maka perusahaan akan lebih tanggap karena dapat merancangkan strategi pendanaan untuk kejadian buruk ini. 

Cuaca cenderung sulit untuk diketahui. Akan tetapi banyak faktor lainnya yang dapat menentukan seseorang akan melakukan klaim seperti durasi perjalanan mereka dan negara yang dituju. Dengan melakukan prediksi ini, kita dapat **membantu perusahaan** meningkatkan **efisiensi waktu dan dana** dan juga mengidentifikasi faktor apa yang berhubungan dengan meningkatnya risiko klaim seorang nasabah. 

### **Goals**
Perusahaan ingin memprediksi 'Risiko Klaim Asuransi' untuk pemegang polis baru dengan menggunakan beberapa atribut. Analisis ini akan memanfaatkan data historis yang mencakup atribut seperti agency name, agency type, distribution channel, product name, gender, duration of travel, destination, net sales, commission, age, dan prior claim history. Tujuannya adalah untuk mengoptimalkan alokasi keuangan dan memastikan cadangan yang tepat untuk klaim yang berpotensial.

### **Analytical Approach**

Sebelum membuat model machine learning untuk memprediksi 'Risiko Klaim Asuransi', kita akan mempelajari atribut mana yang berkorelasi dengan variabel target kita 'Klaim'. Memilih atribut atau fitur yang tepat akan mengoptimalkan model untuk memprediksi target 'Y' kita seakurat mungkin. Tahap ini akan dilakukan dengan pendekatan data understanding dan analisis pada data historical dari setiap pemegang polis dari berbagai agensi. Setelah itu, model akan dibuat dengan berbagai *classifier* karena kasus ini memprediksi antara 2 kelas. 

### **Metric Evaluation**

Kita akan menetapkan :
- Klaim sebagai **kelas Positive (1)**
- Tidak Klaim sebagai **kelas Negative (0)**
<br> Hal ini dikarenakan **pemegang polis yang melakukan klaim dinilai akan lebih berpengaruh** terharap perusahaan dibandingkan yang tidak melakukan klaim sebab pengajuan klaim memerlukan persiapan dana yang tepat agar perusahaan siap menanggulangi klaim dengan lebih cepat bagi pemegang polis dan tidak terdapat kekurangan dana. Maka kelas positif atau **perhatian utama** kita adalah pemegang polis yang melakukan **klaim**. 

Dalam metriks klasifikasi terdapat :
1. **True Positive (TP)** yaitu pemegang polis yang terprediksi (1) dan nyatanya melakukan klaim (1).
2. **True Negative (TN)** yaitu pemegang polis yang terprediksi (0) dan nyatanya tidak melakukan klaim (0).
3. **False Positive (FP)** / Kesalahan Tipe 1 yaitu diprediksi mengajukan klaim (1) namun pada kenyataannya tidak mengajukan klaim (0).
    - Konsekuensi adanya kesalahan ini : Mengalokasikan dana kepada para nasabah yang terprediksi akan melakukan klaim. Kemungkinan terjadinya dana berlebih karena ternyata dana tidak terpakai untuk para nasabah tersebut yang nyatanya tidak melakukan klaim.
4. **False Negative (FN)** / Kesalahan Tipe 2 yaitu diprediksi tidak mengajukan klaim (0) padahal pada kenyataannya mengajukan klaim (1).
    - Konsekuensi adanya kesalahan ini : Kekurangan dana yang membuat perusahaan tidak siap menanggapi para nasabah yang terprediksi tidak melakukan klaim padahal nyatanya melakukan klaim. **Kemungkinan perusahaan merugi dan kehilangan kepercayaan dari nasabah.** 
    
Penilaian yang akan digunakan adalah recall karena yang menjadi fokus utama adalah **meminimalisir kesalahan tipe 2 atau False Negative** agar perusahaan tidak berisiko mengalami tantangan finansial ketika seseorang mengajukan klaim.
Adapun recall adalah penilaian banyaknya jumlah kelas positif yang secara tepat terprediksi diantara seluruh kelas yang sebenar-benarnya positif. Recall ini menjadi pengukur kemampuan model machine learning untuk mendapatkan **sebanyak mungkin kelas Positive (1)** yang diidentifikasi secara benar atau dalam kasus ini yaitu pengaju klaim asuransi. 

Dengan membuat model prediksi dengan target metriks ini, perusahaan dapat terhindar dari kerugian finansial yang tak terduga sebagai bagian dari **manajemen risiko** dan **menanggapi klaim dengan lebih cepat** sehingga meningkatkan kredibilitas perusahaan di mata para pemegang polis. 


Informasi data <br>
|No |Nama Kolom        |Deskripsi                                           |
|---|------------------|----------------------------------------------------|
|1. |*Agency*            |Nama agensi                                          |
|2. |*Agency Type*         |Tipe agen asuransi perjalanan (Maskapai atau perjalanan)|
|3. |*Distribution Channel*|Metode distribusi ('online' melalui platform digital atau 'offline' dengan metode tradisional seperti telepon atau kantor fisik)|
|4. |*Product Name*     |Nama produk asuransi perjalanan                     |
|5. |*Gender*    |Jenis kelamin dari yang diasuransikan               |
|6. |*Duration*            |Durasi perjalanan                                   |
|7. |*Destination*         |Tujuan perjalanan                                   |
|8. |*Net Sales*  |Harga penjualan polis asuransi perjalanan          |
|9. |*Commission (in value)*|Komisi yang diterima untuk agen asuransi perjalanan|
|10.|*Age*           |Usia dari yang diasuransikan                        |
|11.|*Claim*             |Status klaim                                        |

Berdasarkan hasil classification report dari model ini, dapat disimpulkan bahwa model ini dapat memprediksi 81% dari seluruh nasabah yang tidak melakukan klaim dengan kesalahan prediksi sebanyak 19% (memprediksi false negative). Selain itu model ini dapat memprediksi 68% dari seluruh nasabah yang melakukan klaim dengan kesalahan prediksi sebanyak 32% (memprediksi false positif).  


Jika : <br>
Rata-rata biaya yang dibayarkan untuk asuransi perjalanan individu berumur 30 tahun adalah \$20 dimana biaya ini adalah 5% dari total biaya perjalanan mereka (\$400 per individu). Sebut saja semuanya mengambil produk Cancellation plan yang menjanjikan penggantian 50% dari total biaya perjalanan jika individu membatalkan perjalanan (\$200 per individu).  


Tanpa model machine learning jika nasabah sebanyak 1200 orang :<br>
1. Keuntungan = 1200 orang X 20= 24 ribu dollar
2. Alokasi dana = harus mempersiapkan $200 X 1200 orang = 240 ribu dollar dengan asumsi semua orang melakukan klaim. 

Dengan model machine learning dan ternyata diprediksi 1000 orang melakukan klaim dan 200 orang tidak melakukan klaim: 
1. Keuntungan = 1000 orang X 20= 20 ribu dollar
Dengan skor Recall kelas 0 yang didapatkan, dapat dilakukan:<br>
2. Alokasi dana = mengetahui 81% orang tidak akan melakukan klaim maka dana yang perlu dipersiapkan hanya 19% X 1000 orang X \$ 200 = 38 ribu dollar (mempersiapkan orang-orang yang nyatanya melakukan klaim (False negative)).
3. Sisa 200 - 38 ribu dollar = 162 ribu dollar + keuntungan 20 ribu dollar dapat dialokasikan ke investasi seperti reksadana dengan asumsi return 7% per tahun maka perusahaan dapat memperoleh 40 ribu dollar atau setara dengan mendapatkan 2000 nasabah baru tanpa mencari dalam kurun waktu 3 tahun.
Dengan skor Recall kelas 1 yang didapatkan, dapat dilakukan : <br>
4. Alokasi dana  = \$200 x 200 orang = 40 ribu dollar dimana terdapat kemungkinan 32 % dari dana ini yaitu dana berlebih sebanyak 12.8 ribu dollar (karena masuk ke dalam kelas False Positive, terprediksi klaim tapi nyatanya tidak). 


*30 tahun dipilih karena peak pengguna asuransi perjalanan pada dataset ini adalah pada 36 tahun.<br>
*Cancellation plan dipilih karena produk ini paling banyak diminati pada dataset ini.<br>
*20 dollar adalah besar biaya yang paling sering dikeluarkan pemegang polis. 

Sumber : https://www.forbes.com/advisor/travel-insurance/average-travel-insurance-cost/


## Recommendation
- Menambahkan fitur - fitur lain kedepannya jika ingin melakukan prediksi target y yaitu status klaim asuransi tapi yang bertujuan memberi biaya premi yang sesuai. Misalnya mengumpulkan data dari calon nasabah yaitu pernahkah calon nasabah memiliki asuransi atau jumlah asuransi yang sudah pernah dimiliki calon nasabah. Selain itu untuk tujuan seperti ini, fitur Net-Sales tidak dapat digunakan maka akan sebaiknya menggunakan model yang memiliki feature importance Net-Sales paling rendah (seperti pada Logistic Regression dengan randomundersampling).
- Menggumpulkan data orang-orang yang melakukan klaim asuransi (jika memungkinkan)
- Mencari tahu ordinal encoding untuk setiap produk asuransi dikarenakan setiap produk memiliki coverage yang berbeda-beda dan tentunya memiliki tingkatan tertentu, penting untuk memiliki domain knowledge terkait ini. 
- Melakukan explorasi model machine learning lainnya seperti SVM atau support Vector Machines.  
