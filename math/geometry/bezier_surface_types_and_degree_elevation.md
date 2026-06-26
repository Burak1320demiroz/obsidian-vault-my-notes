---
title: Bezier Surface Types and Degree Elevation
date: 2026-06-26
tags:
  - math
  - geometry
  - bezier
  - surfaces
  - degree-elevation
aliases:
  - Bezier Yüzey Tipleri ve Derece Arttırma
---

# Bezier Surface Types and Degree Elevation

## 1. Farklı Tiplerde Bezier Yüzeyi Hesaplamaları

Dikdörtgensel Bezier yüzeyleri, $u$ ve $v$ parametrelerinin derecelerine göre $m \times n$ tipinde isimlendirilir.

### $1 \times 2$ Tipinde Bezier Yüzeyi

Bu yüzey, $u$ yönünde 1. derece (lineer, 2 nokta) ve $v$ yönünde 2. derece (kuadratik, 3 nokta) olmak üzere toplam $2 \times 3 = 6$ kontrol noktasından oluşur.

**Kullanılan Formül:**

$$P(u,v) = \sum_{i=0}^1 \sum_{j=0}^2 B_i^1(u) P_{ij} B_j^2(v)$$

**Açılımı:** Formül $u$ ve $v$ Bernstein polinomları kullanılarak açıldığında, iki farklı kuadratik eğrinin birbiriyle [[lofted_surfaces|Lofted yüzey]] mantığında birleştiği görülür:

$$P(u,v) = (1-u)[P_{00}(1-v)^2 + P_{01}2v(1-v) + P_{02}v^2] + u[P_{10}(1-v)^2 + P_{11}2v(1-v) + P_{12}v^2]$$

> [!warning] Sınav İçin Kritik Uyarı
> Hocanın özellikle vurguladığı bir detay: $1 \times 2$ tipindeki bir yüzey ile $2 \times 1$ tipindeki bir yüzey **aynı değildir**. Bezier yüzeylerinde matris çarpımından dolayı değişme özelliği yoktur.

### $2 \times 3$ Tipinde Bezier Yüzeyi

Bu yüzey, $u$ yönünde kuadratik (3 nokta) ve $v$ yönünde kübik (4 nokta) polinomların çarpımıdır. Toplam 12 kontrol noktası gerektirir ve formül genişleterek her bir $(u)$ ve $(v)$ baz polinomu birbiriyle çarpılır.

---

## 2. Bezier Eğrilerinde Derece Arttırma (Degree Elevation)

> [!info] Amaç
> Bu işlemin amacı, **eğrinin fiziksel şeklini (geometrisini) hiçbir şekilde değiştirmeden**, eğriyi tanımlayan kontrol noktası sayısını bir adet artırmaktır. İki farklı derecedeki eğriyi pürüzsüz şekilde birleştirmek veya eğri üzerinde daha hassas yerel kontroller yapabilmek için kullanılır.

### Temel Mantık

$n$. dereceden bir Bezier eğrisi ($n+1$ adet kontrol noktası vardır), $n+1$. dereceden bir eğri gibi ifade edilir.

### Formül

Eski noktalarımız $P_i$, yeni noktalarımız $Q_i$ olsun. Yeni kontrol noktalarını bulmak için kullanılan oran formülü:

$$Q_i = \alpha_i P_{i-1} + (1 - \alpha_i) P_i$$

### Oran Katsayısı ($\alpha$)

$$\alpha_i = \frac{i}{n+1}$$

> [!tip] Hatırla
> İlk nokta ($Q_0 = P_0$) ve son nokta ($Q_{n+1} = P_n$) her zaman eski eğrinin başlangıç ve bitiş noktalarıyla aynı kalır. Sadece aradaki noktalar değişir.

---

## 3. Sınavda Çıkabilecek Derece Arttırma Örnekleri

### Örnek 1: Kuadratik → Kübik ($n=2 \to 3$)

Eski kontrol noktaları: $P_0, P_1, P_2$ ($n=2$). Yeni derecemiz 3 olduğu için formüldeki paydamız $n+1 = 3$ olacaktır. Dört yeni nokta ($Q_0, Q_1, Q_2, Q_3$) şu şekilde hesaplanır:

* $Q_0 = P_0$
* $i=1$ için $\alpha_1 = 1/3$:

$$Q_1 = \frac{1}{3}P_0 + \frac{2}{3}P_1$$

* $i=2$ için $\alpha_2 = 2/3$:

$$Q_2 = \frac{2}{3}P_1 + \frac{1}{3}P_2$$

* $Q_3 = P_2$

### Örnek 2: Kübik → 4. Derece (Sayısal Çözüm)

> [!note] OCR Düzeltmesi
> Taradığın notlardaki hesaplamaları matematiksel olarak sağlamlaştırdığımda, ilk noktanın OCR hatası nedeniyle $(10,3)$ gibi okunmuş olabileceği, ancak gerçek işlemlerin $P_0=(0,0)$ üzerinden yapıldığı kesinleşmiştir. Çözümü bu doğru formata göre yapılandırdım.

Eski noktalar: $P_0(0,0), \; P_1(1,2), \; P_2(3,2), \; P_3(2,0)$. Burada $n=3$'tür.
Yeni derecemiz $n+1 = 4$ olduğu için oranlarımız bölü 4 üzerinden hesaplanır. Yeni beş kontrol noktası:

* $Q_0 = P_0 = (0,0)$

* $i=1$ için $\alpha_1 = 1/4$:

$$Q_1 = \frac{1}{4}P_0 + \frac{3}{4}P_1 = \frac{1}{4}(0,0) + \frac{3}{4}(1,2) = \mathbf{\left( \frac{3}{4}, \frac{3}{2} \right)}$$

* $i=2$ için $\alpha_2 = 1/2$:

$$Q_2 = \frac{1}{2}P_1 + \frac{1}{2}P_2 = \frac{1}{2}(1,2) + \frac{1}{2}(3,2) = \mathbf{(2, 2)}$$

* $i=3$ için $\alpha_3 = 3/4$:

$$Q_3 = \frac{3}{4}P_2 + \frac{1}{4}P_3 = \frac{3}{4}(3,2) + \frac{1}{4}(2,0) = \mathbf{\left( \frac{11}{4}, \frac{3}{2} \right)}$$

* $Q_4 = P_3 = (2,0)$

> [!success] Sonuç
> Yeni kontrol noktaları: $Q_0(0,0), \; Q_1(3/4, 3/2), \; Q_2(2,2), \; Q_3(11/4, 3/2), \; Q_4(2,0)$
> Eğrinin şekli değişmedi, sadece kontrol noktası sayısı 4'ten 5'e çıktı.

***
