# **Credit Card Customer Segmentation**

### **Creator Profile** 
1. Gina Nur Rahmasari - ginanurahmasari@gmail.com | [LinkedIn](https://www.linkedin.com/in/gina-nur-rahmasari-4ab0a4b7/) | [GitHub](https://github.com/ginanurahmasari)
2. Herdiansyah Prihatna Putra - herdiansyahprihatna@gmail.com | [LinkedIn](https://www.linkedin.com/in/herdiansyahp/) | [GitHub](https://github.com/HerdiansyahPP)
3. Saniyya Hanan Rosyida - saniyya.rosyida@gmail.com | [LinkedIn](https://www.linkedin.com/in/saniyya-hanan-rosyida/) | [GitHub](https://github.com/saniyyarosyida)

### **Content**
1. Business Problem Understanding
2. Data Understanding
3. Data Preprocessing
4. Modeling and Evaluation
5. Conclusion
6. Recommendation
7. Business Implementation

## **I. Business Problem Understanding**
#### **Context**
Dilansir dari [US Bank](https://www.usbank.com/credit-cards/how-credit-cards-work.html#:~:text=Credit%20cards%20offer%20you%20a,loan%20amount%20in%20the%20future.), kartu kredit merupakan instrumen yang dikeluarkan oleh pihak Bank atau lembaga keuangan sejenis yang memungkinkan pemilik kartu kredit untuk melakukan pembayaran non tunai, mentransfer saldo dan menarik uang tunai menggunakan uang milik bank yang tertera dalam sebuah kartu kredit. Tiap jenis kartu kredit memiliki limit saldo yang berbeda-beda. Kepemilikan jenis kartu kredit biasanya disesuaikan dengan penghasilan customer, riwayat penggunaan kartu kredit dan jumlah aset yang dimiliki. Semakin besar penghasilan dan kepemilikan aset, serta semakin loyal, konsumtif dan bertanggung jawab seorang customer dalam riwayat penggunaan kredit, akan memungkinkan bagi bank untuk memberikan limit kredit yang semakin besar atau bahkan tak terbatas. Setiap kegiatan transaksi yang dilakukan menggunakan kartu kredit wajib dibayarkan kembali kepada pihak bank di masa mendatang sesuai dengan tenggat waktu yang diberikan. Seorang customer dapat membayar tagihan kredit secara lunas atau dengan pembayaran minimum namun dikenakan bunga. Jika seorang customer terlambat/tidak membayar tagihannya, maka jumlah tagihannya akan dikenakan bunga dan denda oleh pihak bank dan jika hal ini terus terjadi akan beresiko untuk diturunkan limitnya atau di-blacklist. Dengan demikian, customer yang loyal, konsumtif, dan selalu membayar tagihan kreditnya menjadi kunci bagi pemberi kredit agar bisnis tetap berjalan lancar dan tidak terjadi kredit macet.

Berdasarkan survei yang dilakukan oleh [Forbes Advisor](https://www.forbes.com/advisor/credit-cards/credit-card-statistics/#:~:text=Most%20Common%20Types%20of%20Credit,52.8%25%20of%20cards%20in%20circulation.) pada Februari 2023, hanya 9% warga USA yang masih aktif menggunakan uang tunai untuk bertransaksi, 54% orang lebih memilih menggunakan kartu debit fisik atau virtual, dan 36% lainnya menggunakan kartu kredit fisik atau virtual. Hal ini membuktikan bahwa pola transaksi jual beli di masyarakat telah beralih dari tunai menjadi non tunai, sebab proses pembayarannya yang lebih simpel dan akurat. Beberapa alasan seseorang lebih memilih kartu kredit untuk bertransaksi adalah adanya credit reward, ingin membangun credit score, serta kenyamanan dan keamanan dalam bertransaksi. 4 kartu kredit yang paling umum digunakan di USA adalah Visa, Mastercard, American Express, dan Discover. 

Berdasarkan artikel [Money Geek](https://www.moneygeek.com/credit-cards/advice/how-credit-card-companies-make-money/) dan [Joe Resendiz](https://www.valuepenguin.com/how-do-credit-card-companies-make-money), Bank memperoleh keuntungan dari bisnis kartu kredit melalui :
- Bunga dan denda yang dikenakan ketika customer telat membayar tagihan.
- Bunga dari peminjaman baik sekali bayar, cicilan, maupun tunai.
- Biaya penarikan uang tunai / cash advance. Seringkali Bank membebankan biaya yang lebih tinggi untuk tarik tunai.
- Biaya transfer saldo dari satu kartu kredit ke kartu kredit lain.
- Biaya transaksi luar negeri.
- Biaya yang dibayarkan merchant untuk setiap barang/aset yang terjual melalui transaksi dengan kredit.

Bertumbuhnya jumlah pengguna kartu kredit dari tahun ke tahun menyebabkan persaingan bisnis kartu kredit semakin ketat. Pelanggan dapat dengan mudah beralih ke kartu kredit lain yang memiliki biaya keseluruhan paling rendah. Oleh karena itu, penting bagi perusahaan kartu kredit untuk memahami karakteristik pelanggannya kemudian membangun loyalitas dan perilaku konsumtif pelanggan berdasarkan karakteristiknya, sebab mempertahankan pelanggan yang sudah ada lebih murah dibandingkan dengan mendapatkan pelanggan baru. Dilansir dari [SendPulse](https://sendpulse.com/support/glossary/customer-loyalty), pelanggan yang loyal dalam menggunakan kartu kredit sangat penting bagi Bank karena pelanggan tersebut cenderung melakukan pembayaran dengan kredit secara berulang-ulang dan pengeluaran lebih besar saat liburan, sehingga lebih banyak menghasilkan keuntungan daripada pelanggan yang lebih memilih untuk bertransaksi non kredit.

#### **Problem Statement & Goals**
American Gold Bank adalah sebuah Bank penyedia layanan kartu kredit di USA. Bank tersebut ingin mengetahui karakteristik pelanggannya yang sudah ada kemudian menentukan strategi pemasaran yang tepat untuk dapat membangun loyalitas pelanggan dalam menggunakan produk mereka. Hal ini berguna agar penawaran produk/reward menjadi tepat sasaran sehingga kebutuhan dan kepuasan pelanggan dapat terpenuhi, Bank dapat membangun pelanggan yang masih kurang menguntungkan maupun yang sudah loyal menjadi lebih menguntungkan, serta Bank tidak membuang-buang waktu maupun biaya kepada pelanggan yang merugikan.

Jika pelanggan yang sudah ada tidak dipertahankan, pelanggan dapat beralih ke kartu kredit lain dan menyebabkan keuntungan bisnis menurun, citra bisnis buruk akibat penilaian dari pelanggan kurang baik, dan dalam jangka waktu panjang ketidakpuasan pelanggan akan memengaruhi respon pasar terhadap konten pemasaran yang diterbitkan sehingga membuat penetrasi produk ke pasar menjadi sulit dan Bank tidak dapat menghadapi persaingan perbankan.

#### **Analytic Approach (Model & Metric Evaluation)**
Selaku Data Scientist di American Gold Bank, kami akan menyelesaikan permasalahan ini dengan men-segmentasi pelanggan berdasarkan riwayat penggunaan kartu kreditnya. Dari sini, kita dapat melihat tingkat loyalitas, perilaku konsumtif dan tanggung jawab pelanggan saat membayar tagihan kredit. Oleh karena itu, model akan dibuat menggunakan metode clustering. Beberapa algoritma clustering yang akan digunakan adalah K-Means, Agglomerative dan DBSCAN (Density-based spatial clustering of applications with noise).

Metric evaluasi yang akan digunakan adalah silhouette score untuk setiap model. Metric silhouette score mengevaluasi model berdasarkan tingkat kemiripan sebuah data poin dengan clusternya sendiri terhadap cluster lain. Jika nilai silhouette score semakin mendekati angka 1, maka semakin jelas perbedaan antar tiap cluster / dapat menjadi tolak ukur untuk melihat apakah pelanggan kartu kredit telah benar-benar tersegmentasi dengan jelas berdasarkan perilaku penggunaan kredit. Jika pelanggan tersegmentasi dengan baik, maka pemberian dan penerapan strategi bisnis untuk tiap segmen pelanggan menjadi lebih tepat sasaran, sehingga dapat meminimalisir waktu, tenaga dan pengeluaran biaya yang sia-sia. 

Kami juga menggunakan membership untuk melihat jumlah anggota pada tiap cluster yang telah dibuat, sehingga penentuan model terbaik tak hanya berdasarkan nilai metric evaluasinya saja. Terkadang, ada model yang memiliki nilai evaluasi baik namun jumlah anggota pada tiap clusternya sangat jauh berbeda. Penggunaan membership dapat menghindari hal tersebut. Visualisasi boxplot dari hasil clustering juga akan menjadi pertimbangan untuk melihat perbedaan antara 1 cluster dengan cluster lain. Model dengan silhouette score terbaik dengan hasil cluster yang jelas terlihat perbedaannya dan proporsi cluster yang tidak mendiskriminasi cluster lain dapat dipertimbangkan sebagai model terbaik.

## **II. Data Understanding**
Permasalahan di atas akan dianalisa menggunakan dataset **Credit Card for Clustering**. Dataset ini diupload oleh Arjun Bhasin di situs kaggle pada tahun 2018 dan berisi data riwayat perilaku pemegang kartu kredit aktif selama 6 bulan. Dataset dapat diakses [di sini.](https://www.kaggle.com/datasets/arjunbhasin2013/ccdata)
**Dataset Information**

| Variabel Perilaku | Data Type | Description |
| --- | --- | --- |
| CUST_ID | Object | ID customer |
| BALANCE | Float | Jumlah saldo kredit yang tersisa pada 1 akun customer (Dollar USA) |
| BALANCE_FREQUENCY | Float | Frekuensi saldo kredit terupdate (Range 0-1, semakin besar nilai semakin sering frekuensinya) |
| PURCHASES | Float | Total transaksi pembelian menggunakan kartu kredit (one off dan installment) dalam 1 akun selama 6 bulan terakhir (Dollar USA) |
| ONEOFF_PURCHASES | Float | Total transaksi pembelian yang dilakukan dengan sekali pembayaran (one off) menggunakan kartu kredit (Dollar USA) |
| INSTALLMENTS_PURCHASES | Float | Total transaksi pembelian yang dilakukan dengan cicilan pembayaran (installment) menggunakan kartu kredit (Dollar USA) |
| CASH_ADVANCE | Float | Total penarikan tunai (Dollar USA) |
| PURCHASES_FREQUENCY | Float | Frekuensi pembelian menggunakan metode One off dan installment (Range 0-1, semakin besar nilai semakin sering frekuensinya) |
| ONEOFFPURCHASESFREQUENCY | Float | Frekuensi pembelian menggunakan metode one off (Range 0-1, semakin besar nilai semakin sering frekuensinya) |
| PURCHASESINSTALLMENTSFREQUENCY | Float | Frekuensi pembelian menggunakan metode installment (Range 0-1, semakin besar nilai semakin sering frekuensinya) |
| CASHADVANCEFREQUENCY | Float | Frekuensi penarikan tunai (semakin besar nilai semakin sering frekuensinya) |
| CASHADVANCETRX | Integer | Jumlah transaksi penarikan tunai |
| PURCHASES_TRX | Integer | Jumlah transaksi pembelian menggunakan kartu kredit (one off dan installment) |
| CREDIT_LIMIT | Float | Total maksimum saldo kredit dalam 1 akun customer selama masa kredit aktif dalam 6 bulan (Dollar USA) |
| PAYMENTS | Float | Total pembayaran tagihan yang telah dilakukan customer (Dollar USA) |
| MINIMUM_PAYMENTS | Float | Total pembayaran minimum tagihan yang telah dilakukan customer (Dollar USA) |
| PRCFULLPAYMENT | Float | Persentase pembayaran tagihan secara lunas yang telah dilakukan customer (Range 0-1, semakin besar nilai semakin tinggi persentasenya) |
| TENURE | Integer | Tenor / jangka waktu layanan kartu kredit untuk pengguna (bulan) |

## **III. Data Preprocessing**
- Handle Missing Value in credit limit and minimum payments
- Handle invalid data in credit limit
- Scaling with robust scaler
- Handle multicollinearity for K-Means with PCA and Feature Selection
