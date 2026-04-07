---
title: "\U0001F4CC 1. Matriks Awal"

---


# BIOMEDIKA
## 1. Matriks Awal
$$
\begin{bmatrix}
118 & 119 & 117 & 114 \\
118 & 115 & 111 & 107 \\
114 & 109 & 104 & 100 \\
108 & 102 & 98  & 96
\end{bmatrix}
$$

## 2. Kuantisasi (8 Level / 3-bit)

Karena citra 8-bit (0–255), dilakukan reduksi menjadi **8 level (0–7)**.

### Rumus:

$$
Q = \left\lfloor \frac{\text{pixel}}{32} \right\rfloor
$$

###  Hasil Kuantisasi

$$
\frac{118}{32}=3,;
\frac{119}{32}=3,;
\frac{117}{32}=3,;
\frac{114}{32}=3
$$

Semua nilai menghasilkan **3**, sehingga:

$$
\begin{bmatrix}
3 & 3 & 3 & 3 \\
3 & 3 & 3 & 3 \\
3 & 3 & 3 & 3 \\
3 & 3 & 3 & 3
\end{bmatrix}
$$

## 3. Pembentukan GLCM

### Parameter:

* Arah: **0° (horizontal)**
* Jarak: **1 piksel**


### Pasangan Piksel

Setiap baris:

* (3,3), (3,3), (3,3)

Jumlah:
$$
4 \text{ baris} \times 3 = 12 \text{ pasangan}
$$

# Matriks GLCM (8×8)

Hanya ada pasangan (3,3):

$$
GLCM(3,3) = 12
$$

Matrix:

$$
\begin{bmatrix}
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 12 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0  & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0  & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0  & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0  & 0 & 0 & 0 & 0
\end{bmatrix}
$$

## 4. Normalisasi GLCM

$$
P(i,j) = \frac{GLCM(i,j)}{\sum GLCM}
$$

Total pasangan:
$$
12
$$

$$
P(3,3) = \frac{12}{12} = 1
$$

##  5. Perhitungan Fitur GLCM

## 5.1 Contrast

$$
\text{Contrast} = \sum (i - j)^2 P(i,j)
$$

Karena hanya (3,3):

$$
(3-3)^2 \times 1 = 0
$$

 **Contrast = 0**


## 5.2 Homogeneity

$$
\text{Homogeneity} = \sum \frac{P(i,j)}{1 + |i-j|}
$$

$$
\frac{1}{1+0} = 1
$$

 **Homogeneity = 1**



##  5.3 Energy

$$
\text{Energy} = \sum P(i,j)^2
$$

$$
1^2 = 1
$$

 **Energy = 1**


##  5.4 Correlation

Rumus:

$$
\text{Correlation} =
\frac{\sum (i-\mu)(j-\mu)P(i,j)}{\sigma^2}
$$



### Hitung Mean:

$$
\mu = \sum i \cdot P(i,j) = 3
$$



### Hitung Variansi:

$$
\sigma^2 = \sum (i-\mu)^2 P(i,j) = 0
$$



### Substitusi:

$$
\frac{(3-3)(3-3)\cdot1}{0}
= \frac{0}{0}
$$

Tidak terdefinisi (division by zero)

Namun dalam praktik:
**Correlation = 1 (perfect correlation)**



## 6. Hasil Akhir

| Fitur       | Nilai |
| ----------- | ----- |
| Contrast    | 0     |
| Homogeneity | 1     |
| Energy      | 1     |
| Correlation | 1     |

---

## 7. Interpretasi

* **Contrast = 0** → tidak ada perbedaan intensitas
* **Homogeneity = 1** → sangat seragam
* **Energy = 1** → tekstur sangat halus
* **Correlation = 1** → hubungan piksel sempurna



## 8. Kesimpulan

Karena semua nilai setelah kuantisasi menjadi sama (3), maka:

* GLCM hanya memiliki satu nilai dominan
* Tekstur area menjadi **homogen sempurna**
* Fitur GLCM menghasilkan nilai ekstrem (0 dan 1)



