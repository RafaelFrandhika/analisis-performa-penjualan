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

### Tren Penjualan Bulanan
![Tren Penjualan](tren_penjualan.png)
> Penjualan terendah terjadi pada April 2011 (~430.000) dan terus meningkat
> drastis hingga puncaknya di November 2011 (~1,13 juta). Penurunan tajam
> di Desember 2011 kemungkinan karena data bulan tersebut belum lengkap.

### Heatmap Korelasi
![Heatmap](heatmap.png)
> Quantity memiliki korelasi sangat kuat terhadap Total_Sales (0.92),
> artinya semakin banyak barang terjual maka pendapatan semakin besar.
> Sebaliknya, UnitPrice justru berkorelasi negatif (-0.13) terhadap
> Total_Sales, menunjukkan produk mahal tidak selalu menghasilkan
> pendapatan lebih tinggi.

### Produk Underperformer
![Scatter Plot](scatter.png)
> Sebagian besar produk menumpuk di kisaran harga di bawah rata-rata
> (Rp 3.99) dengan penjualan tinggi. Namun terdapat beberapa produk
> dengan harga sangat tinggi (hingga 700+) yang quantity terjualnya
> mendekati nol — inilah produk underperformer yang perlu dievaluasi.

### RFM Analysis
![RFM](rfm.png)
> Segmentasi pelanggan berhasil dilakukan dengan skor 1–5 pada tiga
> dimensi. Pelanggan dengan RFM Group 555 adalah pelanggan Champions —
> paling baru bertransaksi, paling sering belanja, dan pengeluaran
> terbesar. Pelanggan dengan skor rendah seperti 211 berisiko churn
> dan perlu pendekatan retensi.

### Efisiensi Kategori vs Anggaran Iklan
![Bar Chart](barchart.png)
> REGENCY CAKESTAND 3 TIER memiliki rasio efisiensi tertinggi (~0.13),
> jauh di atas produk lainnya. Artinya produk ini menghasilkan penjualan
> terbesar dibanding anggaran iklan yang dikeluarkan. Sebaliknya,
> kelompok produk LUNCH BAG memiliki efisiensi paling rendah.

### Pengaruh Ad_Budget terhadap Penjualan
![Hipotesis](hipotesis.png)
> Rata-rata penjualan kelompok iklan tinggi (Rp 20.08) justru sedikit
> lebih rendah dibanding iklan rendah (Rp 20.73). Hal ini menunjukkan
> bahwa Ad_Budget tidak berpengaruh signifikan — wajar karena kolom
> ini disimulasikan secara acak, bukan data nyata.

### Regresi Linear
> - Koefisien Iklan : (isi dari output Sel 12)
> - R² Score        : (isi dari output Sel 12)

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
