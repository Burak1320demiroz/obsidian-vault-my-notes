---
title: Geometry Exam Practice
date: 2026-06-26
tags:
  - math
  - geometry
  - exam
  - practice
  - bezier
  - coons
aliases:
  - Geometri Sınav Pratiği
  - Çözümlü Örnekler
---

# Geometry Exam Practice

Üçgensel Bezier, Derece Arttırma ve Coons Yüzeyi konularından çözümlü sınav pratiği soruları.

---

## Soru 1: Üçgensel Bezier Yüzeyleri ($P_{ijk}$ Mantığı)

> [!question] Soru
> 2. dereceden ($n=2$) bir üçgensel Bezier yüzeyinde kaç adet kontrol noktası vardır? $u=0.5, v=0.5, w=0$ parametre değerleri için yüzey denkleminin sonucunu, ilgili kontrol noktaları cinsinden hesaplayınız.

### Çözüm

**1. Nokta Sayısını Bulma:**

Üçgensel Bezier yüzeylerinde kontrol noktası sayısı $\frac{(n+1)(n+2)}{2}$ formülü ile bulunur. $n=2$ için:

$$\frac{3 \times 4}{2} = 6 \text{ adet kontrol noktası}$$

**2. Genel Formülü Yazma:**

$$P(u,v,w) = \sum_{i+j+k=n} P_{ijk} \frac{n!}{i!j!k!} u^i v^j w^k$$

**3. Parametreleri Yerine Koyma:**

Soruda $w=0$ verilmiş. Formülde çarpım durumunda $w$ bulunduğu için, içinde $w$ barındıran (yani $k>0$ olan) tüm terimler sıfır olur. $n=2$ olduğu için sadece $i+j=2$ kuralını sağlayan terimler kalır:

> [!tip] Eleme Kuralı
> $w=0$ olduğunda sadece $P_{200}$, $P_{110}$ ve $P_{020}$ noktalarına ait terimler hayatta kalır.

**4. Hesaplama:**

* $P_{200}$ için ($i=2, j=0, k=0$): $\frac{2!}{2!0!0!} (0.5)^2 (0.5)^0 = 1 \times 0.25 = \mathbf{0.25 \cdot P_{200}}$
* $P_{110}$ için ($i=1, j=1, k=0$): $\frac{2!}{1!1!0!} (0.5)^1 (0.5)^1 = 2 \times 0.25 = \mathbf{0.50 \cdot P_{110}}$
* $P_{020}$ için ($i=0, j=2, k=0$): $\frac{2!}{0!2!0!} (0.5)^0 (0.5)^2 = 1 \times 0.25 = \mathbf{0.25 \cdot P_{020}}$

> [!success] Cevap
> $$P(0.5, 0.5, 0) = 0.25 P_{200} + 0.50 P_{110} + 0.25 P_{020}$$

---

## Soru 2: Bezier Eğrisinde 1 Derece Arttırma

> [!question] Soru
> Kontrol noktaları $P_0(0,0), P_1(3,3), P_2(6,0)$ olan 2. dereceden (Kuadratik) Bezier eğrisinin derecesini 1 arttırarak 3. dereceden (Kübik) yeni kontrol noktalarını ($Q_0, Q_1, Q_2, Q_3$) bulunuz.

### Çözüm

Eski derecemiz $n=2$, yeni derecemiz $n+1 = 3$'tür. Kullanacağımız oran formülü:

$$Q_i = \alpha_i P_{i-1} + (1 - \alpha_i) P_{i} \quad \text{burada} \quad \alpha_i = \frac{i}{n+1}$$

**1. Baştaki ve Sondaki Noktalar Sabittir:**

* $Q_0 = P_0 = \mathbf{(0,0)}$
* $Q_3 = P_2 = \mathbf{(6,0)}$

**2. Ara Noktaları Hesaplama:** Formüldeki paydamız yeni derece olan 3'tür.

* $i=1$ için ($\alpha_1 = 1/3$):

$$Q_1 = \frac{1}{3}P_0 + \frac{2}{3}P_1 = \frac{1}{3}(0,0) + \frac{2}{3}(3,3) = (0,0) + (2,2) = \mathbf{(2,2)}$$

* $i=2$ için ($\alpha_2 = 2/3$):

$$Q_2 = \frac{2}{3}P_1 + \frac{1}{3}P_2 = \frac{2}{3}(3,3) + \frac{1}{3}(6,0) = (2,2) + (2,0) = \mathbf{(4,2)}$$

> [!success] Cevap
> Yeni kontrol noktaları kafesi: $(0,0), \; (2,2), \; (4,2), \; (6,0)$
> Eğrinin fiziksel şekli hiç değişmemiştir.

---

## Soru 3: Coons Yüzeyi ve Bilineer Yama

> [!question] Soru
> Bir Coons yüzeyi tasarlanırken sınır eğrileri şu şekilde verilmiştir:
> * Alt Sınır: $P(u,0) = (u, 0, 0)$
> * Üst Sınır: $P(u,1) = (u, 1, 0)$
> * Sol Sınır: $P(0,v) = (0, v, 0)$
> * Sağ Sınır: $P(1,v) = (1, v, 0)$
>
> Bu yüzeyi oluştururken formülden çıkarmamız gereken **Bilineer yüzey yamasını ($P_{ab}(u,v)$)** hesaplayınız.

### Çözüm

**1. Köşe Noktalarını Tespit Etme:**

Coons formülünde Bilineer kısmı yazabilmek için önce 4 köşeyi bulmalıyız. Sınır denklemlerinde parametrelere $0$ ve $1$ vererek köşeleri buluruz:

* $P_{00} = P(0,0) = \mathbf{(0,0,0)}$
* $P_{10} = P(1,0) = \mathbf{(1,0,0)}$
* $P_{01} = P(0,1) = \mathbf{(0,1,0)}$
* $P_{11} = P(1,1) = \mathbf{(1,1,0)}$

**2. Bilineer Yüzey Formülünü Yazma:**

$$P_{ab}(u,v) = P_{00}(1-u)(1-v) + P_{01}(1-u)v + P_{10}u(1-v) + P_{11}uv$$

**3. Değerleri Yerine Koyma:**

$$P_{ab}(u,v) = (0,0,0)(1-u)(1-v) + (0,1,0)(1-u)v + (1,0,0)u(1-v) + (1,1,0)uv$$

**4. Denklemi Düzenleme:** Koordinatları $x, y, z$ olarak kendi aralarında toplayalım:

* **X ekseni:** $0 + 0 + u(1-v) + uv = u - uv + uv = \mathbf{u}$
* **Y ekseni:** $0 + (1-u)v + 0 + uv = v - uv + uv = \mathbf{v}$
* **Z ekseni:** Her terimde sıfır olduğu için $\mathbf{0}$

> [!success] Cevap
> Bu Coons yüzeyi için formülden çıkarılması gereken bilineer yama:
> $$P_{ab}(u,v) = \mathbf{(u, \; v, \; 0)}$$

***