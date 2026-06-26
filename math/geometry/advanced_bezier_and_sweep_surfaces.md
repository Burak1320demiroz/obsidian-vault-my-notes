---
title: Advanced Bezier and Sweep Surfaces
date: 2026-06-26
tags:
  - math
  - geometry
  - bezier
  - degree-elevation
  - triangular
  - sweep
  - homogeneous
aliases:
  - İleri Bezier ve Süpürme Yüzeyleri
  - Üçgensel Bezier Yüzeyleri
---

# Advanced Bezier and Sweep Surfaces

## 1. Bezier Yüzeylerinde Derece Arttırma (Degree Elevation)

Yüzeyin fiziksel geometrisini değiştirmeden kontrol noktası ağını genişletmek amacıyla uygulanır.

> [!important] Sınav Notu
> Sınavda tek seferde iki derece birden arttırma sorulduğunda işlem adım adım (iteratif olarak) her derece için ayrı ayrı yürütülür.

### Sınav Soru Tipi: $1 \times 2$ → $3 \times 2$ Geçişi

> [!question] Soru
> Kontrol noktaları $P_{00}=(1,0,0)$, $P_{10}=(2,1,0)$, $P_{01}=(1,1,0)$, $P_{11}=(2,1,1)$, $P_{02}=(1,1,1)$, $P_{12}=(1,1,2)$ olarak verilen $1 \times 2$ tipindeki ($u$ yönünde lineer, $v$ yönünde kuadratik) Bezier yüzeyinin $u$ yönündeki derecesini 2 derece arttırarak $3 \times 2$ tipindeki yeni kontrol noktalarını bulunuz.

### Adım 1: $1 \times 2$ → $2 \times 2$ ($m=1 \rightarrow 2$)

Yeni ara kontrol noktalarına $Q_{ij}$ diyelim. Derece $m=1$ olduğundan formüldeki payda $m+1 = 2$ olur. $u$ yönünde kenar noktaları korunur, orta noktalar doğrusal birleşimle bulunur:

**$j=0$ için (Taban Eğrisi):**

* $Q_{00} = P_{00} = \mathbf{(1,0,0)}$
* $Q_{10} = \frac{1}{2}P_{00} + \frac{1}{2}P_{10} = \mathbf{(1.5, \; 0.5, \; 0)}$
* $Q_{20} = P_{10} = \mathbf{(2,1,0)}$

**$j=1$ için (Orta Eğri):**

* $Q_{01} = P_{01} = \mathbf{(1,1,0)}$
* $Q_{11} = \frac{1}{2}P_{01} + \frac{1}{2}P_{11} = \mathbf{(1.5, \; 1, \; 0.5)}$
* $Q_{21} = P_{11} = \mathbf{(2,1,1)}$

**$j=2$ için (Tavan Eğrisi):**

* $Q_{02} = P_{02} = \mathbf{(1,1,1)}$
* $Q_{12} = \frac{1}{2}P_{02} + \frac{1}{2}P_{12} = \mathbf{(1, \; 1, \; 1.5)}$
* $Q_{22} = P_{12} = \mathbf{(1,1,2)}$

### Adım 2: $2 \times 2$ → $3 \times 2$ ($m=2 \rightarrow 3$)

Elimizdeki $Q_{ij}$ matrisini kullanarak nihai noktalar olan $R_{ij}$ matrisini hesaplayacağız. Mevcut derece $m=2$ olduğundan yeni payda $m+1 = 3$ olacaktır.

Formül: $R_{ij} = \frac{i}{3}Q_{(i-1)j} + (1 - \frac{i}{3})Q_{ij}$

**$j=0$ için:**

* $R_{00} = Q_{00} = \mathbf{(1,0,0)}$
* $R_{10} = \frac{1}{3}Q_{00} + \frac{2}{3}Q_{10} = \mathbf{(4/3, \; 1/3, \; 0)}$
* $R_{20} = \frac{2}{3}Q_{10} + \frac{1}{3}Q_{20} = \mathbf{(5/3, \; 2/3, \; 0)}$
* $R_{30} = Q_{20} = \mathbf{(2,1,0)}$

**$j=1$ için:**

* $R_{01} = Q_{01} = \mathbf{(1,1,0)}$
* $R_{11} = \frac{1}{3}Q_{01} + \frac{2}{3}Q_{11} = \mathbf{(4/3, \; 1, \; 1/3)}$
* $R_{21} = \frac{2}{3}Q_{11} + \frac{1}{3}Q_{21} = \mathbf{(5/3, \; 1, \; 2/3)}$
* $R_{31} = Q_{21} = \mathbf{(2,1,1)}$

