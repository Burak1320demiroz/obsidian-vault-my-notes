---
title: SHAP Analizi (SHapley Additive exPlanations)
date: 2026-06-29
tags:
  - trex
  - ai
  - açıklanabilirlik
  - shap
  - oyun-teorisi
  - makine-öğrenmesi
aliases:
  - SHAP
  - SHapley Additive exPlanations
  - Shapley Değerleri
---

# SHAP Analizi (SHapley Additive exPlanations)

**SHAP (SHapley Additive exPlanations)**, karmaşık makine öğrenmesi modellerinin (kara kutu) yaptığı tahminleri ==şeffaflaştırmak ve açıklamak== için oyun teorisine dayanan bir yaklaşımdır. Her bir özelliğin (değişkenin) nihai tahmine olan spesifik katkısını sayısal olarak gösterir.

## Matematiksel Temel: Shapley Değerleri

SHAP, **Lloyd Shapley**'in 1953'te Nobel ödülü kazandığı kooperatif oyun teorisi kavramına dayanır.

### Analoji

Bir grup arkadaş birlikte bir iş yapıyor. Herkesin katkısı farklı. Shapley Değeri şu soruyu yanıtlar:
> *"Her bir kişinin, nihai sonuca ==adil== katkısı nedir?"*

ML bağlamında:
- **Oyuncular** = Girdi özellikleri (sıcaklık, titreşim, basınç…)
- **Oyunun sonucu** = Modelin tahmini (arıza olasılığı: %87)
- **Shapley Değeri** = Her özelliğin bu tahmine olan marjinal katkısı

### Formül

Bir $i$ özelliğinin Shapley değeri:

$$
\phi_i = \sum_{S \subseteq N \setminus \{i\}} \frac{|S|! \; (|N| - |S| - 1)!}{|N|!} \left[ f(S \cup \{i\}) - f(S) \right]
$$

Burada:
- $N$ — Tüm özellikler kümesi
- $S$ — $i$ olmadan oluşturulan bir alt küme (koalisyon)
- $f(S)$ — Sadece $S$ kümesindeki özelliklerle modelin tahmini
- $f(S \cup \{i\}) - f(S)$ — $i$'nin bu koalisyona katılmasıyla oluşan marjinal katkı

> [!important] Hesaplama Karmaşıklığı
> $n$ özellik için tüm $2^n$ alt küme kombinasyonu hesaplanmalıdır. 20 özellikte bu 1.048.576 kombinasyon demektir. Bu yüzden SHAP, pratikteki farklı **yaklaşım algoritmaları** kullanır.

### Shapley'in 4 Aksiyomu

SHAP'i diğer açıklama yöntemlerinden üstün kılan, matematiksel olarak kanıtlanmış bu özelliklerdir:

| Aksiyom | Açıklama |
|---|---|
| **Verimlilik (Efficiency)** | Tüm özelliklerin SHAP değerleri toplamı = Modelin tahmini − Ortalama tahmin |
| **Simetri (Symmetry)** | Aynı katkıyı yapan iki özellik, aynı SHAP değerini alır |
| **Kukla (Dummy)** | Hiçbir koalisyonda katkı sağlamayan özelliğin SHAP değeri = 0 |
| **Toplamsallık (Additivity)** | İki modelin birleşimi için SHAP değerleri, ayrı ayrı SHAP değerlerinin toplamıdır |

## SHAP Değerinin Yorumlanması

```
Baz Değer (Ortalama tahmin): %35 arıza olasılığı
Modelin bu örnek için tahmini: %87 arıza olasılığı

Katkıda Bulunan Faktörler:
  Titreşim seviyesi    ████████████████  +0.25  → %35 + 0.25 yönünde itme
  Motor sıcaklığı      ████████████     +0.18  → Riski artırıyor
  Çalışma saati         ████████        +0.12  → Riski artırıyor
  Bakım gecikmesi       ██████          +0.08  → Riski artırıyor
  Nem oranı             ██              -0.04  → Riski azaltıyor
  Ortam sıcaklığı       █              -0.02  → Riski azaltıyor
  Diğer                 █              -0.05  → Toplam düzeltme
                                        ─────
                                  Toplam: +0.52  → %35 + %52 = %87 ✓
```

