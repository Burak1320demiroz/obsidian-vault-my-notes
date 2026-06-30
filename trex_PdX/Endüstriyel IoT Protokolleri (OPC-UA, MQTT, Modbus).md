---
title: Endüstriyel IoT Protokolleri
date: 2026-06-30
tags:
  - trex
  - iot
  - otomasyon
  - protokol
aliases:
  - OPC-UA
  - Modbus
  - MQTT
  - EtherNet/IP
  - Edge Connector
---

# Endüstriyel IoT Protokolleri

Üretim sahasından (shop floor) veri toplamak, kestirimci bakım sürecinin ilk adımıdır. Makinelerdeki sensör ve PLC (Programmable Logic Controller) verilerini merkezi sisteme ([[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]]) aktarmak için endüstriyel ağ protokolleri ve **Edge Connector**'ler kullanılır.

## Temel Protokoller

| Protokol           | Özellik                                                                                       | Kullanım Senaryosu                                                                         |
| :----------------- | :-------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------- |
| **OPC-UA**         | Platform bağımsız, güvenli, semantik veri modeli sunar.                                       | Modern makinelerin MES/SCADA sistemleriyle standart ve güvenli haberleşmesi.               |
| **Modbus TCP/RTU** | Çok eski ama en yaygın protokoldür. RTU seri hat (RS485), TCP ise ethernet üzerinden çalışır. | Basit sensörlerin, motor sürücülerinin veya eski nesil PLC'lerin verisini okumak.          |
| **MQTT**           | Publish/Subscribe mimarisiyle çalışır. Çok hafif ve düşük bant genişliği tüketir.             | Edge cihazlarından buluta veya merkezi sunucuya (broker) asenkron telemetri verisi basmak. |
| **EtherNet/IP**    | Standart Ethernet altyapısını kullanan, yüksek hızlı endüstriyel ağ protokolüdür.             | Allen-Bradley/Rockwell PLC'leri ile fabrika ağında gerçek zamanlı haberleşme.              |

## Edge Connector Yaklaşımı

Ham makine verileri çok yüksek frekanslıdır (örneğin milisaniyede bir titreşim verisi). Bu veriyi doğrudan buluta veya ana veritabanına göndermek ağ trafiğini kilitler.

**Edge Connector (Uç Cihaz Yazılımı):** Makinelerin hemen yanına kurulan veya fabrika lokalinde çalışan ara katmandır.
- Protokol çevirisi yapar (Örn: Modbus'tan okur, MQTT'ye çevirir).
- Ön işleme yapar (Örn: 1000 titreşim verisinin sadece saniyelik ortalamasını, RMS değerini ve max/min değerlerini gönderir).
- İnternet/ağ koptuğunda veriyi lokalde tutar (buffer), ağ gelince iletir.

> [!info] Trex Mimarisi
> Sahadaki makinelerden (Modbus, OPC-UA) toplanan sensör verileri, Edge Connector'ler vasıtasıyla optimize edilir ve yüksek hızda analiz edilmek üzere [[Üretim Yönetim Sistemi (Manufacturing Execution System - MES)|MES]] üzerinden veya doğrudan [[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]] veritabanına basılır.
