# Suci-Nursania_2306046_latihan-workflow-AI
Jadi dari hasil eksplorasi notebook ini, dapat disimpulkan dengan beberapa langkah berikut:
1. Pertama-tama, kita mulai dengan membaca data penjualan yang disimpan dalam file CSV menggunakan pustaka pandas. Data ini berisi informasi tentang transaksi penjualan, seperti jumlah barang yang terjual, harga satuan, stok barang yang tersisa, dan tanggal transaksi. Setelah data dimuat, kita menampilkan beberapa baris pertama untuk memahami strukturnya.
   
2. Langkah berikutnya adalah membersihkan data. Kita memeriksa apakah ada nilai kosong atau data yang tidak lengkap menggunakan fungsi .isnull().sum(). Kalau ada data yang kosong, biasanya harus diputuskan apakah akan mengisi nilai yang hilang atau menghapus baris yang bermasalah. Setelah itu, kita mengonversi kolom tanggal ke dalam format datetime, supaya lebih mudah dalam analisis waktu.
   
3. Selain itu, kita juga menambahkan dua kolom baru:
Total Penjualan, dihitung dengan mengalikan jumlah barang terjual dengan harga satuan.
Keuntungan, yang dihitung berdasarkan asumsi tertentu tentang modal barang. Langkah-langkah ini penting karena sebelum melakukan analisis lebih lanjut atau menerapkan machine learning, kita harus memastikan bahwa data sudah bersih dan siap digunakan.

5. Implementasi Machine Learning dengan Decision Tree
Setelah data siap, kita mulai masuk ke bagian machine learning. Dalam notebook ini, kita menggunakan model Decision Tree Classifier dari pustaka scikit-learn. Algoritma ini sering digunakan untuk masalah klasifikasi karena mudah dipahami dan cukup efektif untuk dataset dengan jumlah data yang tidak terlalu besar.
Pertama, kita menentukan fitur yang akan digunakan sebagai input (X) dan target yang akan diprediksi (y). Dalam kasus ini:
Fitur (X) yang digunakan adalah "Jumlah Terjual" dan "Stok" karena kedua variabel ini dianggap relevan untuk menentukan apakah stok perlu diisi ulang.
Target (y) adalah apakah stok barang perlu diisi ulang atau tidak. Jika stok kurang dari 5, maka diberi label 1 (perlu di-restock), sedangkan jika stok masih cukup, diberi label 0.
Setelah menentukan fitur dan target, kita membagi data menjadi data training dan data testing menggunakan train_test_split(). Biasanya, kita menggunakan 80% data untuk pelatihan dan 20% untuk pengujian. Tujuan dari pembagian ini adalah untuk menguji performa model pada data yang belum pernah dilihat sebelumnya, sehingga kita bisa mengetahui seberapa akurat model dalam melakukan prediksi.

6. Selanjutnya, kita melatih model Decision Tree Classifier menggunakan fit(X_train, y_train). Setelah model selesai dilatih, kita menguji model dengan data uji dan mengukur akurasinya menggunakan accuracy_score(). Semakin tinggi akurasinya, semakin baik model dalam melakukan prediksi.
   
7. Prediksi dan Implementasi Model
Setelah model dilatih, kita coba melakukan prediksi pada data baru. Misalnya, kita punya sebuah produk dengan jumlah terjual 8 dan stok tersisa 3. Kita memasukkan data ini ke dalam model dan meminta model untuk memprediksi apakah stok produk ini perlu di-restock atau tidak.
Jika hasil prediksi 1, maka muncul pesan "Produk perlu di-restock!", yang berarti stok barang sudah hampir habis dan perlu ditambah. Tapi jika hasil prediksi 0, maka muncul pesan "Stok masih cukup.", yang berarti tidak perlu menambah stok untuk saat ini.

Dari praktikum ini, kita belajar bagaimana menggunakan machine learning untuk membantu dalam pengambilan keputusan bisnis. Dengan menggunakan model seperti Decision Tree, kita bisa membuat sistem otomatis yang dapat memprediksi kebutuhan restock barang berdasarkan data penjualan.
