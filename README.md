# PCD_UAS_202231042_I-Gede-Putu-Bagus-Krisna-Pande_ITPLN
# MEMBUAT LIBRARY
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
Ini merupakan proses pembuatan library yang akan digunakan untuk pemrosesan citra dan numpy digunakan untuk yang berhubungan dengan angka, dan matplotlib.pyplot digunakan untuk memvisualisasi data citra <br>
```python
img = cv2.imread('Foto Bagus.jpg')
```
Ini merupakan proses untuk memuat data gambar yang akan digunakan dalam proses ini yaitu berupa gambar diri <br>
# MENAMPILKAN GAMBAR ASLI
```python
plt.subplot(2, 3, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
```
Ini merupakan proses untuk mempilkan citra asli yang digunakan tanpa adanya pengolahan/pemrosesan yang terjadi di dalamnya. Kode di atas membuat sebuah subplot dalam grid 2x3, menampilkan gambar yang dikonversi dari BGR ke RGB, memberikan judul "Original Image" pada subplot tersebut, dan mematikan tampilan sumbu untuk fokus hanya pada gambar itu sendiri. <br>
# PROSES MENAMPILKAN GAMBAR YANG TELAH DIROTASI
```python
(h, w) = img.shape[:2]
center = (w // 2, h // 2)
M = cv2.getRotationMatrix2D(center, 45, 1.0)
img_rotated = cv2.warpAffine(img, M, (w, h))
plt.subplot(2, 3, 2)
plt.imshow(cv2.cvtColor(img_rotated, cv2.COLOR_BGR2RGB))
plt.title('Rotated Image')
plt.axis('off')
```
Ini merupakan proses untuk memutar gambar 45 derajat ke kiri dengan gambar aslinya menggunakan subplot Matplotlib. Ini merupakan contoh pemrosesan citra dasar yang menggabungkan manipulasi gambar (rotasi) dengan OpenCV dan visualisasi hasil menggunakan Matplotlib. Disini juga berisi judul "Rotated Image" pada subplotnya dan tanpa tampilan sumbu. <br>
# PROSES MENAMPILKAN GAMBAR YANG TELAH DI RESIZE
```python
img_resized = cv2.resize(img, (img.shape[1]//3, img.shape[0]//2))
plt.subplot(2, 3, 3)
plt.imshow(cv2.cvtColor(img_resized, cv2.COLOR_BGR2RGB))
plt.title('Resized Image')
plt.axis('off')
```
Ini merupakan proses untuk mengubah size asli dari gambar/citra aslinya menjadi sepertiga dari lebar asli dan setengah dari tinggi asli. Gambar yang diubah ukurannya kemudian ditampilkan dalam subplot dari grid 2x3 dengan judul "Resized Image" dan tanpa tampilan sumbu. <br>
# PROSES MENAMPILKAN GAMBAR YANG TELAH DI CROP
```python
img_cropped = img[0:img.shape[0]//2, 0:img.shape[1]//2]
plt.subplot(2, 3, 4)
plt.imshow(cv2.cvtColor(img_cropped, cv2.COLOR_BGR2RGB))
plt.title('Cropped Image')
plt.axis('off')
```
Ini merupakan proses pemotongan gambar/citra menggunakan array NumPy dan menampilkannya menggunakan Matplotlib. Gambar asli dipotong menjadi setengah dari tinggi dan setengah dari lebar asli, dan gambar yang dipotong ini kemudian ditampilkan dalam subplot dari grid 2x3 dengan judul "Cropped Image" dan tanpa tampilan sumbu. <br>
# PROSES MENAMPILKAN GAMBAR YANG TELAH DI FLIP
```python
img_flipped = cv2.flip(img, 1)
plt.subplot(2, 3, 5)
plt.imshow(cv2.cvtColor(img_flipped, cv2.COLOR_BGR2RGB))
plt.title('Flipped Image')
plt.axis('off')
```
Ini merupakan proses membalik gambar secara horizontal menggunakan OpenCV dan menampilkannya menggunakan Matplotlib. Gambar asli dibalik secara horizontal dan gambar yang dibalik ini kemudian ditampilkan dalam subplot dari grid 2x3 dengan judul "Flipped Image" dan tanpa tampilan sumbu. <br>
# PROSES MENAMPILKAN GAMBAR YANG TELAH DI TRANSLATE
```python
rows, cols = img.shape[:2]
M_translate = np.float32([[1, 0, 250], [0, 1, 180]])
img_translated = cv2.warpAffine(img, M_translate, (cols, rows))
plt.subplot(2, 3, 6)
plt.imshow(cv2.cvtColor(img_translated, cv2.COLOR_BGR2RGB))
plt.title('Translated Image')
plt.axis('off')
```
Proses ini merupakan proses menggeser/mentranslasi gambar/citra menggunakan OpenCV dan menampilkannya menggunakan Matplotlib. Gambar asli digeser sebesar 250 piksel ke kanan dan 180 piksel ke bawah, kemudian gambar yang ditranslasi ini ditampilkan dalam subplot dari grid 2x3 dengan judul "Translated Image" dan tanpa tampilan sumbu.
# MENAMPILKAN SEMUA GAMBAR YANG TELAH DIOLAH
```python
# Display the original image
plt.subplot(2, 3, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')

# Rotate the image 
(h, w) = img.shape[:2]
center = (w // 2, h // 2)
M = cv2.getRotationMatrix2D(center, 45, 1.0)
img_rotated = cv2.warpAffine(img, M, (w, h))
plt.subplot(2, 3, 2)
plt.imshow(cv2.cvtColor(img_rotated, cv2.COLOR_BGR2RGB))
plt.title('Rotated Image')
plt.axis('off')

# Resize the image 
img_resized = cv2.resize(img, (img.shape[1]//3, img.shape[0]//2))
plt.subplot(2, 3, 3)
plt.imshow(cv2.cvtColor(img_resized, cv2.COLOR_BGR2RGB))
plt.title('Resized Image')
plt.axis('off')

# Crop the image 
img_cropped = img[0:img.shape[0]//2, 0:img.shape[1]//2]
plt.subplot(2, 3, 4)
plt.imshow(cv2.cvtColor(img_cropped, cv2.COLOR_BGR2RGB))
plt.title('Cropped Image')
plt.axis('off')

# Flip the image 
img_flipped = cv2.flip(img, 1)
plt.subplot(2, 3, 5)
plt.imshow(cv2.cvtColor(img_flipped, cv2.COLOR_BGR2RGB))
plt.title('Flipped Image')
plt.axis('off')

# Translate the image 
rows, cols = img.shape[:2]
M_translate = np.float32([[1, 0, 250], [0, 1, 180]])
img_translated = cv2.warpAffine(img, M_translate, (cols, rows))
plt.subplot(2, 3, 6)
plt.imshow(cv2.cvtColor(img_translated, cv2.COLOR_BGR2RGB))
plt.title('Translated Image')
plt.axis('off')

plt.tight_layout()
plt.show()
```
Program ini memberikan demonstrasi tentang bagaimana berbagai operasi manipulasi gambar dapat dilakukan menggunakan OpenCV dan hasilnya divisualisasikan menggunakan Matplotlib. Setiap operasi, mulai dari pemutaran, pengubahan ukuran, pemotongan, pembalikan, hingga translasi, ditampilkan secara jelas pada subplot masing-masing dalam grid 2x3.
