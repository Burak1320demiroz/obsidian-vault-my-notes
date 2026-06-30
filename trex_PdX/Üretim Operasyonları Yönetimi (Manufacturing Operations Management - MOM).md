---
title: Üretim Operasyonları Yönetimi (MOM)
date: 2026-06-30
tags:
  - trex
  - üretim
  - otomasyon
aliases:
  - Manufacturing Operations Management
  - MOM
  - WEMS
---

# Üretim Operasyonları Yönetimi (MOM)

**MOM (Manufacturing Operations Management)**, fabrikanın üretim süreçlerini uçtan uca yöneten sistemlerin bütünüdür. Çoğu zaman [[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]] ile karıştırılır, ancak MOM aslında MES'i de kapsayan çok daha geniş bir çerçevedir.

## MOM'un Kapsamı (ISA-95 Standardına Göre)

MOM, fabrika zeminindeki operasyonları 4 ana sütunda inceler:

1. **Üretim Operasyonları (Production):** MES'in klasik alanıdır (İş emri, izlenebilirlik, [[Toplam Ekipman Etkinliği (Overall Equipment Effectiveness - OEE)|OEE]]).
2. **Kalite Operasyonları (Quality):** LIMS (Laboratuvar Bilgi Yönetim Sistemi) ve kestirimci kalite ([[Kestirimci Bakım ve Kalite (PdM - PdQ)|PdQ]]).
3. **Bakım Operasyonları (Maintenance):** CMMS (Bilgisayarlı Bakım Yönetim Sistemi) ve Kestirimci Bakım ([[Kestirimci Bakım ve Kalite (PdM - PdQ)|PdM]]).
4. **Envanter Operasyonları (Inventory):** Depo içi stok hareketleri, WMS.

## WEMS (Warehouse & Energy Management System) Çakışması

MOM çerçevesine genellikle enerji tüketimi izleme de dahil edilir.
**WEMS (Water & Energy Management System veya Warehouse & Energy Management System)** fabrikadaki su, gaz, elektrik tüketimlerini anlık izler. 
- Yapay zeka ile **"Makinenin ne kadar elektrik çektiğine bakarak rulmanın bozulmakta olduğunu anlamak"** (Enerji tabanlı PdM) mümkündür.
- Trex platformunda WEMS modülünden gelen anlık güç tüketimi verileri, makinenin mekanik sağlığını (PdM) tahmin etmek için harika bir dolaylı özelliktir.

> [!note] ERP - MOM - Otomasyon Hiyerarşisi
> 1. **[[Kurumsal Kaynak Planlama (Enterprise Resource Planning - ERP)|ERP]]** — Ne üretileceğini ve finansal planlamayı yapar (İş yönetimi).
> 2. **MOM (MES dahil)** — Üretimin fabrikada *nasıl* ve *ne zaman* yapılacağını yönetir. (Operasyon yönetimi).
> 3. **SCADA / PLC / [[Endüstriyel IoT Protokolleri (OPC-UA, MQTT, Modbus)|Edge]]** — Üretimi fiziksel olarak gerçekleştirir (Kontrol).
