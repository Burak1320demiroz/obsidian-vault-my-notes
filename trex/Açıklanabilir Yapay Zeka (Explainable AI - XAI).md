---
title: Açıklanabilir Yapay Zeka (XAI)
date: 2026-06-29
tags:
  - trex
  - ai
  - açıklanabilirlik
  - makine-öğrenmesi
aliases:
  - Explainable AI
  - Açıklanabilir Yapay Zeka
---

# Açıklanabilir Yapay Zeka (XAI)

**XAI (Explainable AI)**, yapay zeka modellerinin kararlarını ==insanların anlayabileceği== şekilde açıklayan yöntem ve tekniklerin bütünüdür. "Kara kutu" modelleri şeffaflaştırır.

## Neden XAI Gerekli?

- **Güven:** Operatör, modelin önerisine neden güvenmesi gerektiğini bilir
- **Düzenleme:** AB AI Act gibi yasalar açıklanabilirlik zorunluluğu getirir
- **Hata Ayıklama:** Model yanlış öğrendiyse, nedenini görmek mümkün olur
- **Aksiyon:** Hangi parametreyi değiştirerek sonucu iyileştirebileceğini gösterir

## Temel XAI Yöntemleri

| Yöntem                 | Tip            | Açıklama                                                 |
| ---------------------- | -------------- | -------------------------------------------------------- |
| **SHAP**               | Model-agnostik | Her özelliğin tahmine katkısını oyun teorisiyle hesaplar |
| **LIME**               | Model-agnostik | Lokal olarak basit bir model ile tahmini açıklar         |
| **Feature Importance** | Model-spesifik | Ağaç tabanlı modellerde özellik önem sıralaması          |
| **Attention Maps**     | Model-spesifik | Sinir ağlarında hangi girdilere odaklanıldığını gösterir |
|                        |                |                                                          |

## SHAP Örneği

```
Arıza Tahmini = %87

Katkıda Bulunan Faktörler:
  Titreşim seviyesi    ████████████  +0.35
  Motor sıcaklığı      ████████     +0.22
  Çalışma saati         ██████      +0.18
  Bakım gecikmesi       ████        +0.12
```

> [!important] Kara Kutu vs Şeffaf Model
> Yüksek doğruluk (accuracy) tek başına yeterli değil. Endüstriyel ortamda operatör "Bu makine arızalanacak" demek yerine "Titreşim ve sıcaklık artışı nedeniyle arıza riski yüksek" demelidir. XAI bunu mümkün kılar.

## Trex'te XAI

[[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]]'dan çekilen sensör verileriyle eğitilen XGBoost modeline SHAP analizi uygulanır. [[Nightwatch (Anomali Tespiti ve İzleme Sistemi)|Nightwatch]] anomali tespit ettiğinde, XAI modülü kök nedeni açıklar. Bu, [[Kök Neden Analizi (Root Cause Analysis - RCA)|RCA]] sürecini hızlandırır ve [[Senaryo Analizi (What-if Analysis)|What-if Analizi]] senaryolarını anlamlandırır.

## İlişkili Kavramlar

- [[Nightwatch (Anomali Tespiti ve İzleme Sistemi)|Nightwatch]] — Anomali tespiti ve izleme
- [[Kök Neden Analizi (Root Cause Analysis - RCA)|RCA]] — XAI destekli kök neden analizi
- [[Senaryo Analizi (What-if Analysis)|What-if Analizi]] — Açıklanabilir senaryo simülasyonu
- [[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]] — Model eğitim verisi kaynağı
- [[Temel Performans Göstergesi (Key Performance Indicator - KPI)|KPI]] — XAI çıktılarıyla desteklenen metrikler
