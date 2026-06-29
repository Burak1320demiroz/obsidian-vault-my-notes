---
title: PostgreSQL Veritabanı
date: 2026-06-29
tags:
  - trex
  - veritabanı
  - oltp
  - sql
aliases:
  - Postgres
  - PG
---

# PostgreSQL Veritabanı

**PostgreSQL**, dünyanın en gelişmiş ==açık kaynaklı ilişkisel veritabanı== yönetim sistemidir. ACID uyumlu, genişletilebilir ve güvenilirdir.

## Temel Güçlü Yanları

- **ACID Uyumluluğu:** Veri bütünlüğünü garanti eder
- **Zengin Veri Tipleri:** JSON/JSONB, Array, HStore, UUID
- **Genişletilebilirlik:** Özel veri tipleri ve fonksiyonlar
- **Replikasyon:** Streaming ve logical replication

## OLTP vs OLAP

| Özellik | PostgreSQL (OLTP) | [[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]] (OLAP) |
|---|---|---|
| **İş Yükü** | INSERT, UPDATE, DELETE | SELECT, aggregation |
| **Sorgu Tipi** | Tekil kayıt erişimi | Milyonlarca satır tarama |
| **Kullanım** | Uygulama backend | Analitik ve raporlama |

> [!note] Tamamlayıcı Yaklaşım
> PostgreSQL ve ClickHouse **rakip değil, tamamlayıcıdır**. Operasyonel veriler PostgreSQL'de yaşar, analitik sorgular [[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]]'a replike edilir.

## Trex'te PostgreSQL

[[Kurumsal Kaynak Planlama (Enterprise Resource Planning - ERP)|ERP]] ve [[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]] sistemlerinin transactional veritabanı olarak kullanılır. İş emirleri, kullanıcı yönetimi ve konfigürasyon verileri burada saklanır.

## İlişkili Kavramlar

- [[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]] — Analitik katman (OLAP)
- [[Kurumsal Kaynak Planlama (Enterprise Resource Planning - ERP)|ERP]] — PostgreSQL üzerinde çalışan iş sistemi
- [[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]] — Operasyonel veri kaynağı
