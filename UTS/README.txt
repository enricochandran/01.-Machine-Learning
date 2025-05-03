Dokumen ini merangkum hasil pada tiga jenis model Machine Learning: Clustering (Pengelompokan), Classification (Klasifikasi), dan Regression (Regresi). Setiap model diterapkan pada dataset yang berbeda, dengan berbagai metode preprocessing, pemilihan model, dan evaluasi performa.

====================================================================================================

Regression Models – Memprediksi Nilai Kontinu
Model regresi digunakan untuk memprediksi nilai numerik (kontinu) berdasarkan fitur yang ada.

Dataset:
- Berisi 515.344 sampel dengan 91 fitur.
- Setelah preprocessing (penghapusan duplikasi & outlier), data yang digunakan menjadi 37.269 sampel.

Preprocessing:
- Normalisasi data dengan StandardScaler.
- Pembersihan outlier dengan IQR filtering.

Model:
- Linear Regression
- Ridge & Lasso Regression
- Decision Tree Regressor
- Random Forest Regressor
- XGBoost Regressor

Evaluasi & Hasil:
Model                 MAE       MSE       RMSE      R²Score
Linear Regression	    3.12	    12.98  	  3.60	    0.78
Ridge Regression	    2.89	    11.56    	3.40	    0.81
Decision Tree        	2.51	    8.97	    2.99	    0.86
Random Forest	        2.21	    6.84	    2.61	    0.91
XGBoost Regressor	    1.95	    5.32	    2.31	    0.94

XGBoost Regressor menunjukkan performa terbaik dengan R² = 0.94, menandakan model ini dapat memprediksi nilai dengan akurasi tinggi.

====================================================================================================

Classification Models – Memprediksi Kategori Diskrit
Pada eksperimen ini, model klasifikasi digunakan untuk memprediksi kategori diskrit pada dataset transaksi kartu kredit yang mengandung kasus penipuan (fraud detection).

Dataset:
- Mengandung 284.807 transaksi, dengan hanya 473 kasus fraud (highly imbalanced).

Preprocessing Data:
- Penghapusan data duplikat.
- Normalisasi dan standarisasi fitur numerik.
- Oversampling menggunakan SMOTE untuk menangani data imbalance.

Model:
- Logistic Regression
- Decision Tree
- Random Forest
- Support Vector Machine (SVM)
- XGBoost (Gradient Boosting)

Evaluasi & Hasil:
Model	                  Accuracy	  Precision	    Recall	    F1-Score	    ROC-AUC
Logistic Regression	    94.2%	      85.1%	        78.3%	      81.5%	        91.5%
Decision Tree	          97.1%	      88.9%	        82.4%	      85.5%	        92.3%
Random Forest	          99.1%	      92.3%	        90.8%	      91.5%	        97.4%
SVM	                    98.3%	      89.7%	        85.2%	      87.4%	        96.1%
XGBoost	                99.5%	      94.6%	        93.2%	      93.9%	        98.7%

- XGBoost adalah model terbaik, dengan F1-Score (93.9%) dan ROC-AUC Score (98.7%) tertinggi.
- Random Forest juga cukup baik, namun tidak sebaik XGBoost dalam menangani data imbalance.

====================================================================================================

Clustering Models – Pengelompokan Data yang Mirip
Model clustering digunakan untuk mengelompokkan data berdasarkan kemiripannya tanpa label tertentu. Dalam eksperimen ini, beberapa algoritma clustering dibandingkan untuk menilai keakuratan dan efektivitas pengelompokan.

Dataset terdiri dari sejumlah besar data numerik tanpa label kelas.

Beberapa metode klasterisasi diterapkan:
- KMeans – Algoritma berbasis centroid yang mengelompokkan data berdasarkan minimisasi jarak intra-cluster.
- Agglomerative Clustering – Teknik hierarki yang menggabungkan data berdasarkan kedekatan.
- DBSCAN – Algoritma berbasis kepadatan yang tidak memerlukan jumlah cluster tetap.
- Spectral Clustering – Menggunakan pendekatan berbasis graf untuk partisi data.
- Gaussian Mixture Model (GMM) – Model probabilistik yang mengasumsikan distribusi Gaussian dalam data.

Evaluasi & Hasil:
- Silhouette Score (Semakin tinggi, semakin baik)
- Davies-Bouldin Index (Semakin kecil, semakin baik)
- Calinski-Harabasz Index (Semakin besar, semakin baik)

Model	              Silhouette Score	    Davies-Bouldin Index	    Calinski-Harabasz Index
KMeans	            0.640	                0.454	                    9873.13
Agglomerative	      0.558	                0.510	                    7342.66
DBSCAN	            0.543	                1.028	                    13.91
Spectral	          0.100	                0.883	                    4470.92
Gaussian Mixture	  0.084	                11.50	                    336.28

- KMeans memiliki performa terbaik dengan Silhouette Score tertinggi (0.64), menunjukkan klasterisasi yang lebih baik dibanding metode lain.
- DBSCAN efektif dalam mendeteksi outlier tetapi memiliki skor Davies-Bouldin yang kurang optimal.
- Gaussian Mixture Model (GMM) kurang optimal dalam dataset ini karena menghasilkan indeks Davies-Bouldin yang tinggi.

