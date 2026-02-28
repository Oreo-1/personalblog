---
layout: post
title: Uji Hipotesis Satu Arah (One-Tailed) dan Dua Arah (Two-Tailed)
date: 2025-05-23 11:00:00 +0800
tags: [Statistics, 🇮🇩]
mathjax: true
image:
  path: /assets/img/12tailed.png
  alt: Perbandingan Uji Satu Arah dan Dua Arah
---

Setelah memahami dasar-dasar pengujian hipotesis, penting untuk membedakan antara uji satu arah (one-tailed) dan uji dua arah (two-tailed). Pilihan ini bergantung pada bagaimana hipotesis alternatif ($$H_1$$) dirumuskan.

## Prasyarat Umum Uji Hipotesis
Sebelum melakukan uji hipotesis, pastikan beberapa asumsi terpenuhi:
1.  **Skala Data**: Data umumnya berskala interval atau rasio (untuk uji rata-rata).
2.  **Pengambilan Sampel**: Sampel diambil secara acak dan representatif dari populasi.
3.  **Normalitas**: Untuk uji-t dengan sampel kecil, data diasumsikan berdistribusi normal. Jika sampel besar ($$n \ge 30$$), asumsi normalitas bisa dilonggarkan berkat Teorema Limit Pusat (CLT).
4.  **Simpangan Baku Populasi ($$\sigma$$)**: Diketahui atau tidaknya $$\sigma$$ menentukan apakah menggunakan uji-Z (jika diketahui atau sampel sangat besar) atau uji-t (jika tidak diketahui dan sampel lebih kecil).
5.  **Tingkat Signifikansi ($$\alpha$$)**: Telah ditetapkan sebelum pengujian, umumnya 0.05.

## Uji Satu Arah (One-Tailed Test)

Uji satu arah digunakan ketika hipotesis alternatif memiliki **arah spesifik**. Kita tertarik untuk mengetahui apakah parameter populasi lebih besar atau lebih kecil dari nilai tertentu, bukan hanya berbeda.

### 1. Uji Satu Arah Kanan (Right-Tailed Test)
Digunakan ketika kita ingin menguji apakah parameter populasi **lebih besar** dari nilai yang dihipotesiskan.
*   $$H_0: \mu \le \mu_0$$ (atau $$H_0: \mu = \mu_0$$)
*   $$H_1: \mu > \mu_0$$
Wilayah penolakan berada di ekor kanan distribusi.

### 2. Uji Satu Arah Kiri (Left-Tailed Test)
Digunakan ketika kita ingin menguji apakah parameter populasi **lebih kecil** dari nilai yang dihipotesiskan.
*   $$H_0: \mu \ge \mu_0$$ (atau $$H_0: \mu = \mu_0$$)
*   $$H_1: \mu < \mu_0$$
Wilayah penolakan berada di ekor kiri distribusi.

## Uji Dua Arah (Two-Tailed Test)

Uji dua arah digunakan ketika hipotesis alternatif hanya menyatakan bahwa parameter populasi **tidak sama** dengan nilai yang dihipotesiskan, tanpa menentukan arah perbedaan (apakah lebih besar atau lebih kecil).
*   $$H_0: \mu = \mu_0$$
*   $$H_1: \mu \neq \mu_0$$
Wilayah penolakan terbagi dua, di kedua ekor distribusi. Oleh karena itu, p-value untuk uji dua arah biasanya dua kali p-value untuk uji satu arah (untuk nilai statistik uji absolut yang sama).

## Statistik Uji

Statistik uji yang umum digunakan untuk menguji rata-rata populasi:

1.  **Uji-t (t-test)**: Digunakan ketika simpangan baku populasi ($$\sigma$$) tidak diketahui dan/atau ukuran sampel kecil ($$n < 30$$).
    $$ t = \frac{\bar{x} - \mu_0}{s/\sqrt{n}} $$
    dengan derajat kebebasan (df) = $$n-1$$.

