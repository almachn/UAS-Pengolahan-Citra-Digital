# Deteksi Pemutihan Karang Menggunakan Pemrosesan Citra

Proyek ini bertujuan untuk mendeteksi dan menghitung persentase area pemutihan karang pada citra menggunakan teknik pemrosesan citra dengan OpenCV dan NumPy.

## Daftar Isi
- [Pendahuluan](#pendahuluan)
- [Instalasi](#instalasi)
- [Penggunaan](#penggunaan)
- [Deskripsi Fungsi](#deskripsi-fungsi)
- [Contoh Hasil](#contoh-hasil)
- [Pemrosesan Dataset](#pemrosesan-dataset)

## Pendahuluan
Pemutihan karang adalah fenomena yang menunjukkan stres pada terumbu karang, sering kali ditandai dengan perubahan warna menjadi putih. Proyek ini menggunakan pemrosesan citra untuk mendeteksi dan mengukur sejauh mana pemutihan terjadi pada dataset citra.

## Instalasi
Untuk menjalankan proyek ini, instal dependensi berikut:

```bash
pip install opencv-python numpy matplotlib pandas
```

## Penggunaan
Untuk memproses dan memvisualisasikan hasil deteksi pemutihan karang, ikuti langkah-langkah berikut:

1. Letakkan citra karang dalam sebuah folder.
2. Perbarui nilai `dataset_path` dengan path folder Anda.
3. Jalankan skrip untuk melihat visualisasi dan mendapatkan persentase pemutihan.

## Deskripsi Fungsi

**detect_white_areas(image_rgb)**
Mengonversi citra RGB ke HSV dan membuat mask untuk mendeteksi area putih yang menunjukkan pemutihan karang.

**Parameter:**
- `image_rgb`: Citra input dalam format RGB.

**Mengembalikan:**
- Mask biner yang menyoroti area putih.

**morphological_operations(binary_image)**
Membersihkan noise pada mask biner menggunakan operasi morfologi (closing dan opening).

**Parameter:**
- `binary_image`: Citra biner input.

**Mengembalikan:**
- Citra biner yang telah dibersihkan.

**calculate_bleaching_percentage(binary_image)**
Menghitung persentase piksel putih (pemutihan) pada citra biner.

**Parameter:**
- `binary_image`: Citra biner input.

**Mengembalikan:**
- Persentase area pemutihan.

### process_coral_image(image_path)
Memproses satu citra karang untuk mendeteksi dan menghitung pemutihan.

**Parameter:**
- `image_path`: Path ke citra karang.

**Mengembalikan:**
- `bleaching_percentage`: Persentase area pemutihan.
- `image_rgb`: Citra asli dalam format RGB.
- `mask_white`: Mask biner dari area pemutihan yang terdeteksi.
- `morphed_image`: Citra biner yang telah dibersihkan setelah operasi morfologi.

### process_dataset(dataset_path)
Memproses semua citra dalam folder dataset dan memvisualisasikan hasilnya.

**Parameter:**
- `dataset_path`: Path ke folder dataset citra.

Contoh Kode:
```python
process_dataset("path/to/your/dataset")
```

#### Visualisasi:
Skrip menampilkan empat plot untuk setiap citra:
1. Citra input (RGB)
2. Mask pemutihan
3. Hasil operasi morfologi
4. Persentase pemutihan pada judul

## Contoh Hasil
Setelah diproses, visualisasi akan ditampilkan dan persentase pemutihan akan dicatat untuk setiap citra.

Tata letak visualisasi sampel:
- Kiri atas: Citra asli RGB.
- Kanan atas: Mask biner untuk area pemutihan.
- Kiri bawah: Citra yang dibersihkan dengan operasi morfologi.
- Kanan bawah: Judul menampilkan persentase pemutihan.

## Pemrosesan Dataset
Hasil untuk setiap citra disimpan dalam sebuah list dan dapat dengan mudah dikonversi menjadi DataFrame untuk diekspor.

```python
results_df = pd.DataFrame(results)
results_df.to_csv("bleaching_results.csv", index=False)
```


