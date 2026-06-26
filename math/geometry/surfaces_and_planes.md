---
title: Surfaces and Planes
date: 2026-06-26
tags:
  - math
  - geometry
  - surfaces
  - planes
aliases:
  - Yüzeyler ve Düzlemler
---

# Surfaces and Planes

## 1. Kartezyen Çarpım ile Oluşturulan Yüzeyler

İki farklı parametreye sahip eğrilerin (örneğin $u$ ve $w$ parametreleri) Kartezyen çarpımı kullanılarak yüzeyler inşa edilir.

* Eğrilerin parametrik formları sırasıyla $Q(u) = \sum_{i=1}^n f_i(u)P_i$ ve $R(w) = \sum_{j=1}^m g_j(w)R_j$ olsun.
* Bu iki eğrinin çarpımından doğan yüzey denklemi şu şekildedir:

$$P(u,w) = \sum_{i=1}^n \sum_{j=1}^m f_i(u)g_j(w)P_{ij}$$

## 2. Lineer İnterpolasyon ve Poligon Yüzeyleri

Geometrik modellemede her poligon yüzeyi köşelere ve kenarlara sahiptir.

> [!example] Düzlemsellik Testi
> $P_1=(1,0,0)$, $P_2=(0,1,0)$, $P_3=(1,a,1)$ ve $P_4=(0,-a,0)$ noktalarından geçen bir poligonun düzlemsel olabilmesi (aynı düzlemde yatması) için köşe vektörlerinin lineer bağımlı olması gerekir.
> 
> * $u_1 = P_2 - P_1 = (-1, 1, 0)$ 
> * $u_2 = P_3 - P_1 = (0, a, 1)$ 
> * $u_3 = P_4 - P_1 = (-1, -a, 0)$ 
> * Lineer bağımlılık koşulu olan $\det(u_1, u_2, u_3) = 0$ denklemi çözüldüğünde $a = -1$ bulunur.

## 3. Düzlemin Kapalı Denklemi

Uzaydaki bir düzlemin kapalı denklemi standart olarak $Ax + By + Cz + D = 0$ şeklinde ifade edilir.

* $P_i = (x_i, y_i, z_i)$ olacak şekilde uzayda bilinen 3 noktadan geçen düzlemin kapalı denklemi bir determinant yardımıyla doğrudan sıfıra eşitlenerek bulunur:

$$\begin{vmatrix} x & y & z & 1 \\ x_1 & y_1 & z_1 & 1 \\ x_2 & y_2 & z_2 & 1 \\ x_3 & y_3 & z_3 & 1 \end{vmatrix} = 0$$

## 4. Normali Bilinen Düzlem Denklemi

Bir düzlemi tanımlamanın en pratik yollarından biri, düzleme dik olan normal vektörünü ve düzlem üzerindeki tek bir noktayı kullanmaktır.

* Normal vektörü $N=(n_1, n_2, n_3)$ ve düzlem üzerinde bilinen bir nokta $P=(x_1, y_1, z_1)$ olsun.
* Düzlem içindeki herhangi bir vektör ile normal vektörünün iç çarpımı sıfır olmalıdır: $\langle N, \vec{PP_1} \rangle = 0$.
* Formül: $n_1(x-x_1) + n_2(y-y_1) + n_3(z-z_1) = 0$.

> [!example] Örnek
> Normali $N=(1,1,1)$ olan ve $P=(1,1,1)$ noktasından geçen düzlemin denklemi $1(x-1) + 1(y-1) + 1(z-1) = 0$ işleminden $x+y+z=3$ olarak elde edilir.

## 5. Parametrik Düzlem Denklemi

Düzlem denklemini $x, y, z$ kapalı formu yerine, yön vektörleri ve $u, v$ parametreleri kullanarak ifade etme yöntemidir.

* Üç nokta $P_1, P_2, P_3$ verildiğinde, düzlem içindeki iki yön vektörü $s = P_3 - P_1$ ve $r = P_2 - P_1$ olarak belirlenir.
* Parametrik gösterim (lineer birleşim ile) şu şekildedir:

$$P(u,v) = P_1 + us + vr = P_1 + u(P_3 - P_1) + v(P_2 - P_1)$$

> [!example] Örnek Uygulama
> $P_1=(3,0,0)$, $P_2=(0,3,0)$, $P_3=(0,0,3)$ noktalarından geçen düzlem için denklem; $P(u,v) = (3,0,0) + u(-3, 3, 0) + v(-3, 0, 3)$.
> Bu işlem düzenlendiğinde parametrik sonuç $P(u,v) = (3-3v-3u, 3u, 3v)$ olur. (Not: Buradan kapalı denkleme geçmek istenirse koordinatlar toplanıp yine $x+y+z=3$ denklemi bulunabilir.)

## 6. Üçgensel Düzlem

Belirli sınırları olan bir düzlem yaması (üçgen) oluşturmak için parametrik düzlem denkleminin sınırlandırılmış halidir.

* Yüzey, $P_1, P_2, P_3$ noktalarının ağırlıklı birleşimiyle $P(u,v) = P_1 + u(P_2 - P_1) + v(P_3 - P_1)$ formülü ile elde edilir.
* Kontrol noktalarına ulaşmak parametrelere bağlıdır. Örneğin, $u=1$ ve $v=0$ yazıldığında sonuç doğrudan $P_2$ köşesini verir.

***