2.  **Uji-Z (z-test)**: Digunakan ketika simpangan baku populasi ($$\sigma$$) diketahui atau ukuran sampel besar ($$n \ge 30$$), di mana $$s$$ dapat dianggap sebagai estimasi yang baik untuk $$\sigma$$.
    $$ z = \frac{\bar{x} - \mu_0}{\sigma/\sqrt{n}} $$
    (Jika $$\sigma$$ tidak diketahui tapi $$n \ge 30$$, $$s$$ bisa menggantikan $$\sigma$$).

## Penentuan P-Value dan Keputusan

*   **Uji Satu Arah Kanan**: $$p = P(T > t_{\text{hitung}})$$ atau $$p = P(Z > z_{\text{hitung}})$$.
*   **Uji Satu Arah Kiri**: $$p = P(T < t_{\text{hitung}})$$ atau $$p = P(Z < z_{\text{hitung}})$$.
*   **Uji Dua Arah**: $$p = 2 \times P(T > |t_{\text{hitung}}|)$$ atau $$p = 2 \times P(Z > |z_{\text{hitung}}|)$$.

**Keputusan**: Tolak $$H_0$$ jika $$p \text{-value} < \alpha$$.

## Contoh Aplikasi

### Contoh 1: Uji Satu Arah Kanan (Right-Tailed t-test)
Seorang guru yakin rata-rata nilai siswa di kelasnya lebih tinggi dari 75. Sampel 25 siswa diambil, diperoleh rata-rata sampel ($$\bar{x}$$) = 78, dan simpangan baku sampel ($$s$$) = 8. Uji pada $$\alpha = 0.05$$.

*   $$H_0: \mu \le 75$$
*   $$H_1: \mu > 75$$
*   $$n=25, \bar{x}=78, s=8, \alpha=0.05$$
*   $$df = n-1 = 24$$
*   Statistik uji:
    $$ t = \frac{78 - 75}{8/\sqrt{25}} = \frac{3}{8/5} = \frac{3}{1.6} = 1.875 $$
*   P-value: $$P(T > 1.875)$$ dengan $$df=24$$. Dari tabel t atau kalkulator, p-value $$\approx 0.036$$.
*   Keputusan: Karena p-value (0.036) < $$\alpha$$ (0.05), maka **Tolak $$H_0$$**.
*   Kesimpulan: Ada cukup bukti statistik untuk mendukung klaim guru bahwa rata-rata nilai siswa lebih tinggi dari 75.

