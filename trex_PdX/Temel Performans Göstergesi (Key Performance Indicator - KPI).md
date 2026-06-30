---
title: Temel Performans Göstergesi (KPI)
date: 2026-06-29
tags:
  - trex
  - performans
  - yönetim
  - kpi
aliases:
  - Temel Performans Göstergesi
---

# Temel Performans Göstergesi (KPI)

**KPI**, bir organizasyonun veya sürecin belirlenen hedeflere ne kadar yaklaştığını ölçen ==sayısal göstergelerdir==. Doğru KPI seçimi, doğru kararlar almanın ön koşuludur.

## İyi Bir KPI'ın Özellikleri (SMART)

- **S**pecific — Belirli ve net tanımlı
- **M**easurable — Ölçülebilir
- **A**chievable — Ulaşılabilir
- **R**elevant — İşle ilgili
- **T**ime-bound — Zamana bağlı

## Üretimde Yaygın KPI'lar

| KPI | Açıklama | Hedef |
|---|---|---|
| [[Toplam Ekipman Etkinliği (Overall Equipment Effectiveness - OEE)|OEE]] | Toplam ekipman etkinliği | ≥ %85 |
| **MTBF** | Arızalar arası ortalama süre | ↑ Yüksek |
| **MTTR** | Ortalama onarım süresi | ↓ Düşük |
| **Hurda Oranı** | Hatalı ürün yüzdesi | ↓ Düşük |
| **Teslim Süresi** | Siparişten sevkiyata geçen süre | ↓ Düşük |
| **Enerji Tüketimi** | kWh / üretilen birim | ↓ Düşük |

> [!tip] Leading vs Lagging KPI
> - **Leading KPI:** Geleceği tahmin eder (bakım planına uyum oranı)
> - **Lagging KPI:** Geçmişi ölçer (aylık arıza sayısı)
> 
> En etkili dashboard'lar her iki türü de dengeli kullanır.

## Trex'te KPI

[[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]] ve [[Kurumsal Kaynak Planlama (Enterprise Resource Planning - ERP)|ERP]] verilerinden türetilen KPI'lar, [[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]] üzerinde hızlıca sorgulanır ve dashboard'larda anlık olarak görüntülenir. Sapma durumlarında [[Kök Neden Analizi (Root Cause Analysis - RCA)|RCA]] süreci tetiklenir.

## İlişkili Kavramlar

- [[Toplam Ekipman Etkinliği (Overall Equipment Effectiveness - OEE)|OEE]] — En kritik üretim KPI'ı
- [[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]] — KPI verilerinin birincil kaynağı
- [[Kurumsal Kaynak Planlama (Enterprise Resource Planning - ERP)|ERP]] — İş düzeyi KPI raporlaması
- [[Kök Neden Analizi (Root Cause Analysis - RCA)|RCA]] — KPI sapma nedenlerini bulma
