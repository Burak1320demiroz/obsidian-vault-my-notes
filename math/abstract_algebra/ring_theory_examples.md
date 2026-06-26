---
title: Ring Theory Examples
date: 2026-06-26
tags:
  - math
  - abstract-algebra
  - rings
  - examples
aliases:
  - Halka Teorisi Örnekleri
---

# Ring Theory Examples

### Soru 1: Halka Olup Olmama Durumları

> [!info] Halka Olma Şartı Hatırlatması (Tanım 1.1.1)
> Bir kümenin halka olabilmesi için her şeyden önce toplamaya göre değişmeli bir grup olması şarttır.

**(a) $R=\{0,1,2,3,\dots\}$, $\mathbb{Z}$'nin işlemleri** 

* **Açıklama:** Bu küme doğal sayılar kümesidir ($\mathbb{N}$). Bir kümenin toplama işlemine göre $(R,+)$ grup olabilmesi için, kümedeki **her elemanın toplamaya göre tersinin** de o kümede bulunması gerekir.
* **İspat:** $1 \in R$ olmasına rağmen, toplamaya göre tersi olan $-1 \notin R$'dir. $(R,+)$ bir grup şartını sağlayamadığı için, baştan elenir; $R$ bir halka **değildir**.

**(b) $R=2\mathbb{Z}$** 

