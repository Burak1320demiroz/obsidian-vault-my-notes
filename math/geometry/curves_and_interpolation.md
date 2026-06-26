---
title: Curves and Interpolation
date: 2026-06-26
tags:
  - math
  - geometry
  - interpolation
  - polynomials
  - bezier
  - bernstein
  - lagrange
aliases:
  - Eğriler ve İnterpolasyon
---

# Curves and Interpolation

## 1. Polinom İnterpolasyonu

### Doğrunun Denklemi ve Parametrik Gösterim

Doğrular ve eğriler parametrik olarak ifade edilir. Bu yaklaşımda bir $t$ parametresi kullanılır ve genellikle $t \in [0,1]$ aralığında değerlendirilir.

#### Doğrunun Parametrik Denklemi

İki nokta ($P_0$ ve $P_1$) arasındaki doğru parçasının denklemi şu şekilde ifade edilir:

$$P(t) = P_0 + (P_1 - P_0)t$$

Bu denklem düzenlendiğinde interpolasyonun en temel hali olan şu formül elde edilir:

$$P(t) = (1-t)P_0 + tP_1$$

### Polinom İnterpolasyonu Temelleri

Verilen noktalardan geçen (noktaları tam olarak sağlayan) polinomları bulma işlemidir.

#### Kübik Bir Polinom Formu

$$P(t) = at^3 + bt^2 + ct + d$$

Dört nokta ($P_0, P_1, P_2, P_3$) verildiğinde ve parametreler eşit aralıklı $t = 0, \frac{1}{3}, \frac{2}{3}, 1$ olarak seçildiğinde, polinomun katsayıları bu noktaların denklemde yerine konmasıyla ($P(0)=P_0$, $P(1/3)=P_1$ vb.) bir denklem sistemi çözülerek bulunur.

## 2. Lagrange Polinomları

Lagrange interpolasyonu, verilen tüm kontrol noktalarından tam olarak geçen bir eğri oluşturmak için kullanılır.

### Lagrange Baz Polinomu Formülü

Her bir kontrol noktası $P_i$ için bir baz fonksiyonu $L_i^n(t)$ oluşturulur:

$$L_i^n(t) = \frac{\prod_{j \neq i} (t - t_j)}{\prod_{j \neq i} (t_i - t_j)}$$

### Eğri Denklemi

$$P(t) = \sum_{i=0}^n P_i L_i^n(t)$$

### Derecelerine Göre Lagrange Polinomları

#### Lineer (1. Derece)

$t_0=0, t_1=1$ için:

$$L_0^1(t) = 1-t$$

$$L_1^1(t) = t$$

#### Kuadratik (2. Derece)

$t_0=0, \; t_1=1/2, \; t_2=1$ için:

$$L_0^2(t) = \frac{(t-1/2)(t-1)}{(0-1/2)(0-1)} = 2t^2 - 3t + 1$$

$$L_1^2(t) = \frac{(t-0)(t-1)}{(1/2-0)(1/2-1)} = -4t^2 + 4t$$

$$L_2^2(t) = \frac{(t-0)(t-1/2)}{(1-0)(1-1/2)} = 2t^2 - t$$

#### Kübik (3. Derece)

Eşit aralıklı dört nokta ($t_0=0, \; t_1=1/3, \; t_2=2/3, \; t_3=1$) için $L_0^3(t), L_1^3(t), L_2^3(t), L_3^3(t)$ baz fonksiyonları hesaplanır.

## 3. Bezier Eğrisi ve Bernstein Polinomları

Lagrange'ın aksine Bezier eğrileri her zaman kontrol noktalarından geçmek zorunda değildir (başlangıç ve bitiş hariç), kontrol noktaları eğriyi bir mıknatıs gibi kendilerine doğru çeker. Bu eğrilerin temeli Bernstein polinomlarına dayanır.

### Bernstein Baz Polinomu Formülü

$$B_i^n(t) = \binom{n}{i} t^i (1-t)^{n-i}$$

### Bezier Eğrisi Denklemi

$t \in [0,1]$ olmak üzere:

$$P(t) = \sum_{i=0}^n P_i B_i^n(t)$$

### Derecelerine Göre Bezier Eğrileri

#### Lineer (1. Derece)

2 kontrol noktası ($P_0, P_1$):

$$B_0^1(t) = 1-t$$

$$B_1^1(t) = t$$

$$P(t) = P_0(1-t) + P_1t$$

> [!tip] Not
> Bu da Lagrange ve doğrudan interpolasyon ile aynıdır.

#### Kuadratik (2. Derece)

3 kontrol noktası ($P_0, P_1, P_2$):

$$B_0^2(t) = (1-t)^2$$

$$B_1^2(t) = 2t(1-t)$$

$$B_2^2(t) = t^2$$

$$P(t) = P_0(1-t)^2 + P_1(2t(1-t)) + P_2t^2$$

#### Kübik (3. Derece)

4 kontrol noktası ($P_0, P_1, P_2, P_3$):

$$B_0^3(t) = (1-t)^3$$

$$B_1^3(t) = 3t(1-t)^2$$

$$B_2^3(t) = 3t^2(1-t)$$

$$B_3^3(t) = t^3$$

***
