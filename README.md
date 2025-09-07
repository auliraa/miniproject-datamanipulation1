# ETL Data Ritel - Pandas Project

## 📋 Deskripsi Proyek
Project ETL (Extract-Transform-Load) untuk membersihkan dan memproses data transaksi ritel bulan Januari 2019. Proyek ini merupakan implementasi praktis dari pembelajaran **Data Manipulation with Pandas - Part 1**.

## 🎯 Tujuan
Melakukan preprocessing data ritel mentah agar siap untuk analisis lebih lanjut dengan menerapkan tahapan ETL standar:
- **Extract**: Membaca data dari sumber
- **Transform**: Membersihkan dan mengolah data
- **Load**: Menyimpan hasil ke format yang siap pakai

## 📊 Dataset
- **Sumber**: [retail_raw_test.csv](https://storage.googleapis.com/dqlab-dataset/retail_raw_test.csv)
- **Jumlah records**: 5,000 transaksi
- **Periode**: Data transaksi berbagai bulan dengan fokus pada Januari 2019
- **Scope**: Data cabang perusahaan ritel di berbagai kota dan provinsi Indonesia

## 🔧 Tahapan ETL

### 1. Extract (Pembacaan Data)
- Membaca dataset dari URL sumber
- Melakukan initial data exploration

### 2. Transform (Transformasi Data)
- **Konversi Tipe Data**: 
  - `customer_id`: string → int64
  - `quantity`: string → int64  
  - `item_price`: string → int64
- **Standardisasi Product ID**: Format PXXXX dari kolom `product_value`
- **Format Tanggal**: Konversi ke format YYYY-mm-dd
- **Handle Missing Values**:
  - `brand` → "no_brand"
  - `city` & `province` → "unknown"
- **Feature Engineering**:
  - Gabungkan `city/province`
  - Buat hierarchical index
  - Hitung `total_price` = `quantity` × `item_price`
- **Data Filtering**: Slice data untuk Januari 2019 saja

### 3. Load (Penyimpanan)
- Data final tersimpan dengan hierarchical index
- Siap untuk analisis lanjutan

## 🛠️ Dependencies
```python
import pandas as pd
import math
```


```

## 📈 Hasil
- **Dataset Awal**: 5,000 records dengan 9 kolom
- **Dataset Final**: 334 records Januari 2019 dengan 4 kolom + hierarchical index
- **Struktur Index**: `city/province` → `order_date` → `customer_id` → `order_id` → `product_id`
- **Kolom Final**: `brand`, `quantity`, `item_price`, `total_price`

## 🔍 Fitur Utama
- ✅ Data cleaning dan validation
- ✅ Standardisasi format data
- ✅ Missing value handling
- ✅ Feature engineering
- ✅ Hierarchical indexing
- ✅ Data filtering berdasarkan periode

## 📝 Struktur File
```
etl-data-ritel/
│
├── miniproject.py              # Script utama ETL
├── README.md                   # Dokumentasi project
```

## 🎓 Pembelajaran
Project ini mengcover konsep-konsep penting dalam data manipulation:
- Pandas DataFrame operations
- Data type conversion
- String manipulation dan regex
- DateTime handling
- Missing value strategies
- Index manipulation
- Data filtering dan slicing

## 👨‍💻 Author
**AULIRA** - Data Analyst Learner Journey

## 📄 License
This project is open source and available under the [MIT License](LICENSE).

---
> *"ETL itu singkatan dari Extract – Transform – Load. Ini adalah tahapan standar dalam pengolahan data sebelum analisis atau penyimpanan ke data warehouse."*