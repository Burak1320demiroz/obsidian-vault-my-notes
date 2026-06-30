---
title: Üretim Yönetim Sistemi (MES)
date: 2026-06-29
tags:
  - trex
  - üretim
  - endüstri40
  - mes
aliases:
  - Üretim Yönetim Sistemi
---

# Üretim Yönetim Sistemi (MES)

**MES**, üretim sahasındaki operasyonları ==gerçek zamanlı== olarak izleyen, yöneten ve raporlayan yazılım sistemidir. Fabrika zemini (shop floor) ile üst yönetim arasındaki köprü görevini görür.

## Temel Görevleri

- **İş emri yönetimi:** Üretim emirlerini takip eder, önceliklendirir
- **Gerçek zamanlı izleme:** Makine durumları, üretim adetleri, duruş süreleri
- **Kalite kontrol:** Üretim sırasında kalite verilerini toplar ve sapmaları tespit eder
- **İzlenebilirlik (Traceability):** Hammaddeden bitmiş ürüne kadar tüm sürecin kaydı
- **Performans analizi:** [[Toplam Ekipman Etkinliği (Overall Equipment Effectiveness - OEE)|OEE]], verimlilik ve kayıp analizleri

## MES'in Katmanlar İçindeki Yeri

```
┌─────────────┐
│   [[Kurumsal Kaynak Planlama (Enterprise Resource Planning - ERP)|ERP]]   │  ← Planlama (Kurumsal düzey)
├─────────────┤
│   **MES**   │  ← Yürütme (Üretim sahası)
├─────────────┤
│  SCADA/PLC  │  ← Otomasyon (Makine düzeyi)
└─────────────┘
```

> [!info] Trex Bağlamı
> Trex MES sistemi; iş emirleri, duruş kodları, üretim sayaçları ve kalite verilerini merkezi bir veritabanında toplar. Bu veriler [[Temel Performans Göstergesi (Key Performance Indicator - KPI)|KPI]] dashboardları ve [[Kök Neden Analizi (Root Cause Analysis - RCA)|RCA]] analizleri için temel girdiyi oluşturur.

## ISA-95 Standardı

MES, **ISA-95** (IEC 62264) standardına göre **Level 3** katmanında yer alır. Bu standart, iş sistemleri ile kontrol sistemleri arasındaki entegrasyonu tanımlar.

## İlişkili Kavramlar

- [[Kurumsal Kaynak Planlama (Enterprise Resource Planning - ERP)|ERP]] — Üst düzey planlama ve kaynak yönetimi
- [[Toplam Ekipman Etkinliği (Overall Equipment Effectiveness - OEE)|OEE]] — Ekipman etkinlik ölçümü
- [[Temel Performans Göstergesi (Key Performance Indicator - KPI)|KPI]] — Performans göstergeleri
- [[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]] — MES verilerinin analitik sorgulanması