- **Pozitif SHAP Değeri:** Tahmini baz değerden ==yukarı== iter (risk artışı)
- **Negatif SHAP Değeri:** Tahmini baz değerden ==aşağı== çeker (risk azalması)
- Tüm SHAP değerlerinin toplamı = Tahmin − Baz Değer (Verimlilik aksiyomu)

## SHAP Yaklaşım Algoritmaları

Tam Shapley hesaplaması $O(2^n)$ olduğundan, pratik kullanım için farklı yaklaşımlar geliştirilmiştir:

### 1. TreeSHAP (Ağaç Modelleri İçin)

[[machine_learning/xgboost|XGBoost]], LightGBM, Random Forest gibi ağaç tabanlı modeller için ==özel olarak optimize== edilmiş algoritma.

- **Karmaşıklık:** $O(TLD^2)$ — $T$ ağaç, $L$ yaprak, $D$ derinlik
- **Avantaj:** Tam (exact) Shapley değerlerini verir, yaklaşık değil
- **Hız:** Binlerce örnek için saniyeler içinde hesaplanır

```python
import shap

# XGBoost modeli için TreeSHAP
explainer = shap.TreeExplainer(xgb_model)
shap_values = explainer.shap_values(X_test)
```

### 2. KernelSHAP (Model-Agnostik)

Herhangi bir model (sinir ağları, SVM, vb.) için çalışan genel yaklaşım. LIME'ın ağırlıklı lineer regresyon fikrini Shapley değerleriyle birleştirir.

- **Karmaşıklık:** $O(2^M \cdot n_{samples})$ — yaklaşık hesaplama
- **Avantaj:** Her türlü modelde çalışır
- **Dezavantaj:** TreeSHAP'e göre çok daha yavaş

```python
explainer = shap.KernelExplainer(model.predict, X_train[:100])
shap_values = explainer.shap_values(X_test[:10])
```

### 3. DeepSHAP (Derin Öğrenme İçin)

DeepLIFT algoritmasını Shapley değerleriyle birleştirir. TensorFlow/PyTorch modelleri için uygundur.

### 4. LinearSHAP

Lineer modeller için analitik çözüm. Korelasyonlu özelliklerle de doğru sonuç verir.

## SHAP Görselleştirme Türleri

### Waterfall Plot (Şelale Grafik)

Tek bir tahmin için her özelliğin katkısını sıralı olarak gösterir:

```python
shap.plots.waterfall(shap_values[0])
```

```
Baz Değer ─────┐
               │ +0.25 Titreşim
               │ +0.18 Sıcaklık
               │ +0.12 Çalışma saati
               │ -0.04 Nem
               │ ...
      Tahmin ←─┘
```

### Beeswarm Plot (Arı Sürüsü)

==Küresel açıklanabilirlik== için en güçlü görselleştirme. Tüm veri seti üzerinde her özelliğin SHAP dağılımını gösterir:

```python
shap.plots.beeswarm(shap_values)
```

- X ekseni: SHAP değeri (etkinin yönü ve büyüklüğü)
- Y ekseni: Özellikler (önem sırasına göre)
- Renk: Özellik değeri (kırmızı = yüksek, mavi = düşük)

### Force Plot (Kuvvet Grafik)

Tek bir tahminin bileşenlerini yatay olarak görselleştirir. Kırmızı çubuklar tahmini artıran, mavi çubuklar azaltan özellikleri gösterir.

```python
shap.plots.force(shap_values[0])
```

### Summary Plot (Özet)

Global özellik önem sıralamasını bar chart olarak gösterir:

```python
shap.plots.bar(shap_values)
```

### Dependence Plot (Bağımlılık)

Bir özelliğin farklı değerlerinde SHAP etkisinin nasıl değiştiğini gösterir. Etkileşim (interaction) etkilerini de ortaya koyar:

```python
shap.plots.scatter(shap_values[:, "Titreşim"])
```

## Yerel vs Küresel Açıklanabilirlik

