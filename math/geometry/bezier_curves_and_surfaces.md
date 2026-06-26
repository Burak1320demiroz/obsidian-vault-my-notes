---
title: Bezier Curves and Surfaces
date: 2026-06-26
tags:
  - math
  - geometry
  - bezier
  - de-casteljau
  - surfaces
aliases:
  - Bezier Eğrileri ve Yüzeyleri
  - de Casteljau Algoritması
---

# Bezier Curves and Surfaces

## 1. $n$. Dereceden Bezier Eğrileri ve Kontrol Noktaları

Bir Bezier eğrisini tanımlayan en önemli şey kontrol noktalarıdır ve bu noktaların sırası eğrinin şeklini doğrudan etkiler.

* $n$. dereceden bir Bezier eğrisi oluşturmak için $n+1$ adet kontrol noktasına ihtiyaç vardır.

### Genel Formül

$t \in [0,1]$ olmak üzere eğri şu şekilde ifade edilir:

$$P(t) = \sum_{i=0}^n P_i B_i^n(t)$$

### Bernstein Polinomları

Formüldeki $B_i^n(t)$ katsayıları Bernstein baz fonksiyonlarıdır ve Pascal üçgeni mantığıyla (kombinasyon kullanılarak) açılır:

$$B_i^n(t) = \binom{n}{i} t^i (1-t)^{n-i}$$

### En Çok Kullanılan Bezier Dereceleri

#### 1. Derece (Lineer)

2 kontrol noktası vardır ve doğrudan lineer interpolasyon yapar.

$$P(t) = P_0(1-t) + P_1t$$

#### 2. Derece (Kuadratik)

3 kontrol noktası vardır.

$$P(t) = P_0(1-t)^2 + P_1(2t(1-t)) + P_2t^2$$

#### 3. Derece (Kübik)

4 kontrol noktası vardır. Çoğu grafik yazılımının temelidir. Baz fonksiyonları şunlardır:

* $B_0^3(t) = (1-t)^3$
* $B_1^3(t) = 3t(1-t)^2$
* $B_2^3(t) = 3t^2(1-t)$
* $B_3^3(t) = t^3$

---

## 2. de Casteljau Algoritması (Geometrik Bölme)

> [!important] Sınavda Kritik
> Sınavlarda genellikle işlem sorusu olarak gelen çok kritik bir algoritmadır. Polinomları açık açık çarpmak yerine, ardışık lineer interpolasyonlar (geometrik bölmeler) yaparak eğri üzerindeki $t$ noktasını bulmamızı sağlar.

### Özyinelemeli (Recursive) Formül

$$P_i^j = (1-t)P_i^{j-1} + tP_{i+1}^{j-1}$$

### Sınav Tarzı Örnek Çözüm

> [!question] Soru
> Kontrol noktaları $P_0(1,0,1)$, $P_1(2,1,0)$, $P_2(3,2,1)$, $P_3(1,1,1)$ olan kübik Bezier eğrisinde $t = 2/3$ için $P_0^2$ noktasını de Casteljau algoritması ile bulunuz.

**1. Adım (İlk Seviye Bölmeler):** Her ardışık iki nokta arasında $t = 2/3$ oranında yeni noktalar bulunur.

* $P_0^1 = (1 - 2/3)P_0 + (2/3)P_1 = (1/3)(1,0,1) + (2/3)(2,1,0) = \mathbf{(5/3, 2/3, 1/3)}$
* $P_1^1 = (1/3)P_1 + (2/3)P_2 = \mathbf{(8/3, 5/3, 2/3)}$
* $P_2^1 = (1/3)P_2 + (2/3)P_3 = \mathbf{(5/3, 4/3, 1)}$

**2. Adım (İkinci Seviye Bölmeler):** Bulunan yeni noktalar kendi aralarında tekrar işleme sokulur.

* $P_0^2 = (1/3)P_0^1 + (2/3)P_1^1 = (1/3)(5/3, 2/3, 1/3) + (2/3)(8/3, 5/3, 2/3)$

> [!success] Cevap
> $$P_0^2 = \mathbf{(7/3, \; 4/3, \; 5/9)}$$

> [!note] Doğrulama
> Bu işlemin doğruluğu Bernstein polinomlarında doğrudan yerine koyarak $P_0^2 = P_0B_0^2 + P_1B_1^2 + P_2B_2^2$ şeklinde kontrol edilebilir.

---

## 3. Dikdörtgensel Bezier Yüzeyleri

Eğrilerden yüzeylere geçerken, Kartezyen çarpım mantığı kullanılır.

* Bir yönde $m$. derece, diğer yönde $n$. derece bir Bezier yüzeyi oluşturmak için $(m+1) \times (n+1)$ adet kontrol noktasından oluşan bir matris kafesine (grid) ihtiyaç vardır.

### Yüzey Formülü

$u$ ve $v$ parametrelerine bağlı olarak:

$$P(u,v) = \sum_{i=0}^m \sum_{j=0}^n B_i^m(u) P_{ij} B_j^n(v)$$

### Özel Durum: 1×2 Tipinde Yüzey

> [!info] Detay
> $u$ yönünde lineer ($m=1$), $v$ yönünde kuadratik ($n=2$) olan bir yüzeydir. Toplam 6 kontrol noktası ($2 \times 3$) kullanılır.

Bu denklem açıldığında, aslında karşılıklı duran iki kuadratik Bezier eğrisinin ($P_{0j}$ ve $P_{1j}$) birbiriyle [[lofted_surfaces|Lofted yüzey]] mantığında birleştirilmesi olduğu görülür.

Denklem şu hali alır:

$$P(u,v) = (1-u) \sum_{j=0}^2 B_j^2(v)P_{0j} + u \sum_{j=0}^2 B_j^2(v)P_{1j}$$

***
