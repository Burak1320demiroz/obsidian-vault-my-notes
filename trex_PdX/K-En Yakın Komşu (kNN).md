---
title: K-En Yakın Komşu (kNN)
date: 2026-06-30
tags:
  - trex
  - makine-öğrenmesi
  - sınıflandırma
  - regresyon
aliases:
  - K-Nearest Neighbors
  - kNN
  - KNN
---

# K-En Yakın Komşu (kNN)

**kNN (K-Nearest Neighbors)**, bir veri noktasını sınıflandırmak veya değerini tahmin etmek için ==en yakın K komşusuna== bakarak karar veren, basit ama güçlü bir makine öğrenmesi algoritmasıdır. Eğitim aşaması yoktur; tüm hesaplama tahmin anında yapılır (*lazy learning*).

## Nasıl Çalışır?

1. **K değeri belirlenir** — kaç komşuya bakılacağı seçilir (ör. K=5)
2. **Mesafe hesaplanır** — yeni veri noktası ile tüm eğitim verileri arasındaki uzaklık ölçülür
3. **En yakın K komşu seçilir** — mesafeye göre sıralanır
4. **Karar verilir:**
   - *Sınıflandırma:* K komşunun çoğunluk oyuyla sınıf atanır
   - *Regresyon:* K komşunun ortalaması alınır

## Mesafe Metrikleri

| Metrik                | Formül                                                            | Kullanım Alanı                  |
| --------------------- | ----------------------------------------------------------------- | ------------------------------- |
| **Öklid (Euclidean)** | $d = \sqrt{\sum_{i=1}^{n}(x_i - y_i)^2}$                        | Sürekli ve normalleştirilmiş veri |
| **Manhattan**         | $d = \sum_{i=1}^{n} \lvert x_i - y_i \rvert$                    | Yüksek boyutlu veri             |
| **Minkowski**         | $d = \left(\sum_{i=1}^{n} \lvert x_i - y_i \rvert^p \right)^{1/p}$ | Genelleştirilmiş metrik        |

## K Değerinin Seçimi

- **K çok küçükse** (ör. K=1) → Gürültüye duyarlı, ==overfitting== riski
- **K çok büyükse** (ör. K=50) → Aşırı genelleme, ==underfitting== riski
- **En iyi K:** Cross-validation ile denenerek bulunur; genellikle tek sayı tercih edilir (eşitlik bozma)

```
K=1 → Gürültüye hassas, kararsız sınır
K=5 → Dengeli, yaygın tercih
K=N → Her zaman çoğunluk sınıfını verir (anlamsız)
```

## Avantajlar ve Dezavantajlar

| ✅ Avantajlar                           | ❌ Dezavantajlar                             |
| --------------------------------------- | ------------------------------------------- |
| Basit ve sezgisel                       | Büyük veri setlerinde yavaş (tüm veriyi tarar) |
| Eğitim süresi yok                       | Yüksek boyutluluk sorunu (*curse of dimensionality*) |
| Non-linear karar sınırları çizebilir    | Özellik ölçeklendirme (normalizasyon) zorunlu |
| Hem sınıflandırma hem regresyon         | K seçimi sonucu doğrudan etkiler            |

> [!tip] Özellik Ölçeklendirme Şart
> kNN mesafe tabanlı çalıştığı için, farklı ölçeklerdeki özellikler sonucu bozar. Örneğin "sıcaklık (0-200°C)" ile "titreşim (0-1 mm/s)" karşılaştırılırken ==mutlaka normalizasyon== (Min-Max veya Z-score) uygulanmalıdır.

## Trex'te kNN Kullanımı

Kestirimci bakım sürecinde kNN, sensör verileri üzerinde hızlı anomali sınıflandırması için kullanılabilir. [[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]]'dan çekilen titreşim, sıcaklık ve basınç verileri normalize edildikten sonra, yeni bir okuma en yakın K tarihsel örneğe göre "normal" veya "anormal" olarak etiketlenir. [[Özellik Mühendisliği (Feature Engineering)|Özellik mühendisliği]] ile boyut azaltma yapılması kNN performansını önemli ölçüde artırır.

## İlişkili Kavramlar

- [[Açıklanabilir Yapay Zeka (Explainable AI - XAI)|XAI]] — kNN kararları doğası gereği açıklanabilir
- [[Özellik Mühendisliği (Feature Engineering)|Özellik Mühendisliği]] — Boyut azaltma ve normalizasyon
- [[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]] — Sensör verisi kaynağı
- [[Kök Neden Analizi (Root Cause Analysis - RCA)|RCA]] — Anomali sınıflandırması sonrası kök neden analizi
- [[SHAP (SHapley Additive exPlanations)|SHAP]] — Model açıklanabilirlik karşılaştırması
