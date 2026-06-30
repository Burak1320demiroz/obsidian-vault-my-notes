---
title: Senaryo Analizi (What-if Analysis)
date: 2026-06-29
tags:
  - trex
  - analiz
  - planlama
  - simülasyon
aliases:
  - What-if Analysis
  - Senaryo Analizi
---

# Senaryo Analizi (What-if Analysis)

**What-if Analizi**, belirli değişkenleri değiştirerek =="Ya ... olursa?"== sorusuna cevap arayan bir senaryo simülasyon yöntemidir. Karar vericilere risk ve fırsatları önceden görme imkânı tanır.

## Nasıl Çalışır?

1. **Baz senaryo** oluştur (mevcut durum verileri)
2. Bir veya birden fazla **değişkeni değiştir** (parametre)
3. Sonuçları baz senaryoyla **karşılaştır**
4. Riskleri ve fırsatları **değerlendir**

## Üretimde Kullanım Örnekleri

| Soru | Değişen Parametre | Etki |
|---|---|---|
| "Vardiya sayısını artırsak?" | Çalışma süresi | [[Toplam Ekipman Etkinliği (Overall Equipment Effectiveness - OEE)|OEE]] kullanılabilirlik değişimi |
| "Hammadde tedarikçisi değişse?" | Kalite oranı | Hurda ve fire maliyeti |
| "Bakım periyodunu kısaltsak?" | Duruş sıklığı | Arıza olasılığı ve uptime |
| "Yeni makine alsak?" | Kapasite | Darboğaz analizi |

> [!warning] Dikkat
> What-if analizi, modelin doğruluğuna bağlıdır. Kalitesiz veri → yanıltıcı sonuçlar. Verinin güvenilirliğini [[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]] ve [[Kurumsal Kaynak Planlama (Enterprise Resource Planning - ERP)|ERP]] sistemleriyle çapraz doğrulamak kritiktir.

## Trex'te What-if

[[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]] üzerindeki tarihsel veriler kullanılarak farklı üretim senaryoları simüle edilir. [[Açıklanabilir Yapay Zeka (Explainable AI - XAI)|XAI]] modelleri sayesinde her senaryonun sonucu sadece sayısal değil, **açıklanabilir** şekilde sunulur.

## İlişkili Kavramlar

- [[Toplam Ekipman Etkinliği (Overall Equipment Effectiveness - OEE)|OEE]] — Senaryo sonuçlarının temel metriği
- [[Temel Performans Göstergesi (Key Performance Indicator - KPI)|KPI]] — Hedeflerle karşılaştırma
- [[Kök Neden Analizi (Root Cause Analysis - RCA)|RCA]] — Geçmiş sorunlardan senaryo üretme
- [[Açıklanabilir Yapay Zeka (Explainable AI - XAI)|XAI]] — Senaryo sonuçlarının açıklanabilirliği