* 
**Açıklama:** Çift tam sayılar kümesi bilinen toplama ve çarpma işlemlerine göre bir halkadır (Notlar Örnek 1.1.8'de belirtilen $n\mathbb{Z}$ kuralının birebir aynısıdır).


* **İspat:** 1.  $(2\mathbb{Z}, +)$ değişmeli bir gruptur (Tam sayılar kümesinin altgrubudur, eksi değerleri ve sıfırı barındırır).
2.  Çarpma işlemi birleşmelidir (Tam sayılardan miras kalır).
3.  Çarpma işleminin toplama üzerine dağılma özelliği vardır.
* Sonuç olarak $2\mathbb{Z}$ bir halkadır (Birim elemanı yoktur ancak halka olmak için birimli olmak zorunlu değildir ).



---

### Soru 2: Althalka İspatları

> [!info] Althalka Kısayol Testi (Teorem 1.2.6)
> Boş olmayan bir $S$ kümesinin althalka olması için her $x, y \in S$ için şu ikisinin sağlanması gerek ve yeterdir:
> 1. **Farka göre kapalılık:** $x-y \in S$
> 2. **Çarpmaya göre kapalılık:** $xy \in S$

**(a)** $S=\left\{\left[\begin{matrix}a&b\\ c&d\end{matrix}\right] \mid a+c=b+d\right\}$ 

* **Fark:** $A = \left[\begin{matrix}a_1&b_1\\ c_1&d_1\end{matrix}\right]$ ve $B = \left[\begin{matrix}a_2&b_2\\ c_2&d_2\end{matrix}\right]$ alalım. $A-B = \left[\begin{matrix}a_1-a_2 & b_1-b_2\\ c_1-c_2 & d_1-d_2\end{matrix}\right]$.
Şartı sağlıyor mu? $(a_1-a_2)+(c_1-c_2) = (b_1-b_2)+(d_1-d_2)$ midir?
Denklemi düzenlersek: $(a_1+c_1) - (a_2+c_2) = (b_1+d_1) - (b_2+d_2)$. Verilen şarta göre iki taraf da birbirine eşittir, fark işlemi kapalıdır.
* **Çarpım:** $A \cdot B = \left[\begin{matrix}a_1 a_2 + b_1 c_2 & a_1 b_2 + b_1 d_2\\ c_1 a_2 + d_1 c_2 & c_1 b_2 + d_1 d_2\end{matrix}\right]$.
Şartı sağlıyor mu? 1. sütun toplamı eşittir 2. sütun toplamı olmalı:
Sol taraf (1. Sütun): $a_1 a_2 + b_1 c_2 + c_1 a_2 + d_1 c_2 = a_2(a_1+c_1) + c_2(b_1+d_1)$.
Şartımız gereği $(a_1+c_1) = (b_1+d_1)$ olduğundan, yerine koyarsak: $= (b_1+d_1)(a_2+c_2)$.
Sağ taraf (2. Sütun): $a_1 b_2 + b_1 d_2 + c_1 b_2 + d_1 d_2 = b_2(a_1+c_1) + d_2(b_1+d_1)$.
Yine yerine koyarsak: $= (b_1+d_1)(b_2+d_2)$.
İkinci matrisin şartı gereği $(a_2+c_2) = (b_2+d_2)$ olduğundan, Sol taraf $=$ Sağ taraf olur. Çarpmaya göre kapalıdır. **S bir althalkadır.**

**(b)** $S=\left\{\left[\begin{matrix}a&b\\ 0&a\end{matrix}\right]\right\}$ 

* **Fark:** $\left[\begin{matrix}a_1&b_1\\ 0&a_1\end{matrix}\right] - \left[\begin{matrix}a_2&b_2\\ 0&a_2\end{matrix}\right] = \left[\begin{matrix}a_1-a_2 & b_1-b_2\\ 0 & a_1-a_2\end{matrix}\right]$. Ana köşegenler aynı ve sol alt sıfır. Form bozulmadı, $\in S$.
* **Çarpım:** $\left[\begin{matrix}a_1&b_1\\ 0&a_1\end{matrix}\right] \left[\begin{matrix}a_2&b_2\\ 0&a_2\end{matrix}\right] = \left[\begin{matrix}a_1 a_2 & a_1 b_2 + b_1 a_2\\ 0 & a_1 a_2\end{matrix}\right]$. Ana köşegenler eşit ($a_1 a_2$) ve sol alt sıfır. Form bozulmadı, $\in S$. **S bir althalkadır.**

**(c)** $S=\left\{\left[\begin{matrix}a&0&b\\ 0&c&d\\ 0&0&a\end{matrix}\right]\right\}$ 

* **Fark:** Farka girildiğinde matris konumlarındaki sıfırlar sabit kalır ve $a_{11}$ ile $a_{33}$ hücreleri eşit kalmaya devam eder ($a_1-a_2$). Farka göre kapalıdır.
* **Çarpım:** $\left[\begin{matrix}a_1&0&b_1\\ 0&c_1&d_1\\ 0&0&a_1\end{matrix}\right] \left[\begin{matrix}a_2&0&b_2\\ 0&c_2&d_2\\ 0&0&a_2\end{matrix}\right] = \left[\begin{matrix}a_1 a_2 & 0 & a_1 b_2 + b_1 a_2\\ 0 & c_1 c_2 & c_1 d_2 + d_1 a_2\\ 0 & 0 & a_1 a_2\end{matrix}\right]$. Sonuç matrisinin 1. ve 3. köşegeni eşit ($a_1 a_2$) ve diğer sıfır konumları korunduğu için forma uygundur, $\in S$. **S bir althalkadır.**

**(d)** $S=\left\{\left[\begin{matrix}a&2b\\ b&a\end{matrix}\right]\right\}$ 

* **Fark:** $\left[\begin{matrix}a_1-a_2 & 2(b_1-b_2)\\ b_1-b_2 & a_1-a_2\end{matrix}\right]$. Sağ üst, sol altın tam iki katı. Köşegenler aynı. Form bozulmadı.
* **Çarpım:** $\left[\begin{matrix}a_1&2b_1\\ b_1&a_1\end{matrix}\right] \left[\begin{matrix}a_2&2b_2\\ b_2&a_2\end{matrix}\right] = \left[\begin{matrix}a_1 a_2 + 2b_1 b_2 & 2a_1 b_2 + 2b_1 a_2\\ b_1 a_2 + a_1 b_2 & a_1 a_2 + 2b_1 b_2\end{matrix}\right]$. Köşegenler eştir. Sağ üst elemanı $2$ parantezine alırsak: $2(a_1 b_2 + b_1 a_2)$ olur ki bu da tam olarak sol alt elemanın iki katıdır. Form bozulmadı, $\in S$. **S bir althalkadır.**

---

### Soru 3: $(\mathcal{P}(X), \Delta, \cap)$ Halkası İşlem Tabloları

Kuvvet kümesi $\mathcal{P}(X)$'in, $X=\{a,b,c\}$ için elemanları şunlardır:
Boş küme için $\emptyset$, tekli elemanlar için $A, B, C$, ikili kombinasyonlar için $AB, AC, BC$ ve tamamı için $X$ kısaltmasını kullanalım. Toplam 8 elemanlı bir kümedir.

* **Toplama ($\Delta$ - Simetrik Fark):** İki kümede olup, ortak kısımların atılmasıdır. Bir küme kendisiyle toplanırsa birbirini yok eder ve sonuç boş küme ($\emptyset$) çıkar. Bu özellikten dolayı bu yapı bir Boole halkası karakteristiğindedir.


* **Çarpma ($\cap$ - Kesişim):** İki kümedeki sadece ortak elemanların alınmasıdır.

**Toplama ($\Delta$) Tablosu**

| $\Delta$ | $\emptyset$ | A | B | C | AB | AC | BC | X |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **$\emptyset$** | $\emptyset$ | A | B | C | AB | AC | BC | X |
| **A** | A | $\emptyset$ | AB | AC | B | C | X | BC |
| **B** | B | AB | $\emptyset$ | BC | A | X | C | AC |
| **C** | C | AC | BC | $\emptyset$ | X | A | B | AB |
| **AB** | AB | B | A | X | $\emptyset$ | BC | AC | C |
| **AC** | AC | C | X | A | BC | $\emptyset$ | AB | B |
| **BC** | BC | X | C | B | AC | AB | $\emptyset$ | A |
| **X** | X | BC | AC | AB | C | B | A | $\emptyset$ |

**Çarpım ($\cap$) Tablosu**

| $\cap$ | $\emptyset$ | A | B | C | AB | AC | BC | X |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **$\emptyset$** | $\emptyset$ | $\emptyset$ | $\emptyset$ | $\emptyset$ | $\emptyset$ | $\emptyset$ | $\emptyset$ | $\emptyset$ |
| **A** | $\emptyset$ | A | $\emptyset$ | $\emptyset$ | A | A | $\emptyset$ | A |
| **B** | $\emptyset$ | $\emptyset$ | B | $\emptyset$ | B | $\emptyset$ | B | B |
| **C** | $\emptyset$ | $\emptyset$ | $\emptyset$ | C | $\emptyset$ | C | C | C |
| **AB** | $\emptyset$ | A | B | $\emptyset$ | AB | A | B | AB |
| **AC** | $\emptyset$ | A | $\emptyset$ | C | A | AC | C | AC |
| **BC** | $\emptyset$ | $\emptyset$ | B | C | B | C | BC | BC |
| **X** | $\emptyset$ | A | B | C | AB | AC | BC | X |

---

### Soru 4: Birim Elemanın Tekliği İspatı

**Soru:** $R$ bir halka olsun. Eğer $R$ birimli ise o zaman birim elemanın bir tek olduğunu gösteriniz.

**İspat:** Matematikte tekliği (uniqueness) göstermenin en garantili yolu, sanki iki tane varmış gibi varsayıp, sonunda bunların aslında aynı şey olduğunu kanıtlamaktır.

Varsayalım ki $R$ halkasının $e_1$ ve $e_2$ gibi birbirinden farklı iki tane birim elemanı olsun.

1. $e_1$'i halkanın birim elemanı olarak kabul edelim. Birim eleman tanımı gereği, halkadaki her $a$ elemanı için $a \cdot e_1 = e_1 \cdot a = a$ olmalıdır. Bu durumda $e_2$'yi sıradan bir eleman gibi düşünürsek şu eşitliği yazarız:



$$e_2 \cdot e_1 = e_1 \cdot e_2 = e_2$$


2. Şimdi $e_2$'yi halkanın birim elemanı olarak kabul edelim. Aynı kural gereği, $e_1$'i sıradan bir eleman gibi düşünürsek:

$$e_1 \cdot e_2 = e_2 \cdot e_1 = e_1$$


3. Yukarıdaki iki denkleme dikkatli bakarsak, ikisinde de ortak olan $e_1 \cdot e_2$ çarpımı var. Bu çarpım bir ilk denklemde $e_2$'ye, ikinci denklemde $e_1$'e eşittir.
4. Sonuç olarak: **$e_1 = e_1 \cdot e_2 = e_2$** elde edilir.

Yani, iki farklı birim eleman olamaz; birimli bir halkada birim eleman daima **tektir**.

---

### Soru 5: Çarpımsal Tersin Tekliği İspatı

**Soru:** $R$ birimli bir halka olsun. Eğer $R$ de bir elemanın çarpımsal tersi varsa bir tek olduğunu gösteriniz.

**İspat:**
Yine aynı stratejiyi (olmayana ergiye benzer bir teklik ispatı) kullanacağız.


$R$ birimli bir halka ve birim elemanı $1_R$ olsun. Halkadan herhangi bir $a \in R$ elemanı alalım. Varsayalım ki bu $a$ elemanının, $b$ ve $c$ adında iki farklı çarpımsal tersi olsun.

1. Ters eleman tanımına göre, bir elemanla tersinin çarpımı birim elemanı vermelidir:

$$a \cdot b = b \cdot a = 1_R$$



$$a \cdot c = c \cdot a = 1_R$$





2. Şimdi $b$ elemanını alıp, eşitlikleri kullanarak adım adım açalım. Her elemanın $1_R$ ile çarpımı kendisidir:

$$b = b \cdot 1_R$$


3. Yukarıdaki ikinci denklemde $1_R$ yerine $(a \cdot c)$ yazabiliriz:

$$b = b \cdot (a \cdot c)$$


4. Halkalarda çarpma işleminin birleşme özelliği vardır. Parantezi kaydıralım:



$$b \cdot (a \cdot c) = (b \cdot a) \cdot c$$


5. İlk denkleme göre $(b \cdot a)$ çarpımının da $1_R$'ye eşit olduğunu biliyoruz. Yerine koyalım:

$$= 1_R \cdot c$$


6. Birim elemanla çarpım yine elemanın kendisini verir:

$$= c$$



Tüm adımları birleştirdiğimizde zincirleme olarak **$b = c$** sonucuna ulaşırız. Bu da bir elemanın çarpımsal tersi varsa, bunun **tek** olduğunu kanıtlar.

---

### Soru 6: $\mathbb{Z}_{10}$ içinde $R$ Althalkası İncelemesi

**Verilen Küme:** $R = \{\overline{0}, \overline{2}, \overline{4}, \overline{6}, \overline{8}\} \subset \mathbb{Z}_{10}$ 

#### (a) 

Toplama ve Çarpım Tabloları 

Buradaki işlemler mod 10'a göre yapılmaktadır. Yani sonuç 10'u aşarsa 10'a bölüp kalanını tabloya yazıyoruz.

**Toplama ($+$) Tablosu (mod 10):**

| $+$ | $\overline{0}$ | $\overline{2}$ | $\overline{4}$ | $\overline{6}$ | $\overline{8}$ |
| --- | --- | --- | --- | --- | --- |
| **$\overline{0}$** | $\overline{0}$ | $\overline{2}$ | $\overline{4}$ | $\overline{6}$ | $\overline{8}$ |
| **$\overline{2}$** | $\overline{2}$ | $\overline{4}$ | $\overline{6}$ | $\overline{8}$ | $\overline{0}$ |
| **$\overline{4}$** | $\overline{4}$ | $\overline{6}$ | $\overline{8}$ | $\overline{0}$ | $\overline{2}$ |
| **$\overline{6}$** | $\overline{6}$ | $\overline{8}$ | $\overline{0}$ | $\overline{2}$ | $\overline{4}$ |
| **$\overline{8}$** | $\overline{8}$ | $\overline{0}$ | $\overline{2}$ | $\overline{4}$ | $\overline{6}$ |

**Çarpma ($\cdot$) Tablosu (mod 10):**

| $\cdot$ | $\overline{0}$ | $\overline{2}$ | $\overline{4}$ | $\overline{6}$ | $\overline{8}$ |
| --- | --- | --- | --- | --- | --- |
| **$\overline{0}$** | $\overline{0}$ | $\overline{0}$ | $\overline{0}$ | $\overline{0}$ | $\overline{0}$ |
| **$\overline{2}$** | $\overline{0}$ | $\overline{4}$ | $\overline{8}$ | $\overline{2}$ | $\overline{6}$ |
| **$\overline{4}$** | $\overline{0}$ | $\overline{8}$ | $\overline{6}$ | $\overline{4}$ | $\overline{2}$ |
| **$\overline{6}$** | $\overline{0}$ | $\overline{2}$ | $\overline{4}$ | $\overline{6}$ | $\overline{8}$ |
| **$\overline{8}$** | $\overline{0}$ | $\overline{6}$ | $\overline{2}$ | $\overline{8}$ | $\overline{4}$ |

#### (b) 

$R$ Kümesi bir Althalka mıdır? 

**Evet, kesinlikle bir althalkadır.** Açıklaması: Bir kümenin althalka olabilmesi için farka ve çarpmaya göre kapalı olması yeterlidir (Teorem 1.2.6). Tablolarda ve temel mantıkta gördüğümüz üzere, $R$ kümesi $\mathbb{Z}_{10}$ içindeki tüm çift sayıları barındırmaktadır.

* İki çift sayının farkı daima çifttir.
* İki çift sayının çarpımı daima çifttir.
Sonuç olarak $R$ içinden alınan herhangi iki eleman, mod 10'da işlem gördüğünde asla küme dışına çıkmaz, dışarıda kalan tek sayılar üretilemez. İşlemler kapalıdır ve althalkadır.

#### (c) 

$R$'nin Hangi Elemanlarının Çarpımsal Tersi Vardır? 

Bu soru, klasik bir sınav tuzağı içeriyor. Soruyu iki farklı boyutta açıklayalım:

**Boyut 1: Eğer "$\mathbb{Z}_{10}$'un geneline göre ters" soruluyorsa:**
$\mathbb{Z}_{10}$'un ana birim elemanı $\overline{1}$'dir. $\mathbb{Z}_{n}$ formatındaki bir halkada yalnızca $n$ ile aralarında asal olan elemanların tersi vardır (Yani $U(\mathbb{Z}_{10}) = \{\overline{1},\overline{3},\overline{7},\overline{9}\}$ dir). $R$'deki tüm elemanlar çift olduğu için $10$ ile aralarında asal değillerdir, dolayısıyla $\mathbb{Z}_{10}$'da hiçbirinin tersi yoktur.

**Boyut 2: Ancak soru "$R$'nin kendi içindeki işlemlere göre tersleri" soruyorsa (ki tabloları yaptırdığı için kastettiği kesinlikle budur!):**
Bir alt halka, kapsayıcı halkasından farklı bir birim elemana sahip olabilir. Çarpım tablosuna dikkatlice bak: **$\overline{6}$ sütunu ve satırı, aynen ana elemanları dışarı çıkartıyor.** Yani $R$ althalkasının KENDİ birim elemanı **$\overline{6}$**'dır! ($x \cdot \overline{6} = x$).

Buna göre, tablodan sonucu $\overline{6}$ olan (yani birimi veren) çarpımları bulmamız gerekir:

* $\overline{2} \cdot \overline{8} = \overline{6}$ $\implies$ $\overline{2}$'nin tersi **$\overline{8}$**'dir. (Aynı şekilde $\overline{8}$'in tersi de **$\overline{2}$**'dir).
* $\overline{4} \cdot \overline{4} = \overline{6}$ $\implies$ $\overline{4}$'ün tersi kendisidir.
* $\overline{6} \cdot \overline{6} = \overline{6}$ $\implies$ $\overline{6}$'nın (birim eleman) tersi yine kendisidir.

**Sonuç:** $R$ althalkasının kendi içinde $\overline{0}$ hariç tüm elemanlarının ($\overline{2}, \overline{4}, \overline{6}, \overline{8}$) çarpımsal tersi **vardır**.

---

### Soru 7: $R^{op}$ Karşıt Halkasının İspatı

**Soru:** Eğer $R$ bir halka ise, aynı toplama işlemi fakat $r \ast s = s \cdot r$ çarpma işlemi ile tanımlanan $R^{op}$ (karşıt halka) yapısının bir halka olduğunu gösteriniz.
*(Not: Karışıklık olmaması için $R^{op}$'daki yeni çarpma işlemini "$\ast$" sembolü ile, $R$'deki orijinal çarpma işlemini "$\cdot$" ile göstereceğiz.)*

**İspat:**
Bir yapının halka olabilmesi için üç temel şartı sağlaması gerekir.

**1. Toplamaya Göre Değişmeli Grup Olma Şartı:**


$R^{op}$ halkasının toplama işlemi, halihazırda bir halka olan $R$ ile tamamen aynıdır. Bu nedenle $(R^{op}, +)$ yapısı doğrudan değişmeli bir gruptur. (Bu adımı uzun uzadıya ispatlamaya gerek yoktur, mirastır).

**2. Çarpmada Birleşme Özelliği:**
Her $a, b, c \in R^{op}$ için $(a \ast b) \ast c = a \ast (b \ast c)$ olduğunu göstermeliyiz.

* **Sol taraf:** $(a \ast b) \ast c = (b \cdot a) \ast c$ *(Yeni tanıma göre yer değiştirdik)*
$= c \cdot (b \cdot a)$ *(Tekrar yeni tanıma göre yer değiştirdik)*
* **Sağ taraf:** $a \ast (b \ast c) = a \ast (c \cdot b)$
$= (c \cdot b) \cdot a$
* Orijinal $R$ halkasında çarpma işleminin birleşme özelliği olduğundan, $c \cdot (b \cdot a) = (c \cdot b) \cdot a$ eşitliği geçerlidir. Dolayısıyla sol taraf sağ tarafa eşittir.



**3. Çarpmanın Toplama Üzerine Dağılma Özelliği:**

* **Soldan Dağılma:** $a \ast (b + c) = (b + c) \cdot a$ *(Yeni çarpma tanımı gereği)*.


$R$ halkasında *sağdan* dağılma özelliği olduğundan: $(b + c) \cdot a = b \cdot a + c \cdot a$.
Sonucu $R^{op}$ formatına geri çevirirsek: $b \cdot a + c \cdot a = a \ast b + a \ast c$. (Sağlandı).


* **Sağdan Dağılma:** $(a + b) \ast c = c \cdot (a + b)$.


$R$ halkasında *soldan* dağılma özelliği olduğundan: $c \cdot (a + b) = c \cdot a + c \cdot b$.
Sonucu $R^{op}$ formatına çevirirsek: $c \cdot a + c \cdot b = a \ast c + b \ast c$. (Sağlandı).



Tüm şartlar sağlandığı için $R^{op}$ kesinlikle bir halkadır.

---

### Soru 8: Merkezleyen Kümesinin $C(X)$ Althalka İspatı

**Soru:** $X$, $R$'nin boş olmayan bir altkümesi ise, $C(X) = \{c \in R \mid \text{her } x \in X \text{ için } cx=xc\}$ kümesinin $R$'nin bir althalkası olduğunu gösteriniz.

**İspat:**
Burada doğrudan hayat kurtarıcı olan **Teorem 1.2.6 (Althalka Testi)**'ni kullanacağız. Şartlar: Küme boş olmamalı ve her eleman çifti için hem farkları hem de çarpımları kümeye ait olmalı.

**1. Boş Küme Olmama Şartı:**


$R$ halkasının yutan elemanı olan sıfır ($0_R$), her $x \in X$ elemanı için $0_R \cdot x = x \cdot 0_R = 0_R$ eşitliğini sağlar. Dolayısıyla $0_R \in C(X)$'dir, küme boş küme değildir.

**2. Farka Göre Kapalılık ($c_1 - c_2 \in C(X)$):**
Herhangi iki $c_1, c_2 \in C(X)$ alalım. Küme tanımı gereği her $x \in X$ için $c_1 x = x c_1$ ve $c_2 x = x c_2$ olduğunu biliyoruz.
Acaba $(c_1 - c_2)x = x(c_1 - c_2)$ sağlanıyor mu?

* 
**Sol tarafı açalım:** $(c_1 - c_2)x = c_1 x - c_2 x$ 


* Verilen eşitlikleri yerine yazalım: $c_1 x - c_2 x = x c_1 - x c_2$
* Ortak $x$ parantezine alalım: $= x(c_1 - c_2)$.
Eşitlik sağlandığı için farka göre kapalıdır.



**3. Çarpmaya Göre Kapalılık ($c_1 \cdot c_2 \in C(X)$):**
Yine $c_1, c_2 \in C(X)$ alalım. Acaba $(c_1 \cdot c_2)x = x(c_1 \cdot c_2)$ sağlanıyor mu?

* 
Sol tarafı açalım (Halkada birleşme özelliği ): $(c_1 \cdot c_2)x = c_1 \cdot (c_2 \cdot x)$


* $c_2 \in C(X)$ olduğu için yer değiştirelim: $= c_1 \cdot (x \cdot c_2)$
* Parantezi kaydıralım: $= (c_1 \cdot x) \cdot c_2$
* $c_1 \in C(X)$ olduğu için yer değiştirelim: $= (x \cdot c_1) \cdot c_2$
* Parantezi tekrar kaydıralım: $= x \cdot (c_1 \cdot c_2)$.
Eşitlik sağlandığı için çarpmaya göre kapalıdır.

Teorem 1.2.6'nın tüm şartları sağlandığından, $C(X)$ kesinlikle bir althalkadır.

---

### Soru 9: $S$ ve $T$ Kümelerinin Althalka Testi

**Soru:** Aşağıdaki kümelerin althalka olup olmadığına karar veriniz. (Yine Teorem 1.2.6'yı  kullanıyoruz).

(a) $S = \{a\sqrt{2} : a \in \mathbb{Z}\}$ Althalka mıdır? 
**HAYIR, althalka değildir.**

* 
**Sebep:** Bir kümenin althalka olması için çarpmaya göre kapalı olması zorunludur.


* **Karşıt Örnek (Counter-example):** $S$ kümesinden $x = 1\sqrt{2}$ ve $y = 1\sqrt{2}$ elemanlarını alalım (çünkü $1 \in \mathbb{Z}$).
Bunları çarptığımızda: $x \cdot y = \sqrt{2} \cdot \sqrt{2} = 2$ sonucunu buluruz.
Peki $2$ elemanı $S$ kümesine ait midir? $2$'nin $S$'de olması için $2 = a\sqrt{2}$ şeklinde yazılabiliyor olması ve buradaki $a$'nın kesinlikle tam sayı ($a \in \mathbb{Z}$) olması gerekir. Buradan $a = \sqrt{2}$ çıkar, ancak $\sqrt{2}$ bir tam sayı değildir!
Çarpım sonucu kümenin dışına taştığı için (işlem kapalı olmadığı için) **$S$ bir althalka olamaz.**

(b) $T = \{a + b\sqrt{2} : a, b \in \mathbb{Z}\}$ Althalka mıdır? 
**EVET, kesinlikle althalkadır.**
Herhangi iki eleman alalım: $x = a_1 + b_1\sqrt{2}$ ve $y = a_2 + b_2\sqrt{2}$ (Burada $a_1, a_2, b_1, b_2 \in \mathbb{Z}$).

* **Farka Göre Kapalılık Testi:**
$x - y = (a_1 + b_1\sqrt{2}) - (a_2 + b_2\sqrt{2})$
$= (a_1 - a_2) + (b_1 - b_2)\sqrt{2}$
İki tam sayının farkı yine tam sayıdır. $(a_1 - a_2) \in \mathbb{Z}$ ve $(b_1 - b_2) \in \mathbb{Z}$ olduğu için yeni oluşan sayı yine $T$ kümesinin formatına birebir uyar. Farka göre kapalıdır.


* **Çarpmaya Göre Kapalılık Testi:**
$x \cdot y = (a_1 + b_1\sqrt{2}) \cdot (a_2 + b_2\sqrt{2})$
$= a_1 a_2 + a_1 b_2\sqrt{2} + b_1 a_2\sqrt{2} + b_1 b_2(\sqrt{2}\cdot\sqrt{2})$
$= a_1 a_2 + a_1 b_2\sqrt{2} + b_1 a_2\sqrt{2} + 2b_1 b_2$
Kök dışındakileri ve kök içindekileri gruplayalım:
$= (a_1 a_2 + 2b_1 b_2) + (a_1 b_2 + b_1 a_2)\sqrt{2}$
Tam sayıların çarpımları ve toplamları yine tam sayı edeceğinden;
$(a_1 a_2 + 2b_1 b_2) \in \mathbb{Z}$ ve $(a_1 b_2 + b_1 a_2) \in \mathbb{Z}$ olur.
Sonuç kusursuz bir şekilde $T$ formatındadır. Çarpmaya göre kapalıdır.



Şartları sağladığı için **$T$ bir althalkadır.**

***

**İlgili Konular:**
- [[Abstract Algebra Index]]
