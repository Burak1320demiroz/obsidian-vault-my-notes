---
title: XGBoost (eXtreme Gradient Boosting)
date: 2026-06-29
tags:
  - makine-öğrenmesi
  - ensemble
  - gradient-boosting
  - xgboost
  - sınıflandırma
  - regresyon
aliases:
  - XGBoost
  - eXtreme Gradient Boosting
---

# XGBoost (eXtreme Gradient Boosting)

**XGBoost**, Tianqi Chen tarafından 2014'te geliştirilen, ==gradient boosting== algoritmasının yüksek performanslı, ölçeklenebilir ve düzenlenmiş (regularized) bir uygulamasıdır. Tablo (tabular) verilerde en güçlü algoritmalardan biri olarak kabul edilir ve Kaggle yarışmalarındaki baskın başarısıyla ünlenmiştir.

## Temel Kavramlar

### Ensemble Öğrenme

Tek bir güçlü model yerine, birçok **zayıf öğrenicinin** (weak learner) bir araya gelerek güçlü bir tahmin üretmesi ilkesine dayanır. XGBoost'ta zayıf öğrenici genellikle **sığ karar ağaçlarıdır** (decision stumps / shallow trees).

### Boosting vs Bagging

| Özellik | **Boosting** (XGBoost) | **Bagging** (Random Forest) |
|---|---|---|
| Eğitim | Sıralı (sequential) — her ağaç bir öncekinin hatasını düzeltir | Paralel — bağımsız ağaçlar |
| Odak | Yanlış tahmin edilen örneklere ağırlık verir | Rastgele alt kümeler üzerinde çalışır |
| Risk | Overfitting'e daha yatkın (regularization gerektirir) | Daha dayanıklı |
| Performans | Genellikle daha yüksek doğruluk | Daha kararlı (stable) |

### Gradient Boosting Mekanizması

Her yeni ağaç, bir önceki modelin **artık hatalarını (residuals)** öğrenir:

```
Tahmin_1 = Ağaç_1(X)                          → ilk kaba tahmin
Hata_1   = y - Tahmin_1                        → artık hata

Tahmin_2 = Ağaç_1(X) + η · Ağaç_2(Hata_1)    → hatayı düzelt
Hata_2   = y - Tahmin_2                        → kalan hata

...

Tahmin_N = Σ η · Ağaç_i(Hata_{i-1})           → nihai tahmin
```

> [!note] Öğrenme Oranı (η)
> `η` (eta / learning rate), her ağacın katkısını küçülterek modelin daha yavaş ama daha sağlıklı öğrenmesini sağlar. Düşük `η` + yüksek ağaç sayısı genellikle en iyi sonucu verir.

## XGBoost'u Özel Kılan Nedir?

### 1. Regularization (Düzenleme)

Klasik gradient boosting'den farklı olarak XGBoost, kayıp fonksiyonuna **L1 (Lasso)** ve **L2 (Ridge)** düzenleme terimleri ekler:

$$
\mathcal{L} = \sum_{i=1}^{n} l(y_i, \hat{y}_i) + \sum_{k=1}^{K} \Omega(f_k)
$$

$$
\Omega(f) = \gamma T + \frac{1}{2} \lambda \sum_{j=1}^{T} w_j^2
$$

Burada:
- $l$ — Kayıp fonksiyonu (loss function)
- $T$ — Yaprak (leaf) sayısı, $\gamma$ ile cezalandırılır (budama)
- $w_j$ — Yaprak ağırlıkları, $\lambda$ ile cezalandırılır (L2)

Bu sayede model karmaşıklığı kontrol altında tutulur ve **overfitting** riski azalır.

### 2. İkinci Derece Taylor Yaklaşımı

XGBoost, kayıp fonksiyonunu optimize ederken birinci türevin (gradient) yanı sıra ==ikinci türevi (Hessian)== de kullanır. Bu, daha hassas ve hızlı yakınsama sağlar:

$$
\mathcal{L}^{(t)} \approx \sum_{i=1}^{n} \left[ g_i f_t(x_i) + \frac{1}{2} h_i f_t^2(x_i) \right] + \Omega(f_t)
$$

- $g_i = \frac{\partial l(y_i, \hat{y}^{(t-1)})}{\partial \hat{y}^{(t-1)}}$ → Gradient (1. türev)
- $h_i = \frac{\partial^2 l(y_i, \hat{y}^{(t-1)})}{\partial (\hat{y}^{(t-1)})^2}$ → Hessian (2. türev)