**$j=2$ için:**

* $R_{02} = Q_{02} = \mathbf{(1,1,1)}$
* $R_{12} = \frac{1}{3}Q_{02} + \frac{2}{3}Q_{12} = \mathbf{(1, \; 1, \; 4/3)}$
* $R_{22} = \frac{2}{3}Q_{12} + \frac{1}{3}Q_{22} = \mathbf{(1, \; 1, \; 5/3)}$
* $R_{32} = Q_{22} = \mathbf{(1,1,2)}$

---

## 2. Üçgensel Bezier Yüzeyleri (Triangular Bezier Surfaces)

Dörtgensel kafeslerin aksine, üç parametreli ağırlık (barycentric) koordinat sistemini kullanan yüzey modelleme tekniğidir.

### Kontrol Noktası Sayısı Formülü

$n$. dereceden bir üçgensel Bezier yüzeyinin sahip olduğu kontrol noktası ($P_{ijk}$) sayısı:

$$\text{Kontrol Noktası Sayısı} = \frac{(n+1)(n+2)}{2}$$

| Derece ($n$) | Tip | Kontrol Noktası |
|---|---|---|
| 2 | Kuadratik | **6** |
| 3 | Kübik | **10** |
| 4 | Kuartik | **15** |

### Yüzeyin Genel Formülü

$u+v+w=1$ kısıtı altında:

$$P(u,v,w) = \sum_{i+j+k=n} P_{ijk} \frac{n!}{i!j!k!} u^i v^j w^k$$

> [!tip] İki Değişkenli Formata İndirgeme
> Sınavda fonksiyonel hesap yaparken $w = 1-u-v$ dönüşümü doğrudan yerine yazılarak yüzey $P(u,v)$ formatına indirgenir.

---

## 3. Süpürme (Sweep) Yüzeyleri ve Homojen Dönüşüm Matrisleri

Uzayda tanımlı bir profil eğrisinin ($C(u)$), bir geometrik dönüşüm matrisi ($T(v)$) boyunca hareket ettirilmesiyle üretilen yüzeylerdir. Hesabın matris çarpımıyla yürütülebilmesi için homojen koordinatlar ($P=[x,y,z,1]$) kullanılır.

### Genel Formül

$$P(u,v) = C(u) \cdot T(v)$$

### 4×4 Homojen Matris Yapısı ($T$)

$$T = \begin{pmatrix} & \text{3x3 Dönme / Kırpma / Ölçek} & & 0 \\ & & & 0 \\ & & & 0 \\ t_x & t_y & t_z & 1 \end{pmatrix}$$

> [!note]
> Sol alt köşedeki $[t_x, t_y, t_z]$ değerleri öteleme (translation) vektörünü belirtir.

### Sınavda Çıkabilecek En Önemli Süpürme Örnekleri

#### A) Helikoid (Helicoid) Yüzeyi

Bir doğrunun bir eksen etrafında eş zamanlı olarak hem dönmesi hem de o eksen boyunca yükselmesiyle oluşur.

**Profil Eğrisi (Doğru):** $C(u) = (u, 0, 0, 1)$

**$z$ ekseni etrafında $2\pi v$ kadar dönme ve $z$ boyunca $\alpha v$ kadar yükselme matrisi:**

$$T(v) = \begin{pmatrix} \cos(2\pi v) & \sin(2\pi v) & 0 & 0 \\ -\sin(2\pi v) & \cos(2\pi v) & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 0 & \alpha v & 1 \end{pmatrix}$$

> [!success] Helikoid Denklemi
> $$P(u,v) = \Big(u\cos(2\pi v), \; u\sin(2\pi v), \; \alpha v\Big)$$

#### B) Koni Yüzeyi (Cone Surface)

Orijinden başlayıp dairesel kılavuz eğrisine doğru uzanan doğruların doğrusal ölçeklenmesi ile oluşur.

**Profil Eğrisi:** $C(v) = (R\cos v, \; R\sin v, \; H, \; 1)$

**Orijine doğru daralmayı (ölçeklenmeyi) sağlayan $u$ parametrik matrisi:**

$$T(u) = \begin{pmatrix} u & 0 & 0 & 0 \\ 0 & u & 0 & 0 \\ 0 & 0 & u & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix}$$

> [!success] Koni Yüzey Denklemi
> $$P(u,v) = \Big(uR\cos v, \; uR\sin v, \; uH\Big)$$

***
