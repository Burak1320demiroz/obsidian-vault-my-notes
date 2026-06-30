---
title: Kurumsal Kaynak Planlama (ERP)
date: 2026-06-29
tags:
  - trex
  - yönetim
  - planlama
  - erp
aliases:
  - Kurumsal Kaynak Planlama
---

# Kurumsal Kaynak Planlama (ERP)

**ERP**, bir organizasyonun ==tüm iş süreçlerini== tek bir entegre sistem altında yöneten kurumsal yazılım platformudur. Finans, satın alma, üretim planlama, insan kaynakları ve satış gibi modülleri birleştirir.

## Temel Modüller

| Modül | İşlev |
|---|---|
| **Finans** | Muhasebe, bütçe, maliyet takibi |
| **Üretim Planlama** | MRP, kapasite planlama, iş emirleri |
| **Satın Alma** | Tedarikçi yönetimi, sipariş takibi |
| **Satış & Dağıtım** | Müşteri siparişleri, sevkiyat |
| **İnsan Kaynakları** | Personel, vardiya, maaş yönetimi |
| **Bakım (PM)** | Planlı/plansız bakım yönetimi |

## ERP vs MES

| Özellik | [[Kurumsal Kaynak Planlama (Enterprise Resource Planning - ERP)|ERP]] | [[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]] |
|---|---|---|
| **Odak** | İşletme geneli | Üretim sahası |
| **Zaman** | Günlük/Haftalık plan | Gerçek zamanlı |
| **Veri** | Planlanan değerler | Gerçekleşen değerler |
| **Katman** | ISA-95 Level 4 | ISA-95 Level 3 |

> [!note] Entegrasyon
> ERP, üretim **planını** yapar; [[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]], bu planın sahada nasıl **yürütüldüğünü** izler. İkisi arasındaki veri akışı, verimli üretimin temelidir.

## Yaygın ERP Sistemleri

- SAP S/4HANA
- Oracle ERP Cloud
- Microsoft Dynamics 365
- IFS, Infor, QAD

## İlişkili Kavramlar

- [[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]] — Üretim sahası yürütme katmanı
- [[Temel Performans Göstergesi (Key Performance Indicator - KPI)|KPI]] — ERP'nin raporladığı iş metrikleri
- [[Toplam Ekipman Etkinliği (Overall Equipment Effectiveness - OEE)|OEE]] — Üretim performans ölçümü
- [[PostgreSQL Veritabanı (RDBMS - OLTP)|PostgreSQL]] — ERP sistemlerinin sıkça kullandığı veritabanı
