---
title: Nightwatch
date: 2026-06-29
tags:
  - trex
  - izleme
  - monitoring
  - anomali
aliases:
  - NightWatch
  - Night Watch
---

# Nightwatch

**Nightwatch**, üretim ortamlarında ==anomali tespiti ve sürekli izleme== için kullanılan bir monitoring/watchdog sistemidir. Normal çalışma kalıplarından sapmaları otomatik olarak algılar ve uyarı üretir.

## Temel İşlevler

- **Anomali Tespiti:** Sensör verilerindeki anormal kalıpları gerçek zamanlı tespit eder
- **Eşik İzleme:** Statik ve dinamik eşik değerlerini kontrol eder
- **Alarm Yönetimi:** Kritik sapmalarda anlık bildirim
- **Trend Analizi:** Uzun vadeli eğilimleri izleyerek erken uyarı verir
- **Otonom Karar:** Belirli koşullarda otomatik aksiyon tetikler

## Nasıl Çalışır?

```
Sensör Verisi → Veri Toplama → Anomali Modeli → Karar
     ↑              ↓              ↓            ↓
  [[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]]    [[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]]   ML/İstatistik   Alarm / Aksiyon
```

## İzlenen Veri Tipleri

| Veri | Kaynak | Anomali Örneği |
|---|---|---|
| Sıcaklık | Termal sensör | Ani yükseliş |
| Titreşim | Vibrasyon sensör | Frekans kayması |
| Basınç | Basınç sensör | Düşüş trendi |
| Enerji | Güç ölçer | Aşırı tüketim |
| Üretim hızı | [[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]] sayaç | Beklenmeyen yavaşlama |

> [!warning] Gece Vardiyası Riski
> İstatistiksel olarak arızaların önemli bir kısmı gece vardiyasında, daha az personel varken gerçekleşir. Nightwatch, 7/24 otomatik izleme sağlayarak bu riski minimize eder.

## [[Açıklanabilir Yapay Zeka (Explainable AI - XAI)|XAI]] ile Entegrasyon

Nightwatch bir anomali tespit ettiğinde, [[Açıklanabilir Yapay Zeka (Explainable AI - XAI)|XAI]] modülleri bu anomalinin **neden** oluştuğunu açıklar. Bu sayede operatör sadece "bir şey yanlış" değil, "şu parametreler yüzünden yanlış" bilgisini alır.

## İlişkili Kavramlar

- [[Açıklanabilir Yapay Zeka (Explainable AI - XAI)|XAI]] — Anomali açıklanabilirliği
- [[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]] — Veri kaynağı
- [[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]] — Zaman serisi depolama
- [[Kök Neden Analizi (Root Cause Analysis - RCA)|RCA]] — Anomali sonrası kök neden analizi
- [[Temel Performans Göstergesi (Key Performance Indicator - KPI)|KPI]] — İzlenen performans metrikleri
