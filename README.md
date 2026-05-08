# 📊 Analisis Performa Penjualan E-Commerce

## 1. Business Question
- Siapa pelanggan terbaik berdasarkan perilaku transaksi mereka?
- Produk apa yang memiliki harga tinggi namun penjualan rendah (underperformer)?
- Apakah anggaran iklan yang lebih tinggi menghasilkan penjualan yang lebih besar?

## 2. Data Wrangling
- Dataset bersumber dari Kaggle (carrie1/ecommerce-data)
- Menghapus baris dengan nilai kosong menggunakan `dropna()`
- Menghapus transaksi dengan harga nol atau negatif
- Mengubah kolom `InvoiceDate` ke format datetime
- Membuat kolom baru `Total_Sales = Quantity × UnitPrice`

## 3. Insights
<img width="655" height="556" alt="heatmap" src="https://github.com/user-attachments/assets/82a4264d-28c3-4833-bdea-7776f8dc4967" />

Quantity → Total_Sales: 0.92 (korelasi sangat kuat) — semakin banyak quantity terjual, maka total pendapatan semakin besar. Ini adalah faktor utama yang mendorong penjualan.
UnitPrice → Total_Sales: -0.13 (korelasi negatif lemah) — produk dengan harga tinggi justru cenderung menghasilkan pendapatan lebih rendah, kemungkinan karena pembeliannya sedikit.
Quantity → UnitPrice: -0.0012 (hampir tidak ada korelasi) — harga produk tidak mempengaruhi seberapa banyak produk dibeli.

<img width="947" height="756" alt="grafik bar chart" src="https://github.com/user-attachments/assets/ee4c1b78-790d-473c-b174-cd464cd1bfa1" />

REGENCY CAKESTAND 3 TIER memiliki rasio efisiensi tertinggi (~0.13) — produk ini menghasilkan penjualan paling besar dibanding anggaran iklan yang dikeluarkan.
Kelompok produk LUNCH BAG (Cars Blue, Black Skull, Spaceboy) memiliki efisiensi paling rendah (~0.02–0.03) — anggaran iklan yang dikeluarkan tidak sebanding dengan penjualan yang dihasilkan.
Produk dekorasi seperti PARTY BUNTING dan WHITE HANGING HEART T-LIGHT HOLDER juga menunjukkan efisiensi yang cukup tinggi.

## 4. Recommendation
- **Pertahankan pelanggan Champions (RFM 555)** dengan program loyalitas
  atau reward eksklusif agar tidak berpindah ke kompetitor
- **Evaluasi produk underperformer** dengan harga tinggi namun penjualan
  rendah — berikan diskon atau pertimbangkan untuk dihentikan
- **Fokuskan anggaran iklan** pada REGENCY CAKESTAND 3 TIER dan produk
  dengan efisiensi tinggi lainnya
- **Manfaatkan momentum September–November** dengan kampanye promosi
  lebih agresif karena tren penjualan naik signifikan di periode tersebut
- **Lakukan retensi pelanggan RFM rendah** (skor 211) dengan voucher
  atau email marketing sebelum mereka benar-benar churn
