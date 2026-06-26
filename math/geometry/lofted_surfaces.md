---
title: Lofted Surfaces
date: 2026-06-26
tags:
  - math
  - geometry
  - surfaces
  - lofted
  - skinning
aliases:
  - Lofted Yüzeyler
  - Deri Giydirme Yüzeyleri
---

# Lofted Surfaces

Bilgisayar grafiklerinde **yüzey modellemenin** en temel "skinning" (deri giydirme) tekniklerinden biri olan **Lofted Yüzeyler** konusu. İki farklı eğriyi uzayda karşılıklı koyup, aralarına düz bir çarşaf gerer gibi yüzey oluşturma yöntemidir.

## 1. Lofted Yüzeyin Mantığı ve Genel Formülü

Karşı karşıya duran iki ray (sınır eğrisi) düşün: Alt sınır eğrisi $P(u,0)$ ve üst sınır eğrisi $P(u,1)$. Bu iki eğriyi $v$ parametresi boyunca **lineer (doğrusal)** olarak birbirine bağlarsak bir Lofted yüzeyi elde ederiz.

### Genel Formül ($v$ yönünde lineer bağlantı)

$$P(u,v) = (1-v)P(u,0) + vP(u,1) \quad (u,v \in [0,1])$$

> [!warning] Kritik Uyarı
> Bağlantıyı alt-üst yerine sol sınır $P(0,v)$ ile sağ sınır $P(1,v)$ arasında yaparsan, formül bu kez $u$ parametresine göre lineer olur:
> $$P(u,v) = (1-u)P(0,v) + uP(1,v)$$

---

## 2. Sınavda Çözüm Algoritması (3 Altın Adım)

> [!important] Sınavda Karşına Geldiğinde
> Kağıda hemen şu **3 adımı** yazıp sırayla doldurmalısın:
> 1. **Alt Sınır Eğrisini $P(u,0)$ bul:** Verilen noktalara göre alt eğrinin denklemini çıkar (Doğru mu, Bezier mi, Lagrange mı?).
> 2. **Üst Sınır Eğrisini $P(u,1)$ bul:** Üstteki noktalar için polinom katsayılarını ($A, B, C$) sistem çözerek yaz.
> 3. **Ana Formülde Birleştir:** Bulduğun iki vektörü $(1-v)$ ve $v$ katsayılarıyla dağıtıp $x, y, z$ koordinatlarını kendi içlerinde topla.

---

## 3. Sınav Soru Tipi 1 (Bezier + Polinom)

> [!question] Soru
> Alt sınır eğrisi $P_1(-1,0,0), P_2(0,-1,0), P_3(1,0,0)$ noktalarından geçen bir **Kuadratik Bezier**, üst sınır eğrisi ise $P_4(-1,0,1), P_5(0,-1,1), P_6(1,0,1)$ noktalarından geçen bir **Kuadratik Polinom** eğrisidir. Lofted yüzey parametrelendirmesini bulunuz.

### Adım 1: Alt Sınır Eğrisini Yaz (Kuadratik Bezier)

Bernstein baz katsayılarımız: $B_0^2 = (1-u)^2, \; B_1^2 = 2u(1-u), \; B_2^2 = u^2$.

$$P(u,0) = (1-u)^2(-1,0,0) + 2u(1-u)(0,-1,0) + u^2(1,0,0)$$

Vektörleri dağıtıp topladığımızda alt sınırımız hazır:

$$P(u,0) = (2u-1, \; 2u^2-2u, \; 0)$$

### Adım 2: Üst Sınır Eğrisini Çöz (Kuadratik Polinom)

Polinom formumuz: $P(u,1) = Au^2 + Bu + C$. Verilen noktaları $u = 0, \frac{1}{2}, 1$ noktalarına yerleştiririz:

* $u=0 \Rightarrow C = P_4 = (-1,0,1)$
* $u=\frac{1}{2} \Rightarrow \frac{A}{4} + \frac{B}{2} + C = P_5(0,-1,1) \Rightarrow A + 2B = (4,-4,0)$
* $u=1 \Rightarrow A + B + C = P_6(1,0,1) \Rightarrow A + B = (2,0,0)$

Bu iki denklemi birbirinden çıkardığımızda $B = (2,-4,0)$ ve dolayısıyla $A = (0,4,0)$ bulunur. Yerine koyarsak üst sınırımız:

$$P(u,1) = (2u-1, \; 4u^2-4u, \; 1)$$

### Adım 3: Yüzeyi Formülde Birleştir

$$P(u,v) = (1-v) P(u,0) + v P(u,1)$$

* **X ekseni:** $(1-v)(2u-1) + v(2u-1) = \mathbf{2u-1}$
* **Y ekseni:** $(1-v)(2u^2-2u) + v(4u^2-4u) = (2u^2-2u)(1+v) = \mathbf{2u(u-1)(v+1)}$
* **Z ekseni:** $(1-v)(0) + v(1) = \mathbf{v}$

> [!success] Cevap
> $$P(u,v) = \Big(2u-1, \; 2u(u-1)(v+1), \; v\Big)$$

---

## 4. Sınav Soru Tipi 2 (Doğru + Polinom)

> [!question] Soru
> Alt sınır eğrisi $P_1(-1,-1,0)$ ve $P_2(1,-1,0)$ noktalarından geçen bir **doğru parçası**, üst sınır eğrisi ise $P_3(-1,1,0), P_4(0,1,1), P_5(1,1,0)$ noktalarından geçen bir **kuadratik polinom** olsun. Lofted yüzey yaması denklemini bulunuz.

### Adım 1: Alt Sınır (Doğru Denklemi)

$$P(u,0) = (1-u)P_1 + uP_2 = (1-u)(-1,-1,0) + u(1,-1,0) = (2u-1, \; -1, \; 0)$$

### Adım 2: Üst Sınır (Kuadratik Polinom)

$P(u,1) = Au^2 + Bu + C$ denkleminde noktaları $0, \frac{1}{2}, 1$ aralığına oturtalım:

* $u=0 \Rightarrow C = (-1,1,0)$
* $u=\frac{1}{2} \Rightarrow \frac{A}{4} + \frac{B}{2} + C = (0,1,1) \Rightarrow A + 2B = (4,0,4)$
* $u=1 \Rightarrow A + B + C = (1,1,0) \Rightarrow A + B = (2,0,0)$

Sistem çözüldüğünde katsayılar $B = (2,0,4)$ ve $A = (0,0,-4)$ gelir. Üst sınır denklemimiz:

$$P(u,1) = (2u-1, \; 1, \; -4u^2+4u)$$

### Adım 3: Birleştirme

* **X:** $(1-v)(2u-1) + v(2u-1) = \mathbf{2u-1}$
* **Y:** $(1-v)(-1) + v(1) = \mathbf{2v-1}$
* **Z:** $(1-v)(0) + v(-4u^2+4u) = \mathbf{4uv(1-u)}$

> [!success] Cevap
> $$P(u,v) = \Big(2u-1, \; 2v-1, \; 4uv(1-u)\Big)$$

***
