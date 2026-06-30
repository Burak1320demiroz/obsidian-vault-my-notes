---
title: ClickHouse Veritabanı
date: 2026-06-29
tags:
  - trex
  - veritabanı
  - olap
  - büyükveri
aliases:
  - CH
---

# ClickHouse Veritabanı

**ClickHouse**, Yandex tarafından geliştirilen, ==sütun tabanlı (columnar)== açık kaynaklı OLAP veritabanı yönetim sistemidir. Milyarlarca satır üzerinde saniyeler içinde analitik sorgu çalıştırabilir.

## Neden ClickHouse?

| Özellik | Değer |
|---|---|
| **Mimari** | Columnar (sütun bazlı depolama) |
| **Sorgu Hızı** | Milyarlarca satırda < 1 saniye |
| **Sıkıştırma** | ~10x veri sıkıştırma oranı |
| **SQL Desteği** | Geniş SQL uyumluluğu |
| **Ölçeklenebilirlik** | Yatay ve dikey ölçeklenir |

## Columnar vs Row-Based

```
Row-Based (PostgreSQL):       Columnar (ClickHouse):
┌────┬──────┬─────┐           ┌────┬────┬────┐
│ id │ temp │ rpm │           │ id │ id │ id │  → id sütunu
├────┼──────┼─────┤           ├────┴────┴────┤
│ 1  │ 72.5 │ 1500│           │72.5│73.1│71.8│  → temp sütunu
│ 2  │ 73.1 │ 1480│           ├────┴────┴────┤
│ 3  │ 71.8 │ 1520│           │1500│1480│1520│  → rpm sütunu
└────┴──────┴─────┘           └────┴────┴────┘
```

> [!info] Ne Zaman ClickHouse?
> - **Yüksek hacimli zaman serisi verileri** (IoT sensör, log)
> - **Analitik sorgular** (GROUP BY, aggregation, OLAP)
> - **Dashboard ve raporlama** altyapısı
> 
> **Ne zaman değil?** CRUD ağırlıklı, transactional işlemler → [[PostgreSQL Veritabanı (RDBMS - OLTP)|PostgreSQL]] tercih et.

## Trex'te ClickHouse

[[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]] sisteminden akan sensör verileri (sıcaklık, titreşim, basınç, RPM) ClickHouse'a yazılır. [[Temel Performans Göstergesi (Key Performance Indicator - KPI)|KPI]] dashboardları ve [[Senaryo Analizi (What-if Analysis)|What-if Analizi]] simülasyonları bu veri üzerinde çalışır. [[Açıklanabilir Yapay Zeka (Explainable AI - XAI)|XAI]] modellerinin eğitim verileri de buradan çekilir.

## İlişkili Kavramlar

- [[PostgreSQL Veritabanı (RDBMS - OLTP)|PostgreSQL]] — OLTP iş yükü için tamamlayıcı veritabanı
- [[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]] — Veri kaynağı
- [[Temel Performans Göstergesi (Key Performance Indicator - KPI)|KPI]] — Analitik sorguların çıktısı
- [[Açıklanabilir Yapay Zeka (Explainable AI - XAI)|XAI]] — Model eğitim verisinin deposu