### 3. Ağaç Budama (Pruning)

- **Ön budama (Pre-pruning):** `max_depth` parametresi ile ağaç derinliği sınırlanır
- **Son budama (Post-pruning):** `γ` (gamma) parametresi ile kazanç (gain) eşiğinin altında kalan dallar kesilir

### 4. Eksik Veri Yönetimi

XGBoost, eksik değerleri otomatik olarak yönetir. Eğitim sırasında her düğümde eksik verileri sola veya sağa yönlendirmenin hangisinin daha iyi sonuç verdiğini öğrenir — ek bir imputation adımına gerek kalmaz.

### 5. Performans Optimizasyonları

| Özellik | Açıklama |
|---|---|
| **Column Block** | Veriler sütun bazında sıralanıp bellekte saklanır, split arama hızlanır |
| **Cache-Aware Access** | CPU önbelleğiyle uyumlu bellek erişim deseni |
| **Out-of-Core** | RAM'e sığmayan veriler için disk tabanlı hesaplama |
| **Paralel Hesaplama** | Ağaç içi split araması paralel yapılır |
| **GPU Desteği** | `tree_method='gpu_hist'` ile GPU üzerinde eğitim |

## Hiperparametreler

### Kritik Parametreler

| Parametre | Varsayılan | Açıklama |
|---|---|---|
| `n_estimators` | 100 | Toplam ağaç sayısı |
| `learning_rate` (η) | 0.3 | Her ağacın katkı oranı |
| `max_depth` | 6 | Ağaç derinliği |
| `min_child_weight` | 1 | Yaprak düğümde minimum Hessian toplamı |
| `subsample` | 1.0 | Her ağaçta kullanılacak örnek oranı |
| `colsample_bytree` | 1.0 | Her ağaçta kullanılacak özellik oranı |
| `gamma` (γ) | 0 | Minimum split kazancı (budama eşiği) |
| `lambda` (λ) | 1 | L2 düzenleme katsayısı |
| `alpha` (α) | 0 | L1 düzenleme katsayısı |

> [!tip] Hiperparametre Ayarlama Stratejisi
> 1. `learning_rate`'i düşür (0.01–0.1), `n_estimators`'ı yükselt
> 2. `max_depth` (3–8) ve `min_child_weight` ile ağaç karmaşıklığını ayarla
> 3. `subsample` ve `colsample_bytree` (0.6–0.9) ile stokastiklik ekle
> 4. `gamma`, `lambda`, `alpha` ile düzenlemeyi ince ayarla
> 5. `early_stopping_rounds` ile gereksiz ağaç eklenmesini önle

## Kullanım Alanları

- **Sınıflandırma:** Arıza tahmini, müşteri kaybı (churn), dolandırıcılık tespiti
- **Regresyon:** Fiyat tahmini, süre tahmini, talep öngörüsü
- **Sıralama (Ranking):** Arama motoru sonuç sıralama (LambdaMART)

## Python Örneği

```python
import xgboost as xgb
from sklearn.model_selection import train_test_split
from sklearn.metrics import classification_report

# Veri hazırlığı
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

# Model eğitimi
model = xgb.XGBClassifier(
    n_estimators=500,
    learning_rate=0.05,
    max_depth=5,
    subsample=0.8,
    colsample_bytree=0.8,
    eval_metric='logloss',
    early_stopping_rounds=50
)

model.fit(
    X_train, y_train,
    eval_set=[(X_test, y_test)],
    verbose=50
)

# Tahmin ve değerlendirme
y_pred = model.predict(X_test)
print(classification_report(y_test, y_pred))
```

## XGBoost vs LightGBM vs CatBoost

| Özellik | XGBoost | LightGBM | CatBoost |
|---|---|---|---|
| Ağaç büyüme | Level-wise | ==Leaf-wise== (daha hızlı) | Symmetric tree |
| Kategorik veri | Manuel encoding | Optimal split | ==Native destek== |
| Hız | Hızlı | En hızlı | Orta |
| Overfitting direnci | İyi (regularization) | Orta | En iyi (ordered boosting) |
| GPU desteği | Var | Var | Var |

## İlişkili Kavramlar

- [[simple_linear_regression|Linear Regression]] — Temel regresyon modeli
