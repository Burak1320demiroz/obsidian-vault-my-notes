---
title: Halkalar Teorisi Sınav Özeti
date: 2026-06-26
tags:
  - math
  - abstract-algebra
  - rings
aliases:
  - Soyut Cebir Sınav Özeti
---
## 1. Halka (Ring) Olma Şartları

Bir $(R,+,\cdot)$ üçlüsünün **halka** olabilmesi için 3 temel şart vardır:

* $(R,+)$ bir değişmeli grup olmalıdır.
* $R$'de çarpma ($\cdot$) işleminin birleşme özelliği olmalıdır.
* Çarpma işlemi, toplama işlemi üzerine sağdan ve soldan dağılmalıdır: $x(y+z) = xy+xz$ ve $(x+y)z = xz+yz$.

## 2. Özel Halka Tanımları

* **Değişmeli Halka:** Her $x, y \in R$ için $x \cdot y = y \cdot x$ sağlanıyorsa.
* **Birimli Halka:** Çarpmaya göre etkisiz elemanı (birimi) olan halkadır. $e \cdot x = x \cdot e = x$ sağlayan $e \in R$ ($1_{R}$ olarak da yazılır) vardır.
* **Boole Halkası:** Her elemanı *idempotent* olan, yani her $a \in R$ için $a^2=a$ şartını sağlayan halkadır.

> [!important] Sınavlık Kural
> Her Boole halkası kesinlikle **değişmelidir**.

## 3. Halkanın Merkezi ($C(R)$)

Halkanın tüm elemanlarıyla değişmeli olarak çarpılabilen elemanların kümesidir.

* $C(R) = \{a \in R \mid \text{her } b \in R \text{ için } ab=ba\}$

> [!info] Kural
> Bir $R$ halkasının değişmeli olması için gerek ve yeter şart $C(R)=R$ olmasıdır.

## 4. Çarpımsal Ters ve Tersinir Elemanlar Grubu ($U(R)$)

Birimli bir halkada bir $a$ elemanının çarpımsal tersi $a^{-1}$ ile gösterilir ve $a \cdot a^{-1} = 1_{R}$ dir. Tersinir elemanların kümesi $U(R)$ ile gösterilir.

* $U(R)$ boş küme olamaz ($U(R) \neq \emptyset$).
* Halkanın sıfırı tersinir olamaz ($0_{R} \notin U(R)$).

> [!info] Kural
> $U(R)$ kümesi çarpma işlemine göre bir **gruptur**.

## 5. Temel İşlem Kuralları

Sınavda işlem hatası yapmamak için her $x, y \in R$ için şu kurallara dikkat et:

* **Yutan eleman:** $0_{R} \cdot a = a \cdot 0_{R} = 0_{R}$
* **İşaret kuralları:** $(-x)y = -(xy)$ ve $x(-y) = -(xy)$
* **Eksi ile eksinin çarpımı:** $(-x)(-y) = xy$

---

## 6. Althalka (Subring)

> [!warning] Sınavda Kesin Çıkar
> Bir $S$ altkümesinin (boş olmayan) bir $R$ halkasının althalkası olup olmadığını kanıtlamak için *tek tek tüm halka şartlarını göstermene gerek yoktur.*

**Kısayol Testi (Teorem 1.2.6):**
Boş kümeden farklı $S \subseteq R$ kümesinin althalka olması için şu iki şartı sağlaması **gerek ve yeterlidir**:

1. **Farka göre kapalı olmalı:** Her $x, y \in S$ için $x-y \in S$
2. **Çarpmaya göre kapalı olmalı:** Her $x, y \in S$ için $xy \in S$

> [!note] Önemli Notlar
> * Değişmeli bir halkanın her althalkası değişmelidir.
> * Birimli bir halkanın althalkası **birimli olmak zorunda değildir** (Örneğin; $\mathbb{Z}$ birimlidir ama alt halkası olan çift tam sayılar $2\mathbb{Z}$ birimli değildir).

***