# PA-PC_202231502_NanaSukarna_E

Repository ini adalah UAS dari mata kuliah Pengolahan Citra Digital

## Teori Pendukung

### Filterering Citra
Filter adalah alat untuk memproses data yang mempunyai ciri mengambil data asli untuk memproduksi data hasil sebagaimana yang diinginkan. Dalam pengolahan citra, respon perambatan filter memberikan gambaran bagaimana pixel-pixel pada citra diproses. (Gonzales dan Woods, 1992:119)
Pemfilteran domain spasial adalah proses manipulasi kumpulan pixel dari sebuah citra untuk menghasilkan citra baru. Pemfilteran domain spasial digunakan untuk peningkatan kualitas citra dan perbaikan citra.

#### Filter Mean
salah satu filter linier adalah filter rata-rata dari intensitas pada beberapa pixel lokal dimana setiap pixel akan digantikan nilainya dengan rata-rata dari nilai intensitas pixel tersebut dengan pixel-pixel tetangganya, dan jumlah pixel tetangga yang dilibatkan tergantung pada filter yang dirancang.

#### Filter Median
Suatu jendela yang memuat sejumlah pixel ganjil. Jendela digeser titik demi titik pada seluruh daerah citra. Pada setiap pergeseran dibuat jendela baru. Titik tengah dari jendela ini diubah dengan nilai median dari jendela tersebut

## Tata Cara Pengerjaan

### Import Library
import cv2
import numpy as np
import matplotlib.pyplot as plt

- cv2: Library OpenCV untuk pengolahan gambar dan komputer visi.
- numpy as np: Library untuk operasi numerik, digunakan di sini untuk pembuatan kernel mean filtering.
- matplotlib.pyplot as plt: Library untuk plotting dan visualisasi data.

### Membaca gambar
image_path = 'foto_diri.jpeg'
original_image = cv2.imread(image_path, cv2.IMREAD_COLOR)

- image_path: Path gambar yang akan dibaca.
- original_image: Membaca gambar dari path yang diberikan ke dalam format BGR menggunakan OpenCV (cv2.IMREAD_COLOR).

### Konversi Ke Grayscale
gray_image = cv2.cvtColor(original_image, cv2.COLOR_BGR2GRAY)

- cv2.cvtColor: Fungsi untuk mengubah warna ruang piksel, dalam hal ini dari BGR ke grayscale.

### Median Filtering
median_filtered_image = cv2.medianBlur(original_image, 5)

- cv2.medianBlur: Fungsi untuk menerapkan median filtering pada gambar.
- 5: Ukuran kernel untuk median filter.

### Mean Filtering
kernel = np.ones((3, 3), np.float32) / 9
mean_filtered_image = cv2.filter2D(gray_image, -1, kernel)

- np.ones((3, 3), np.float32) / 9: Membuat kernel berukuran 3x3 dengan nilai 1, kemudian dibagi 9 untuk mean filtering.
- cv2.filter2D: Fungsi untuk menerapkan kernel yang diberikan ke citra grayscale (gray_image) untuk mean filtering.

### Menampilkan Hasil dengan Matplotlib
plt.figure(figsize=(10, 10))

#Gambar asli
plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(original_image, cv2.COLOR_BGR2RGB))
plt.title('Citra Asli')
plt.axis('on')

#Gambar setelah median filtering
plt.subplot(2, 2, 2)
plt.imshow(cv2.cvtColor(median_filtered_image, cv2.COLOR_BGR2RGB))
plt.title('Setelah filter median')
plt.axis('on')

#Gambar asli dalam grayscale
plt.subplot(2, 2, 3)
plt.imshow(gray_image, cmap='gray')
plt.title('Citra Asli (Grayscale)')
plt.axis('on')

#Gambar setelah mean filtering
plt.subplot(2, 2, 4)
plt.imshow(mean_filtered_image, cmap='gray')
plt.title('Citra setelah Mean Filter')
plt.axis('on')

plt.tight_layout()
plt.show()


- plt.figure(figsize=(10, 10)): Membuat figure baru dengan ukuran 10x10 inci.
- plt.subplot(2, 2, 1), plt.subplot(2, 2, 2), dan seterusnya: Membuat subplot dengan 2 baris dan 2 kolom.
- plt.imshow: Menampilkan gambar dengan menggunakan colormap yang sesuai (RGB untuk gambar berwarna dan grayscale untuk gambar grayscale).
- plt.axis('on'): Menampilkan sumbu pada setiap subplot.
- plt.tight_layout(): Mengatur tata letak subplot agar terlihat lebih rapi.
- plt.show(): Menampilkan semua subplot yang telah didefinisikan.