```r
# Contoh 1: Right-tailed t-test
t_val_ex1 <- 1.875
df_ex1 <- 24
alpha_ex1 <- 0.05
p_value_ex1 <- pt(t_val_ex1, df = df_ex1, lower.tail = FALSE)
print(paste("P-value (Contoh 1):", round(p_value_ex1, 3)))
if (p_value_ex1 < alpha_ex1) {
  print("Tolak H0")
} else {
  print("Gagal Tolak H0")
}
Use code with caution.
Output R:
[1] "P-value (Contoh 1): 0.036"
[1] "Tolak H0"
Use code with caution.
Contoh 2: Uji Satu Arah Kiri (Left-Tailed t-test)
Contoh ini disesuaikan dari materi OCR untuk kejelasan.
Sebuah pabrik mengklaim kadar logam berat dalam produknya tidak melebihi 0.1 mg/L. Seorang regulator ingin menguji apakah ada bukti bahwa kadar logamnya kurang dari 0.1 mg/L (misalnya, untuk menunjukkan efektivitas peraturan baru).
16 sampel air diuji, diperoleh rata-rata sampel (
x
ˉ
x
ˉ
 
) = 0.08 mg/L, dan simpangan baku sampel (
s
s
) = 0.04 mg/L. Uji pada
α
=
0.01
α=0.01
.
H
0
:
μ
≥
0.1
H 
0
​
 :μ≥0.1
(Kadar logam sama dengan atau lebih dari 0.1 mg/L)
H
1
:
μ
<
0.1
H 
1
​
 :μ<0.1
(Kadar logam kurang dari 0.1 mg/L)
n
=
16
,
x
ˉ
=
0.08
,
s
=
0.04
,
α
=
0.01
n=16, 
x
ˉ
 =0.08,s=0.04,α=0.01
d
f
=
n
−
1
=
15
df=n−1=15
Statistik uji:
t
=
0.08
−
0.1
0.04
/
16
=
−
0.02
0.04
/
4
=
−
0.02
0.01
=
−
2.0
t= 
0.04/ 
16
​
 
0.08−0.1
​
 = 
0.04/4
−0.02
​
 = 
0.01
−0.02
​
 =−2.0
P-value:
P
(
T
<
−
2.0
)
P(T<−2.0)
dengan
d
f
=
15
df=15
. Dari tabel t atau kalkulator, p-value
≈
0.032
≈0.032
.
Keputusan: Karena p-value (0.032) >
α
α
(0.01), maka Gagal Tolak
H
0
H 
0
​
 
.
Kesimpulan: Tidak ada cukup bukti statistik pada tingkat signifikansi 1% untuk menyatakan bahwa kadar logam berat rata-rata kurang dari 0.1 mg/L.
(Catatan: Contoh dari materi OCR asli untuk left-tailed test memiliki
t
=
1.0
t=1.0
dan
p
≈
0.841
p≈0.841
. Ini terjadi jika
x
ˉ
=
0.12
x
ˉ
 =0.12
(lebih besar dari
μ
0
=
0.1
μ 
0
​
 =0.1
) saat menguji
H
1
:
μ
<
0.1
H 
1
​
 :μ<0.1
. Jika data sampel berlawanan arah dengan
H
1
H 
1
​
 
, p-value akan besar).
Contoh 3: Uji Dua Arah (Two-Tailed t-test)
Seorang peneliti ingin menguji apakah rata-rata waktu belajar mahasiswa berbeda dari 5 jam per hari. Sampel 36 mahasiswa diambil, diperoleh rata-rata sampel (
x
ˉ
x
ˉ
 
) = 4.5 jam, dan simpangan baku sampel (
s
s
) = 1.2 jam. Uji pada
α
=
0.05
α=0.05
.
H
0
:
μ
=
5
H 
0
​
 :μ=5
H
1
:
μ
≠
5
H 
1
​
 :μ

=5
n
=
36
,
x
ˉ
=
4.5
,
s
=
1.2
,
α
=
0.05
n=36, 
x
ˉ
 =4.5,s=1.2,α=0.05
Karena
n
≥
30
n≥30
, kita bisa gunakan uji-t atau aproksimasi Z. Mari gunakan uji-t dengan
d
f
=
n
−
1
=
35
df=n−1=35
.
Statistik uji:
t
=
4.5
−
5
1.2
/
36
=
−
0.5
1.2
/
6
=
−
0.5
0.2
=
−
2.5
t= 
1.2/ 
36
​
 
4.5−5
​
 = 
1.2/6
−0.5
​
 = 
0.2
−0.5
​
 =−2.5
P-value:
2
×
P
(
T
>
∣
−
2.5
∣
)
2×P(T>∣−2.5∣)
atau
2
×
P
(
T
<
−
2.5
)
2×P(T<−2.5)
dengan
d
f
=
35
df=35
. Dari tabel t atau kalkulator, p-value
≈
2
×
0.0085
=
0.017
≈2×0.0085=0.017
.
Keputusan: Karena p-value (0.017) <
α
α
(0.05), maka Tolak
H
0
H 
0
​
 
.
Kesimpulan: Ada cukup bukti statistik untuk menyatakan bahwa rata-rata waktu belajar mahasiswa berbeda dari 5 jam per hari.
# Contoh 3: Two-tailed t-test
t_val_ex3 <- -2.5
df_ex3 <- 35
alpha_ex3 <- 0.05
p_value_ex3 <- 2 * pt(abs(t_val_ex3), df = df_ex3, lower.tail = FALSE)
print(paste("P-value (Contoh 3):", round(p_value_ex3, 3)))
if (p_value_ex3 < alpha_ex3) {
  print("Tolak H0")
} else {
  print("Gagal Tolak H0")
}
Use code with caution.
R
Output R:
[1] "P-value (Contoh 3): 0.017"
[1] "Tolak H0"
Use code with caution.
Contoh 4: Uji Dua Arah (Two-Tailed Z-test)
Sebuah populasi besar memiliki simpangan baku berat badan (
σ
σ
) = 10 kg. Kita ingin menguji apakah rata-rata berat badan populasi tersebut adalah 70 kg. Sampel 64 orang diambil, diperoleh rata-rata sampel (
x
ˉ
x
ˉ
 
) = 72 kg. Uji pada
α
=
0.01
α=0.01
.
H
0
:
μ
=
70
H 
0
​
 :μ=70
H
1
:
μ
≠
70
H 
1
​
 :μ

=70
σ
=
10
,
n
=
64
,
x
ˉ
=
72
,
α
=
0.01
σ=10,n=64, 
x
ˉ
 =72,α=0.01
Karena
σ
σ
diketahui (atau
n
≥
30
n≥30
), kita gunakan uji-Z.
Statistik uji:
z
=
72
−
70
10
/
64
=
2
10
/
8
=
2
1.25
=
1.6
z= 
10/ 
64
​
 
72−70
​
 = 
10/8
2
​
 = 
1.25
2
​
 =1.6
P-value:
2
×
P
(
Z
>
1.6
)
2×P(Z>1.6)
. Dari tabel Z atau kalkulator,
P
(
Z
>
1.6
)
≈
0.0548
P(Z>1.6)≈0.0548
. Jadi, p-value
≈
2
×
0.0548
=
0.1096
≈2×0.0548=0.1096
.
Keputusan: Karena p-value (0.1096) >
α
α
(0.01), maka Gagal Tolak
H
0
H 
0
​
 
.
Kesimpulan: Tidak ada cukup bukti statistik pada tingkat signifikansi 1% untuk menyatakan bahwa rata-rata berat badan populasi berbeda dari 70 kg.
# Contoh 4: Two-tailed Z-test
z_val_ex4 <- 1.6
alpha_ex4 <- 0.01
p_value_ex4 <- 2 * pnorm(abs(z_val_ex4), lower.tail = FALSE)
print(paste("P-value (Contoh 4):", round(p_value_ex4, 4)))
if (p_value_ex4 < alpha_ex4) {
  print("Tolak H0")
} else {
  print("Gagal Tolak H0")
}
Use code with caution.
R
Output R:
[1] "P-value (Contoh 4): 0.1096"
[1] "Gagal Tolak H0"
Use code with caution.
Implementasi di Excel untuk Menghitung P-Value
Excel menyediakan fungsi untuk menghitung p-value dari uji-t dan uji-Z.
Jenis Uji	Hipotesis Alternatif	Distribusi	Formula Excel
One-Tailed (Right)	
H
1
:
μ
>
μ
0
H 
1
​
 :μ>μ 
0
​
 
t-distribusi	=T.DIST.RT(t, df)
z-distribusi	=1 - NORM.S.DIST(z, TRUE)
One-Tailed (Left)	
H
1
:
μ
<
μ
0
H 
1
​
 :μ<μ 
0
​
 
t-distribusi	=T.DIST(t, df, TRUE)
z-distribusi	=NORM.S.DIST(z, TRUE)
Two-Tailed	
H
1
:
μ
≠
μ
0
H 
1
​
 :μ

=μ 
0
​
 
t-distribusi	=T.DIST.2T(ABS(t), df)
z-distribusi	=2 * (1 - NORM.S.DIST(ABS(z), TRUE))
Keterangan:
t: Nilai statistik uji t yang dihitung.
df: Derajat kebebasan (
n
−
1
n−1
untuk uji satu sampel).
z: Nilai statistik uji z yang dihitung.
ABS(t) atau ABS(z): Nilai absolut dari statistik uji.
TRUE dalam NORM.S.DIST: Mengindikasikan fungsi distribusi kumulatif.
Memilih jenis uji yang tepat (satu arah atau dua arah) adalah langkah krusial dalam pengujian hipotesis dan harus didasarkan pada pertanyaan penelitian sebelum data dianalisis.