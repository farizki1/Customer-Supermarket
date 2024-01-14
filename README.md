# Customer-Supermarket

# LATAR BELAKANG
Sebuah perusahaan bergerak dibidang retail Supermarket bernama Serba Ada Mart. Serba Ada Mart saat ini menjalani bisnisnya di usia 10 tahun. Namun, mulai bermunculan kompetitor - kompetitor baru yang lahir dan dapat mengancam bisnis Serba Ada Mart.

Dikarenakan itu Manajamen Serba Ada Mart berinisiatif untuk merekrut seorang Data Scienctist. Data Scientist tersebut bertugas untuk menganalisis data pelanggan Serba Ada Mart pada rentang tahun 2012 - 2014. Diharapkan Manajemen mendapat rekomendasi yang dapat berdampak positif terhadap kemajuan Perusahaan. 

# RUMUSAN MASALAH
1. Bagaimana karakteristik pelanggan dan produk yand dijual?
2. Apakah strategi promo yang sudah diterapkan tepat guna?

# REFERENSI
- Referensi 2n cycle (https://www.studera.nu/startpage/higher-education/sweden/levels-degrees/)
- Kategori usia (https://gaya.tempo.co/read/1724197/kategori-umur-balita-remaja-dan-dewasa-menurut-kemenkes-jangan-salah)

# DATA

Untuk menjawab pertanyaan di atas, kita akan menganalisa data peserta yang sudah dikumpulkan oleh perusahaan. Dataset dapat diakses di sini.

Dataset ini berisi informasi terkait data pelanggan pada saat pelanggan melakukan transaksi. Ada 29 kolom di dalam dataset Supermarket Customer, yaitu:

### People
- ID: Customer's unique identifier
- Year_Birth: Customer's birth year
- Education: Customer's education level
- Marital_Status: Customer's marital status
- Income: Customer's yearly household income
- Kidhome: Number of children in customer's household
- Teenhome: Number of teenagers in customer's household
- Dt_Customer: Date of customer's enrollment with the company
- Recency: Number of days since customer's last purchase
- Complain: 1 if the customer complained in the last 2 years, 0 otherwise
### Products
- MntWines: Amount spent on wine in last 2 years
- MntFruits: Amount spent on fruits in last 2 years
- MntMeatProducts: Amount spent on meat in last 2 years
- MntFishProducts: Amount spent on fish in last 2 years
- MntSweetProducts: Amount spent on sweets in last 2 years
- MntGoldProds: Amount spent on gold in last 2 years
### Promotion
- NumDealsPurchases: Number of purchases made with a discount
- AcceptedCmp1: 1 if the customer accepted the offer in the 1st campaign, 0 otherwise
- AcceptedCmp2: 1 if the customer accepted the offer in the 2nd campaign, 0 otherwise
- AcceptedCmp3: 1 if the customer accepted the offer in the 3rd campaign, 0 otherwise
- AcceptedCmp4: 1 if the customer accepted the offer in the 4th campaign, 0 otherwise
- AcceptedCmp5: 1 if the customer accepted the offer in the 5th campaign, 0 otherwise
- Response: 1 if the customer accepted the offer in the last campaign, 0 otherwise
### Place
- NumWebPurchases: Number of purchases made through the company’s website
- NumCatalogPurchases: Number of purchases made using a catalog
- NumStorePurchases: Number of purchases made directly in stores
- NumWebVisitsMonth: Number of visits to the company’s website in the last month

Secara garis besar kita kita mendapat informasi sbb :
- Dataset Supermarket Customer memiliki 29 Kolom dan 2240 Baris.
- Kolom Z_CostContact tidak di jelaskan pada Data dictionary serta untuk semua ID hanya berisi 1 jenis angka yaitu angka 3, selain itu kolom Z_Revenue memiliki case yang sama.
- Kolom Income terdapat 24 baris yang berisikan nan.
- Pada kolom Education, terdapat 2 jenis education yang levelnya sama yaitu Master dan 2n Cycle. Untuk nantinya keterangan 2n cycle akan kita ubah menjadi master agar menjadi 1 jenis education yang sama.
- Kolom Marital_Status terdapat 4 jenis status yang berarti sama yaitu Single, Alone, Absurd, dan YOLO yang nantinya akan kita ubah menjadi Single. Selain itu Together dan Married, Together akan kita ubah menjadi Married. Sehingga nantinya akan ada 4 jenis Marital_Status yaitu Single, Divorced, Widow dan Married.
- Kolom Year_Birth terdapat 3 nilai yang sangat jauh berbeda dengan nilai lain, yaitu tahun 1893 enrollment tahun 2014 (umur 121), 1899 enrollment tahun 2013 (umur 114 tahun) , 1900 (113) enrollment tahun 2013. Dengan asumsi tahun tertua yang saling berdekatan antar 1 sama lain yaitu Year_Birth 1940 enrollment 2013 (umur 73). Sehingga kita asumsikan batas enrollment yang produktif adalah 75 tahun. Sehingga data yang melebihi usia 75 tahun tidak kita gunakan.
- kolom income terdapat data yang terpaut jauh dengan data lain yaitu 666666.

Secara garis besar
- missing value hanya di kolom Income, yang memiliki persentase 1.07% yaitu sebanyak 24 data baris kosong.

Cara penanganan missing value 
- yaitu dengan cara menghapus kolom yang memiliki nilai NAN, selain itu karena juga persentase yang kecil sehingga dapat disarankan untuk kita menghapus data kosong.

Dengan adanya anomali yang sudah kita temukan, mari kita menangani anomali - anomali secara lebih jauh dan mendalam

Dari data diatas kita memperoleh urutan tertinggi pertama untuk income dan kedua terpaut selisih yang sangat jauh, dan bahkan nilai income tersebut 12.7x dari rata- rata income. Selain itu pada data juga didapat bahwa urutan ke 2 dan 5 adalah pelanggan dengan education PHD dan Master. Melihat temuan ini agaknya cukup aneh jika jumlah income untuk jenjang graduation jauh lebih besar dibanding jenjang pendidikan yang lebih tinggi. Sehingga untuk anomali ini kita akan menghapus data tersebut.

### Analisis
Dari data diatas diperoleh analisis yaitu :
1. Income dari Serba ada Mart yaitu dari sektor Wines, sumbangsih paling tinggi adalah dari kategori Lansia, diikuti oleh Pra Lanjut Usia, Dewasa, dan Remaja. Hal ini menandakan semakin matang usia, maka konsumsi akan wines semakin tinggi. Hal ini juga menandakan bahwa kategori remaja yang masih rentan dan terlalu dini untuk mengonsumsi wines sehingga berdampak penjualan wine pada kategori remaja cukup rendah.
2. Kategori lansia juga merupakan kategori dengan pembelian tertinggi. hal ini berarti menandakan semakin matang usia seseorang maka pengeluaran juga banyak, dan sepadan dengan pendapat yang mereka peroleh. 
3. secara garis besar, kategori umur lansia adalah unggul dalam setiap pembelian produk.
4. produk teringgi yang di beli masing - masing kategori usia sama dengan peringkat produk dari invoice Serba Ada Mart. yaitu Wine, Meat, dan Gold.

untuk memastikan data sudah tepat, maka kita akan mencoba menganalisis apakah semakin matang usia maka pendapatan juga akan tinggi.

### Analisis

Dari data diatas di peroleh bahwa :
1. trend pengeluaran mirip dengan pendapatan. Dan hal ini menguatkan bahwa semakin matang usia memiliki penghasilan yang tinggi.
2. kategori remaja memiliki pendapatan dan pengeluaran yang kecil, hal ini memungkinkan karena pengeluaran mereka sebagian besar mengikuti orang tua, dan pendapatannya pun dari orang tua.
3. selain itu juga semakin matang tingkat konsumtif akan semakin tinggi.

# Analisis

1. Pada kategori graduation, master dan Phd. bahwa pengeluaran tertinggi yaitu secara urut untuk Wine, Meat, Gold, Fish, Fruit dan sweet;
2. pada kategori basic, pengeluaran terbesar mereka untuk Gold, dan terkecilnya untuk wine. 

untuk memastikan data sudah tepat, maka kita akan mencoba menganalisis apakah trend pendapatan by jenjang pendidikan sama dengan trend pengeluaran.

### Analisis

1. pendapatan dari tiap jenjang pendidikan memiliki trend yang sama dengan pengeluaran, yaitu Phd di pertama, graduation, master dan Basic
2. pendapatan dari master lebih renda meski tidak terpaut cukup jauh dari graduation. asumsi bahwa ada hal lain yang mempengaruhi sehingga tingginya pendidikan belum tentu pendapatannya juga tinggi, serta tingginya pendidikan belum tentu konsumen lebih konsumtif.

### Analisis

1. secara kategori marital, prduk tertinggi masih untuk pembelian wines, diikuti oleh daging, dan Gold. Hal ini sama jika kita bandingkan dengan income serba ada mart, pengeluaran & pendapatan berdasarkan kategori usia, pengeluaran & pendapatan berdasarkan jenjang pendidikan.
2. pembelian paling tinggu untuk wine yaitu pada kategori widow dan divorced. Diasumsikan bahwa perjuangan tinggal sendiri after pernikahan membuat kadar stres yang cukup tinggi, sehingga pelanggan membutuhkan hiburan berupa wine.

kita akan mencoba menganalisis apakah trend pendapatan by Marital sama dengan trend pengeluarannya.

### Analisis

1. sejalan dengan pengeluaran, pendapatan tertinggi diperoleh kategori widow. hal ini membuat trend pengeluaran dan pendapatan by marital status sama.
2. status singlee memiliki pengeluaran dan pendapatan yang paling kecil. hal ini mendadakan tingkat konsumsi status single rendah karena mereka tidak memiliki tanggungan kebutuhan.

### Analisis

1. Pelanggan yang tidak pernah menggunakan Promo yaitu sebesar 72.69 Persen. Hal ini menandakan bahwa promo yang saat ini berlangsung kurang efektif dan kurang memberikan ketertarikan kepada pelanggan. Total promo yang digunakan yaitu 27.32 pelanggan. hal ini bahwa cuman 1/4 pelanggan yang menggunakan promo. Dengan asumsi bahwa promo yang berjalan kurang memberikan ketertarikan ke pelanggan dan pelanggan tidak mengetahui adanya promo yang berjalan.

### Analisis

1. Campaign terakhir terbukti banyak digunakan oleh para pelanggan. sehingga diharapkan untuk strategi campaign yang akan berjalan selanjutnya dapat menggunakan cara strategi terakhir, dibanding dengan strategi campaign sebelum-sebelumnya.

### Analisis

1. dari informasi diatas di peroleh bahwa Total pengeluaran pelanggan untuk penggunaan campaign berbanding lurus dengan campaign yang diikuti.
2. Kategori dewasa merupakan kategori umur tertinggi dalam mengikuti campaign dan juga tertinggi dalam pengeluaran untuk penggunaan campaign. Hal ini diasumsikan bahwa untuk kategori umur tersebut sangat gencar dan up to date untuk mendapat informasi terkait campaign promosi.

untuk lebih mendapatkan informasi, sekarang kita coba untuk menguji apakah jenis promo dapat mempengaruhi ketertarikan konsumen berdasarkan kategori usia. 

pvalue = 0.00448. pvalue <= 0.05. Berhasil menolak Ho.
          Kita memiliki bukti yang cukup untuk mengatakan bahwa antara kategori usia dan campaign promo yang diikuti ada keterkaitan (dependent)
          (proporsinya berbeda signifikan)

# Analisis

1. Kategori usia remaja menduduki ratio penerimaan Campaign, hal ini kemungkinan dikarenakan strategi Serba ada Mart menjurus kepada anak remaja dan barang - barang remaja. Serta remaja memiiki waktu yang lebih untuk sekeder mencari campaign campaign promo.
2. kategori usia Dewasa, pra lanjut Usia, dan lansia justru memiliki ratio rendah. hal ini diasumsikan bahwa strategi serba ada Mart yang tidak menyasar pada ketiga kategori tersebut. Padahal meskipun ketiga kategori tersebut merupakan kategori konsumtif yang tinggi, tetap harus di lakukan strategi campaign yang sesuai dengan kategori usia mereka, agar dapat datang kembali untuk berbelanja.

### Analisis

1. Dari hubungan diatas juga didapat bahwa pengeluaran untuk mengikuti promo berbanding lurus dengan banyakya promo yang diikuti.
2. dari data jenjang pendidikan graduation merupakan jenjang pendidikan paling tinggi untuk mengikuti promo.

untuk lebih mendapatkan informasi, sekarang kita coba untuk menguji apakah jenis promo dapat mempengaruhi ketertarikan konsumen berdasarkan jenjang pendidikan. 

pvalue = 0.01224. pvalue <= 0.05. Berhasil menolak Ho.
          Kita memiliki bukti yang cukup untuk mengatakan bahwa antara jenjang pendidikan dan promo yang diikuti ada keterkaitan (dependent)
          (proporsinya berbeda signifikan)

### Analisis

1. dari data diatas didapat bahwa ratio jenajng pendidikan Phd paling tinggi, diasumsikan adanya hal ini karena seamkin tinggi jenjang pendidikan maka pengaturan keuangan semakin baik. sehingga lebih memanfaatkan program promo yang ada.

### Analisis

1. Dari hubungan diatas juga didapat bahwa pengeluaran untuk mengikuti promo berbanding lurus dengan banyakya promo yang diikuti berdasarkan marital status.
2. status married merupakan marital status paling tinggi untuk mengikuti promo, hal ini di asumsikan bahwa manajemen keuangan status married lebih baik. dimungkinkan karena banyak kebutuhan untuk status married sehingga menjadikan mereka lebih gencar untuk mengikuti promo.

untuk lebih mendapatkan informasi, sekarang kita coba untuk menguji apakah jenis promo dapat mempengaruhi ketertarikan konsumen berdasarkan marital status. 

pvalue = 0.00294. pvalue <= 0.05. Berhasil menolak Ho.
          Kita memiliki bukti yang cukup untuk mengatakan bahwa antara marital status dan promo yang diikuti ada keterkaitan (dependent)
          (proporsinya berbeda signifikan)

### Analisis

1. dari data diatas didapat bahwa ratio status widow paling tinggi, diasumsikan adanya hal ini karena status widow memiliki ekonomi sulit setelah pasangan mereka meninggal. sehingga mereka dengan gencar memanfaatkan campaign promo yang ada.

# KESIMPULAN
1. Pendapatan yang diperoleh Serba Ada Mart yang terbesar adalah di kategori Wine. 
2. Pendapatan terbesar tersebut dibuktikan dari kategori usia, jenjang pendidikan, dan Marital status, pembelian terbesar untuk tiap kategori tersebut adalah pembelian terhadap Wine, disusul dengan pendapatan melalui Meat. Hal ini dikarenakan Meat adalah produk bahan pokok yang mana semua kategori dapat mengonsumsinya setiap hari.
3. produk Fruit merupakan pendapatan terendah yang di peroleh Serba Ada Mart. 
4. pendapatan terendah Hal ini juga di buktikan dari kategori usia, jenjang pendidikan, dan marital status, bahwa pembelian terendah untuk tiap kategori tersebut adlah pembelian terhadap Fruit. 
5. Semakin matang usia, semakin tinggi Pendidikan maka pendapatan juga tinggi. Hal ini dibuktikan dari kategori usia lansia dan Phd yang memiliki pendapatan tinggi, juga berbanding lurus dengan konsumtif mereka. 
6. Kategori widow merupakan kategori yang memiliki penghasilan tertinggi di kategori marital status, hal tersebut juga didukung oleh konsumtif pengeluaran yang juga tinggi.
7. Kategori usia dan campaign promo yang diikuti ada keterkaitan (dependent)
8. Jenjang pendidikan dan promo yang diikuti ada keterkaitan (dependent)
9. Marital status dan promo yang diikuti ada keterkaitan (dependent)
10. Ratio ketertarikan Promo pada jenjang pendidikan, Phd memiliki ketertarikan yang paling tinggi, diikuti Graduation, Master dan Basic
11. Ratio ketertarikan Promo pada marital status, widow memiliki ketertarikan yang paling tinggi, diikuti Single, Divorced dan Married
12. Ratio ketertarikan Promo pada Kategori usia, Remaja memiliki ketertarikan yang paling tinggi, diikuti Dewasa, Pra Lanjut Usia dan Lansia

# REKOMENDASI

1. Produk Fish dan Fruit menyumbangkan sedikit sekali persentase pendapatan Serba Ada Mart. Namun, jenis produk tersebut membutuhkan penanganan yang extra untuk menghindari ketidak segaran produk, sehingga memerlukan suhu ruang yang lebih tinggi. hal ini harus didukung dengan adanya alat yang mumpuni dan extra cost untuk listrik.
2. Perlu adanya Campaign yang menarik seputar produk Fish dan Fruit, Selain dikarenakan kedua barang ini membutuhkan cost dan extra penanganan yang extra. Mungkin Promo menarik dan edukasi lebih di khususkan lagi untuk kategori Lansia, dan Remaja, Single, Basic . Hal ini dikarenakan lansia perlu menerapkan hidup sehat, untuk remaja makanan sehat cocok untuk masa pertumbuhan, selain itu untuk pendidikan Basic yang masih pada tahap masa sekolah dimana penting untuk stimulasi otak, serta single diasumsikan ingin proses memasak yang singkat.
3. Wine dan Meat sebagai produk unggulan lebih baik stock produk ditambah, apalagi mendekat perayaan - perayaan tertentu. Karena untuk menghindari stock kosong.
4. Selain program campaign promo, juga perlu adanya form penilaian pelayanan serba Ada Mart. Hal ini agar Serba ada Mart dapat terus mereview untuk memberi pelayanan yang lebih baik.
5. Dari segi ketersediaan barang juga, apalagi Serba Ada mart menjual produk yang rentan busuk. sebaiknya memperhatikan kualitas produk.
6. sedikit sekali promo yang dipakai oleh pelanggan. oleh hal ini sebaiknya Serba Ada Mart memberi angket perkategorinya, Produk yang disukai serta pilihan program Campaign Promo yang disukai pelanggan. Hal ini supaya program Promo lebih tepat sasaran yang diharapkan dapat menambah penjualan produk.
7. Produk Meat, Fish, dan Fruit sebaiknya perlu Extra campaign promo. Hal ini karena ketiga produk tersebut sangat rentan. dan jika umur produk mendekat masa - masa tidak bagus, sebaiknya ditambah dengan diskon yang menarik.
8. Campaign terakhir efektif, sehingga minimal untuk kedepannya perlu menggunakan campaign tersebut lagi.
