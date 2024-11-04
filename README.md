Tugas Data Mining
==
Analisis Data dengan Decision Tree
--
Deskripsi Dataset
-
Dataset yang digunakan adalah tentang kesehatan jantung, yang berisi berbagai informasi penting mengenai faktor risiko penyakit jantung, seperti usia, tekanan darah saat istirahat (RestingBP), kadar kolesterol, dan variabel lainnya. Dataset ini terdiri dari 918 sampel, dengan kolom target bernama HeartDisease yang menunjukkan apakah seseorang menderita penyakit jantung atau tidak. Alasan memilih dataset ini karena penyakit jantung merupakan salah satu penyebab kematian tertinggi di dunia, dan banyak kasus bisa dicegah jika terdeteksi lebih awal. Dengan dataset ini, kita bisa membangun model prediktif untuk menilai risiko penyakit jantung, sehingga membantu tenaga kesehatan dan pasien dalam mengidentifikasi mereka yang berisiko tinggi lebih awal.

Proses dan Evaluasi 
-
Proses pembuatan model melibatkan beberapa langkah berikut:
- Penanganan Nilai Ekstrim: Kolom Cholesterol dipotong (clipping) pada nilai maksimum 450 untuk menghindari efek dari outlier. Kolom Oldpeak juga dipotong pada rentang -0.5 hingga 4 untuk menjaga distribusi data yang lebih baik.
- Pengubahan Kolom Kategorikal: Kolom kategorikal (Sex, ChestPainType, RestingECG, ExerciseAngina, dan ST_Slope) diubah menjadi variabel dummy untuk diintegrasikan ke dalam model pohon keputusan.
- Dataset dibagi menjadi data latih (70%) dan data uji (30%) untuk mengevaluasi kinerja model secara objektif.
- Unpruned Decision Tree: Model pertama dibuat tanpa pruning. Hasilnya, akurasi mencapai 100% pada data latih, tetapi hanya 73.5% pada data uji, yang menunjukkan adanya overfitting.
- Prepruned Tree: Model kedua menggunakan teknik pre-pruning dengan batasan tertentu (max_depth=6, min_samples_split=10, dan min_samples_leaf=10). Akurasinya adalah 87% pada data latih dan 80.4% pada data uji, menunjukkan perbaikan dalam generalisasi.
- Postpruned Tree: Model ketiga dilakukan dengan post-pruning (ccp_alpha=0.005). Model ini mencapai akurasi 85.7% pada data latih dan 86.9% pada data uji, memberikan keseimbangan yang lebih baik antara keduanya.

Visualisasi dan Analisis
-
Pada setiap model pohon keputusan, visualisasi struktur pohon menunjukkan jalur keputusan yang diambil berdasarkan variabel input untuk memprediksi risiko penyakit jantung.

- Unpruned Tree: Struktur pohon ini sangat kompleks dan memiliki banyak node, yang menyebabkan overfitting terlihat jelas dari perbedaan akurasi antara data latih dan uji.
- Prepruned Tree: Model ini lebih sederhana dengan kedalaman terbatas dan lebih sedikit node, mengurangi overfitting meskipun dengan sedikit penurunan akurasi.
- Postpruned Tree: Model ini menunjukkan kinerja yang paling seimbang antara akurasi data latih dan uji, menunjukkan bahwa ia dapat menggeneralisasi dengan lebih baik tanpa terlalu banyak cabang.
  
Rekomendasi dan Saran
-
Berdasarkan analisis, beberapa rekomendasi dapat diberikan:

- Implementasi Model Postpruning: Post-pruned decision tree memiliki kinerja terbaik, sehingga disarankan untuk menggunakan model ini dalam prediksi penyakit jantung.
- Penggunaan Fitur Penting: Berdasarkan korelasi dengan HeartDisease, variabel MaxHR, Cholesterol, dan Oldpeak memiliki pengaruh signifikan, sehingga penting untuk memberikan perhatian lebih pada variabel-variabel ini dalam analisis lebih lanjut atau pengembangan model.
- Pengembangan Model yang Lebih Kompleks: Model lain seperti Random Forest atau Gradient Boosting dapat dipertimbangkan untuk meningkatkan akurasi prediksi dan mengurangi variabilitas model pohon keputusan.

