# Capstone3

**Business Problem Understanding :**


Asuransi perjalanan adalah asuransi yang melindungi kita jika terjadi masalah selama perjalanan, seperti perjalanan dibatalkan atau kecelakaan. Perusahaan akan menentukan biaya premi asuransi setiap individu berdasarkan berbagai faktor seperti perlindungan apa saja yang diinginkan, durasi perjalanan, dan faktor lainnya.

Tantangan yang dihadapi oleh perusahaan adalah alokasi dana yang akurat. Terkadang, dana yang dialokasikan tidak akurat sehingga ketersediaan dana menjadi tidak memadai saat menghadapi klaim. Alhasil, perusahaan tidak siap menanggapi nasabah yang melakukan klaim, yang pada akhirnya dapat mengakibatkan kerugian.

Untuk mengatasi tantangan ini, perusahaan berkeinginan untuk memprediksi lebih dini pemegang polis mana yang akan melakukan klaim asuransi.

Target:

0, Tidak Mengklaim asuransi <br>
1, Mengklaim asuransi

### **Problem Statement** 

Perusahaan ingin menyiapkan dana secara akurat agar siap untuk menanggani nasabah yang berisiko melakukan 'Klaim' asuransi. Perusahaan dapat mengalokasikan dana cadangan secara proaktif untuk menutupi potensi klaim, terutama dari pemegang polis berisiko tinggi. 

### **Goals**
Perusahaan ingin memprediksi 'Risiko Klaim Asuransi' untuk pemegang polis baru dengan menggunakan beberapa atribut. Analisis ini akan memanfaatkan data historis yang mencakup atribut seperti agency name, agency type, distribution channel, product name, gender, duration of travel, destination, net sales, commission, age, dan prior claim history. Tujuannya adalah untuk mengoptimalkan alokasi keuangan dan memastikan cadangan yang tepat untuk klaim yang berpotensial.

### **Analytical Approach**
Sebelum membuat model machine learning untuk memprediksi 'Risiko Klaim Asuransi', kita akan mempelajari atribut mana yang berkorelasi dengan variabel target kita 'Klaim'. Memilih atribut atau fitur yang tepat akan mengoptimalkan model untuk memprediksi target 'Y' kita seakurat mungkin.

### **Metric Evaluation**
- Kesalahan Tipe 1 : False Positive (diprediksi mengajukan klaim (1) namun pada kenyataannya tidak mengajukan klaim (0))
    - Konsekuensi : Mengalokasikan dana kepada para nasabah yang terprediksi akan melakukan klaim. Kemungkinan terjadinya dana berlebih karena ternyata dana tidak terpakai untuk para nasabah tersebut yang nyatanya tidak melakukan klaim.
    
- Kesalahan Tipe 2 : False Negative (diprediksi tidak mengajukan klaim (0) padahal pada kenyataannya mengajukan klaim (1))
    - Konsekuensi : Kekurangan dana yang membuat perusahaan tidak siap menanggapi para nasabah yang terprediksi tidak melakukan klaim padahal nyatanya melakukan klaim. Kemungkinan perusahaan merugi dan kehilangan kepercayaan dari nasabah. 
    
Penilaian yang akan digunakan adalah recall karena yang menjadi fokus utama adalah meminimalisir kesalahan tipe 2 atau False Negative agar perusahaan tidak berisiko mengalami tantangan finansial ketika seseorang mengajukan klaim.

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
