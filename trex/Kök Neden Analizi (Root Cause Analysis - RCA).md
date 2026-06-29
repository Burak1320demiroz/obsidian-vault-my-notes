---
title: Kök Neden Analizi (RCA)
date: 2026-06-29
tags:
  - trex
  - analiz
  - kalite
  - rca
aliases:
  - Root Cause Analysis
  - Kök Neden Analizi
---

# Kök Neden Analizi (RCA)

**RCA (Root Cause Analysis)**, bir problemin yüzeydeki belirtileri yerine ==asıl kaynağını== bulmayı hedefleyen sistematik analiz yöntemidir. "Neden oldu?" sorusunu tekrar tekrar sorarak kök nedene ulaşır.

## Temel Yöntemler

### 5 Neden (5 Whys)

```
Problem: Makine durdu
 → Neden? Motor aşırı ısındı
  → Neden? Soğutma sıvısı yetersizdi
   → Neden? Pompa arızalıydı
    → Neden? Bakım yapılmamıştı
     → Neden? Bakım planı oluşturulmamıştı ← KÖK NEDEN
```

### Balık Kılçığı (Ishikawa) Diyagramı

Kategoriler: **6M** — Man, Machine, Method, Material, Measurement, Mother Nature (Çevre)

### Pareto Analizi

En sık tekrarlanan nedenleri **%80-20 kuralıyla** önceliklendirir. Az sayıda kök neden, sorunların büyük çoğunluğunu oluşturur.

> [!important] Belirtiye Değil, Nedene Odaklan
> Makine durduğunda motoru değiştirmek belirtiyi giderir. Bakım planı oluşturmak ise kök nedeni ortadan kaldırır. RCA, kalıcı çözüm üretir.

## Trex'te RCA

[[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]] sistemindeki duruş kodları ve arıza logları, [[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]] üzerinde analiz edilir. [[Açıklanabilir Yapay Zeka (Explainable AI - XAI)|XAI]] modelleri (SHAP değerleri), arızaya en çok katkıda bulunan faktörleri veri odaklı olarak ortaya koyar ve manuel RCA sürecini hızlandırır.

## İlişkili Kavramlar

- [[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]] — Duruş ve arıza verisi kaynağı
- [[Toplam Ekipman Etkinliği (Overall Equipment Effectiveness - OEE)|OEE]] — RCA sonucu iyileşen metrik
- [[Açıklanabilir Yapay Zeka (Explainable AI - XAI)|XAI]] — Veri odaklı kök neden açıklaması
- [[Temel Performans Göstergesi (Key Performance Indicator - KPI)|KPI]] — RCA'nın başarısını ölçen göstergeler
