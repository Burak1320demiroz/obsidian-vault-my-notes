---
title: Polynomial and Coons Surfaces
date: 2026-06-26
tags:
  - math
  - geometry
  - surfaces
  - coons
  - bilinear
  - biquadratic
aliases:
  - Polinom ve Coons Yüzeyleri
  - Coons Yamaları
---

# Polynomial and Coons Surfaces

## 1. Polinom Yüzeyleri ve Parametrik Gösterimleri

Eğrilerde tek bir parametre ($t$) kullanırken, yüzeylerde iki boyutlu bir ağ oluşturmak için iki parametre ($u$ ve $w$ veya $u$ ve $v$) kullanılır.

### Genel Formül

Eğrilerin Kartezyen çarpım mantığıyla yüzey denklemi şu hali alır:

$$P(u,w) = \sum_{i} \sum_{j} u^i w^j P_{ij}$$

Burada $P_{ij}$, yüzeyi tanımlayan kontrol noktalarıdır.

## 2. Bikvadratik Polinom Yüzeyleri ve Dokuz Nokta Yöntemi

Kuadratik (2. dereceden) iki eğrinin çarpımı ile oluşan yüzeylere "Bikvadratik Yüzey" denir.

> [!info] Dokuz Nokta Yöntemi
> Bu yüzeyi tanımlamak için $u$ yönünde 3, $w$ yönünde 3 olmak üzere toplam **9 adet kontrol noktasına** ($P_{00}$'dan $P_{22}$'ye kadar bir kafes) ihtiyaç vardır.

### Matris Formülasyonu

Notlarındaki en kritik gösterim budur. Katsayı matrisi ile kontrol noktaları matrisini (3x3 boyutunda) çarparak yüzey denklemi bulunur:

$$P(u,v) = (u^2, u, 1) \begin{pmatrix} 2 & -4 & 2 \\ -3 & 4 & -1 \\ 1 & 0 & 0 \end{pmatrix} \begin{pmatrix} P_{00} & P_{01} & P_{02} \\ P_{10} & P_{11} & P_{12} \\ P_{20} & P_{21} & P_{22} \end{pmatrix} \begin{pmatrix} 2 & -4 & 2 \\ -3 & 4 & -1 \\ 1 & 0 & 0 \end{pmatrix}^T \begin{pmatrix} v^2 \\ v \\ 1 \end{pmatrix}$$

## 3. Bilineer Yüzey Parametrelendirmesi

Bilineer yüzey, sadece **4 köşe noktası** ($P_{00}, P_{01}, P_{10}, P_{11}$) kullanılarak oluşturulan en basit yüzey yamasıdır. Bu yüzey, Coons yüzeyinin formülündeki "kesişim/fazlalık" kısmını oluşturduğu için çok önemlidir.

### Bilineer Yüzey Denklemi ($P_{ab}$)

$$P_{ab}(u,v) = P_{00}(1-u)(1-v) + P_{01}(1-u)v + P_{10}u(1-v) + P_{11}uv$$

> [!tip] Pratik İpucu
> Hangi noktanın hangi katsayıyı alacağını $u, v$ koordinatlarına bakarak ezberleyebilirsin. Örneğin $P_{00}$ için $u=0, v=0$'dır, bu yüzden $(1-u)(1-v)$ ile çarpılır.

## 4. Coons Yüzeyleri

> [!important] Çok Önemli Konu
> Coons yüzeyi, 4 farklı sınır eğrisinin (alt, üst, sağ, sol) birbirine bağlanmasıyla oluşturulan çok pürüzsüz bir yama tekniğidir. İki adet [[lofted_surfaces|Lofted yüzeyin]] toplanıp, kesişimlerindeki Bilineer yüzeyin çıkarılması mantığına dayanır.

### Sınav Formülü

$$P(u,v) = P_a(u,v) + P_b(u,v) - P_{ab}(u,v)$$

### Formülün Parçaları

#### $P_a(u,v)$ — 1. Lofted Yüzey

Karşılıklı iki sınır eğrisi ile oluşturulur:

$$P_a(u,v) = (1-v)P(u,0) + vP(u,1)$$

> [!note]
> Notlarındaki semboller $u$/$v$ yönlerine göre değişebilir, ana mantık lineer interpolasyondur.

#### $P_b(u,v)$ — 2. Lofted Yüzey

Diğer karşılıklı iki sınır eğrisi ile oluşturulur:

$$P_b(u,v) = (1-u)P(0,v) + uP(1,v)$$

#### $P_{ab}(u,v)$ — Bilineer Yüzey

Fazla hesaplanan köşe noktalarını çıkarmak için kullanılır. Yukarıdaki 3. maddede verilen formülün aynısıdır.

## 5. Öteleme Yüzeyleri (Translation Surfaces)

Bir profil eğrisinin, başka bir kılavuz (yörünge) eğrisi boyunca hareket ettirilmesiyle (ötelenmesiyle) yüzey oluşturma işlemidir. Parametrik olarak iki eğrinin toplamı şeklinde ifade edilir:

$$P(u,v) = C_1(u) + C_2(v)$$

---

> [!warning] Sınav Taktiği
> Coons yüzeyi sorusu geldiğinde gözün korkmasın. Soruda sana 4 adet eğri denklemi verecektir. Sırayla $P_a$ ve $P_b$ Lofted yüzeylerini yazıp, köşe noktalarını çıkararak bulduğun Bilineer yüzeyi denklemden eksi ($-$) olarak düşeceksin.

***