| Düzey | Soru | SHAP Yaklaşımı |
|---|---|---|
| **Yerel (Local)** | "Bu **spesifik** arıza tahmini neden %87?" | Waterfall, Force plot — tek bir örneği açıkla |
| **Küresel (Global)** | "Model **genel olarak** en çok neye bakıyor?" | Beeswarm, Bar plot — tüm tahminlerin ortalamasını al |

> [!tip] Doğru Soruya Doğru Grafik
> - Operatör "Bu alarm neden geldi?" diye sorarsa → **Waterfall** (yerel)
> - Mühendis "Model sağlıklı mı, neyi öğrenmiş?" diye sorarsa → **Beeswarm** (küresel)

## SHAP vs Diğer XAI Yöntemleri

| Özellik | **SHAP** | **LIME** | **Permutation Importance** |
|---|---|---|---|
| Matematiksel temel | Shapley aksiyomları ✓ | Sezgisel yaklaşım | İstatistiksel |
| Tutarlılık | Garantili (aksiyomlarla) | Garanti yok | Garanti yok |
| Yerel açıklama | ✓ (per-sample) | ✓ (per-sample) | ✗ (sadece global) |
| Küresel açıklama | ✓ (ortalama SHAP) | ✗ | ✓ |
| Hesaplama maliyeti | Orta (TreeSHAP hızlı) | Düşük | Yüksek |
| Özellik etkileşimi | ✓ (interaction values) | ✗ | ✗ |

## Python ile Tam Örnek

```python
import xgboost as xgb
import shap
import pandas as pd

# 1. Model eğitimi
model = xgb.XGBClassifier(n_estimators=200, max_depth=5)
model.fit(X_train, y_train)

# 2. SHAP Explainer oluştur
explainer = shap.TreeExplainer(model)
shap_values = explainer(X_test)

# 3. Yerel açıklama — tek bir tahmini açıkla
shap.plots.waterfall(shap_values[0])

# 4. Küresel açıklama — genel model davranışı
shap.plots.beeswarm(shap_values)

# 5. Özellik etkileşim analizi
shap.plots.scatter(shap_values[:, "Motor_Sicakligi"],
                   color=shap_values[:, "Titresim"])

# 6. SHAP değerlerini DataFrame olarak al
shap_df = pd.DataFrame(
    shap_values.values,
    columns=X_test.columns
)
top_features = shap_df.abs().mean().sort_values(ascending=False)
print("En etkili 5 özellik:")
print(top_features.head())
```

## Trex ve XAI İçindeki Yeri

Trex sisteminde, makine arızalarını veya anormalliklerini tahmin eden [[machine_learning/xgboost|XGBoost]] modelinin sonuçları operatörlere SHAP analizleriyle sunulur.

Örneğin, [[Nightwatch (Anomali Tespiti ve İzleme Sistemi)|Nightwatch]] bir anomali alarmı verdiğinde arka planda çalışan [[Açıklanabilir Yapay Zeka (Explainable AI - XAI)|XAI]] modülü SHAP grafiği oluşturur:
- *Titresim_Sensor_A* (+0.25 etki: Arıza ihtimalini artırmış)
- *Motor_Sicakligi* (+0.18 etki: Arıza ihtimalini artırmış)
- *Bakim_Gecikmesi* (-0.05 etki: Normal seviyede)

Bu sayede operatör, sorunun nerede başladığını doğrudan görerek [[Kök Neden Analizi (Root Cause Analysis - RCA)|RCA]] sürecine odaklanabilir.

## İlişkili Kavramlar

- [[Açıklanabilir Yapay Zeka (Explainable AI - XAI)|XAI]] — Üst şemsiye kavram
- [[machine_learning/xgboost|XGBoost]] — TreeSHAP ile en verimli çalışan model
- [[Nightwatch (Anomali Tespiti ve İzleme Sistemi)|Nightwatch]] — Anomali alarmını üreten sistem
- [[Kök Neden Analizi (Root Cause Analysis - RCA)|RCA]] — SHAP çıktısıyla hızlanan analiz süreci
- [[Özellik Mühendisliği (Feature Engineering)|Feature Engineering]] — SHAP'in açıkladığı özelliklerin kaynağı
