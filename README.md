# Sistem Prediksi Biaya Pemakaian Listrik dengan Logika Fuzzy

![Python](https://img.shields.io/badge/python-3.8+-blue.svg)
![Flask](https://img.shields.io/badge/Flask-3.1.1-green.svg)
![scikit-fuzzy](https://img.shields.io/badge/scikit--fuzzy-0.5.0-orange.svg)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.10.3-yellow.svg)
![NumPy](https://img.shields.io/badge/NumPy-2.2.6-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)

Aplikasi web berbasis Flask yang menggunakan sistem inferensi fuzzy untuk memprediksi biaya pemakaian listrik berdasarkan beberapa parameter rumah tangga. Sistem ini mengimplementasikan 81 aturan fuzzy untuk memberikan estimasi yang akurat.

## Deskripsi

Sistem ini dirancang untuk membantu pengguna mengestimasi biaya pemakaian listrik bulanan berdasarkan empat parameter utama:

- **Luas Rumah** (m²)
- **Daya Listrik** (VA)
- **Jumlah Perlengkapan Elektronik** (unit)
- **Pendapatan Ekonomi** (juta rupiah)

Dengan menggunakan metode Mamdani, sistem akan memproses input melalui fungsi keanggotaan fuzzy dan memberikan output berupa prediksi biaya dalam ribuan rupiah.

## Fitur Utama

- Interface web yang sederhana dan responsif menggunakan Bootstrap
- Visualisasi grafik fungsi keanggotaan untuk setiap variabel input
- Visualisasi hasil defuzzifikasi dengan penanda derajat keanggotaan
- Sistem aturan fuzzy komprehensif dengan 81 rules
- Real-time computation menggunakan scikit-fuzzy

## Tech Stack

- **Backend**: Flask 3.1.1
- **Fuzzy Logic**: scikit-fuzzy 0.5.0
- **Data Processing**: NumPy 2.2.6
- **Visualization**: Matplotlib 3.10.3
- **Frontend**: HTML5, Bootstrap 4.5.2
- **Server**: Gunicorn 23.0.0 (production ready)

## Instalasi

### Prerequisites

Pastikan Python 3.8 atau versi lebih baru sudah terinstall di sistem Anda.

### Langkah Instalasi

1. Clone repository ini

```bash
git clone https://github.com/edi-mj/prediksi-biaya-listrik-fuzzy.git
cd prediksi-harga-rumah-fuzzy
```

2. Buat virtual environment (opsional tapi direkomendasikan)

```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows
```

3. Install dependencies

```bash
pip install -r requirements.txt
```

## Cara Penggunaan

### Development Mode

Jalankan aplikasi dalam mode development:

```bash
python app.py
```

Aplikasi akan berjalan di `http://localhost:5000`

### Production Mode

Untuk deployment production menggunakan Gunicorn:

```bash
gunicorn app:app
```

## Struktur Proyek

```
prediksi-harga-rumah-fuzzy/
├── app.py                    # Main Flask application
├── fuzzy_logic.py           # Fuzzy system logic & rules
├── requirements.txt         # Project dependencies
├── templates/
│   └── index.html          # Frontend interface
└── static/
    └── images/             # Generated fuzzy graphs
```

## Metodologi Fuzzy

### Variabel Input

1. **Luas Rumah** (0-250 m²)

   - Standard: 0-55 m²
   - Medium: 40-120 m²
   - Besar: 105-250 m²

2. **Daya Listrik** (0-2200 VA)

   - Rendah: 0-900 VA
   - Sedang: 400-1400 VA
   - Tinggi: 900-2200 VA

3. **Perlengkapan Elektronik** (0-18 unit)

   - Sedikit: 0-7 unit
   - Normal: 5-13 unit
   - Banyak: 11-18 unit

4. **Pendapatan Ekonomi** (0-10 juta Rp)
   - Rendah: 0-2.5 juta
   - Sedang: 2-6.5 juta
   - Tinggi: 6-10 juta

### Variabel Output

**Biaya Pemakaian** (0-1200 ribu Rp)

- Rendah: 0-300 ribu
- Sedang: 200-500 ribu
- Tinggi: 400-1200 ribu

### Membership Functions

Sistem menggunakan kombinasi fungsi keanggotaan:

- **Trapezoidal (trapmf)**: untuk nilai ekstrem di awal dan akhir range
- **Triangular (trimf)**: untuk nilai tengah

## Contoh Penggunaan

Masukkan nilai berikut pada form:

- Luas Rumah: 60 m²
- Daya Listrik: 1300 VA
- Perlengkapan Elektronik: 10 unit
- Pendapatan Ekonomi: 5.0 juta

Sistem akan menghitung dan menampilkan prediksi biaya pemakaian listrik beserta visualisasi grafik fungsi keanggotaan dan hasil defuzzifikasi.

## Dependencies

Semua dependencies dapat dilihat di file `requirements.txt`. Beberapa library utama:

- Flask: Web framework
- scikit-fuzzy: Fuzzy logic computation
- matplotlib: Graph visualization
- numpy: Numerical operations
- gunicorn: WSGI HTTP server

## Kontribusi

Kontribusi sangat diterima. Silakan buat pull request atau laporkan issue jika menemukan bug atau memiliki saran perbaikan.

## Lisensi

Proyek ini menggunakan lisensi MIT. Anda bebas menggunakan, memodifikasi, dan mendistribusikan kode ini.

## Author

Dikembangkan sebagai tugas akhir mata kuliah Kecerdasan Komputasional yaitu implementasi sistem inferensi fuzzy untuk prediksi biaya pemakaian listrik rumah tangga.
