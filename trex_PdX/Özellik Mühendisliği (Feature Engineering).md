---
title: Özellik Mühendisliği (Feature Engineering)
date: 2026-06-29
tags:
  - trex
  - veri-bilimi
  - makine-öğrenmesi
  - feature-engineering
aliases:
  - Feature Engineering
  - Özellik Mühendisliği
---

# Özellik Mühendisliği (Feature Engineering)

**Özellik Mühendisliği (Feature Engineering)**, ham veriyi alıp makine öğrenmesi modellerinin daha iyi anlayabileceği ve öğrenebileceği, ==anlamlı girdilere (özelliklere)== dönüştürme sürecidir. Çoğu zaman iyi bir özellik mühendisliği, model seçimi veya hiperparametre ayarından çok daha büyük bir performans artışı sağlar.

## Neden Önemlidir?

Ham veriler genellikle gürültülü, eksik veya modelin doğrudan matematiksel olarak değerlendiremeyeceği (örneğin metin veya zaman damgası) formattadır. 
- Algoritmalar, "Vardiya başlangıcı" gibi bir kavramı kendiliğinden anlayamaz.
- Doğru özellikler, veri içindeki **gizli örüntüleri** belirgin hale getirir.

## Temel Yöntemler

| Yöntem | Açıklama | Örnek |
|---|---|---|
| **Eksik Veri Doldurma (Imputation)** | Boş değerleri mantıklı bir şekilde tamamlama. | Sensör verisi gelmediğinde bir önceki değeri kullanmak. |
| **Özellik Çıkarımı (Extraction)** | Mevcut değişkenlerden yeni ve anlamlı bilgi üretmek. | Tarih değerinden "Haftanın Günü" bilgisini çekmek. |
| **Dönüştürme (Transformation)** | Verinin dağılımını düzeltmek veya ölçeklendirmek. | Logaritmik dönüşüm veya 0-1 aralığında Min-Max ölçekleme. |
| **Kodlama (Encoding)** | Kategorik verileri sayısal formata çevirmek. | "Makine_A" → `1`, "Makine_B" → `0` (One-Hot Encoding). |
| **Agresgasyon (Aggregation)** | Zaman pencereleri (window) üzerinden özetleme yapmak. | Son 1 saatteki *ortalama* sıcaklık veya *maksimum* titreşim. |

## Trex'te Özellik Mühendisliği

Üretim sahasından [[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]] aracılığıyla saniyede binlerce satır ham sensör verisi (IoT) gelir ve [[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]]'a yazılır. Ancak modellerin "son 5 saniyedeki anlık titreşime" değil, **"son 30 dakikadaki titreşim trendine"** ihtiyacı vardır.

Bu aşamada şu tür özellikler (features) üretilir:
- `rolling_mean_vibration_30m` (Son 30 dakikanın titreşim ortalaması)
- `temp_change_rate_5m` (Son 5 dakikadaki sıcaklık değişim hızı)
- `time_since_last_maintenance` (Son bakımdan bu yana geçen çalışma saati)
- `is_night_shift` (Vardiya türü, 0 veya 1)

> [!tip] Yüksek Başarı
> Bu tarz mühendislik adımlarıyla üretilen kaliteli özellikler, [[Nightwatch (Anomali Tespiti ve İzleme Sistemi)|Nightwatch]] tarafından arızaları çok daha erken tespit etmek için kullanılır. Ayrıca [[Açıklanabilir Yapay Zeka (Explainable AI - XAI)|XAI]] ve [[SHAP (SHapley Additive exPlanations)|SHAP]] analizlerinde operatöre "Ham titreşim değeri 14.5" demek yerine, "Titreşim değişim hızı çok yüksek" gibi anlamlı uyarılar verilmesini sağlar.

## İlişkili Kavramlar

- [[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]] — Ham ve dönüştürülmüş verilerin saklandığı yer
- [[Nightwatch (Anomali Tespiti ve İzleme Sistemi)|Nightwatch]] — Özelliklerin beslendiği izleme sistemi
- [[Açıklanabilir Yapay Zeka (Explainable AI - XAI)|XAI]] & [[SHAP (SHapley Additive exPlanations)|SHAP]] — Hangi özelliğin modele ne kadar etki ettiğini gösteren sistem
