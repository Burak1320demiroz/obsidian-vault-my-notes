---
title: Toplam Ekipman Etkinliği (OEE)
date: 2026-06-29
tags:
  - trex
  - üretim
  - performans
  - oee
aliases:
  - Toplam Ekipman Etkinliği
---

# Toplam Ekipman Etkinliği (OEE)

**OEE**, bir üretim ekipmanının ne kadar verimli kullanıldığını ölçen ==altın standart== metriktir. Üç temel bileşenin çarpımıyla hesaplanır.

## Formül

$$
OEE = \text{Kullanılabilirlik} \times \text{Performans} \times \text{Kalite}
$$

| Bileşen | Açıklama | Formül |
|---|---|---|
| **Kullanılabilirlik** | Planlanan sürede makinenin çalışma oranı | $\frac{\text{Çalışma Süresi}}{\text{Planlanan Süre}}$ |
| **Performans** | Gerçek hız / Tasarım hızı | $\frac{\text{Gerçek Üretim}}{\text{Teorik Kapasite}}$ |
| **Kalite** | Hatasız ürün oranı | $\frac{\text{İyi Ürün}}{\text{Toplam Üretim}}$ |

## Altı Büyük Kayıp (Six Big Losses)

1. **Arıza duruşları** → Kullanılabilirlik kaybı
2. **Setup / ayar süreleri** → Kullanılabilirlik kaybı
3. **Kısa duruşlar** → Performans kaybı
4. **Hız düşüşleri** → Performans kaybı
5. **Üretim hataları** → Kalite kaybı
6. **Başlangıç kayıpları** → Kalite kaybı

> [!tip] Dünya Sınıfı OEE
> Dünya sınıfı (World-Class) OEE değeri **%85** ve üzeridir. Çoğu fabrika **%60** civarında çalışır. Fark, ciddi bir iyileştirme potansiyeli anlamına gelir.

## Trex'te OEE

[[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]] sisteminden gelen duruş kodları, üretim sayaçları ve hurda verileri kullanılarak OEE otomatik olarak hesaplanır. Sonuçlar [[Temel Performans Göstergesi (Key Performance Indicator - KPI)|KPI]] panellerinde anlık olarak gösterilir.

## İlişkili Kavramlar

- [[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]] — OEE verisinin kaynağı
- [[Temel Performans Göstergesi (Key Performance Indicator - KPI)|KPI]] — OEE bir KPI'dır
- [[Senaryo Analizi (What-if Analysis)|What-if Analizi]] — OEE üzerinde senaryo simülasyonu
- [[Kök Neden Analizi (Root Cause Analysis - RCA)|RCA]] — Düşük OEE'nin kök nedenini bulmak
