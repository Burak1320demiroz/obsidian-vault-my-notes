---
title: Kestirimci Bakım ve Kalite (PdM - PdQ)
date: 2026-06-30
tags:
  - trex
  - kestirimci-bakım
  - kestirimci-kalite
  - ai
aliases:
  - Predictive Maintenance
  - PdM
  - Predictive Quality
  - PdQ
---

# Kestirimci Bakım ve Kalite (PdM - PdQ)

Yapay zekâ destekli üretim operasyonları temel olarak makine sağlığına odaklanan **PdM** ve ürün kalitesine odaklanan **PdQ** olmak üzere iki ana stratejiyi barındırır. Bu iki sistem [[Toplam Ekipman Etkinliği (Overall Equipment Effectiveness - OEE)|OEE]] skorunu doğrudan artırmak için tasarlanmıştır.

## Kestirimci Bakım (Predictive Maintenance - PdM)

Makinenin veya bileşenlerinin mevcut çalışma koşullarını analiz ederek, gelecekteki olası arızaları meydana gelmeden **önce** tahmin etme sürecidir.

- **Hedef:** Beklenmedik duruşları (downtime) sıfıra indirmek ve gereksiz planlı bakım maliyetlerini düşürmek.
- **Veri Kaynağı:** Titreşim, sıcaklık, basınç, motor akımı gibi sürekli akan sensör verileri.
- **Modeller:** [[Zaman Serisi Derin Öğrenme Modelleri (LSTM, GRU, Transformer)|LSTM]], [[Anomali Tespiti Modelleri (Autoencoder)|Autoencoder]], XGBoost.
- **Örnek:** "CNC tezgahının 3. eksen motorunda 48 saat içinde %85 ihtimalle rulman arızası bekleniyor."

## Kestirimci Kalite (Predictive Quality - PdQ)

Üretim sürecindeki parametreleri (sıcaklık, basınç, hız, hammadde özellikleri) anlık olarak izleyerek, o an üretilmekte olan ürünün kalite standartlarını karşılayıp karşılamayacağını **ürün daha banttan çıkmadan** tahmin etmektir.

- **Hedef:** Iskarta (hurda) ve yeniden işlem (rework) oranlarını düşürmek.
- **Veri Kaynağı:** Üretim parametreleri (reçete), ortam koşulları, geçmiş kalite test sonuçları (laboratuvar).
- **Modeller:** Sınıflandırma ve regresyon modelleri.
- **Örnek:** "Plastik enjeksiyon makinesindeki mevcut eriyik sıcaklığı ve enjeksiyon basıncı trendine göre, bu partideki ürünlerde çekme (shrinkage) hatası riski %90."

> [!tip] PdM ve PdQ Arasındaki İlişki
> Makinelerin kötü kondisyonda çalışması genellikle önce kalite hatalarına (PdQ alarmlarına), daha sonra da fiziksel kırılmalara (PdM alarmlarına) yol açar. Trex sisteminde [[Nightwatch (Anomali Tespiti ve İzleme Sistemi)|Nightwatch]] her ikisini de gözetler.

## İlişkili Kavramlar
- [[Kök Neden Analizi (Root Cause Analysis - RCA)|RCA]] — Sorun tespit edildikten sonra nedeninin araştırılması.
- [[Senaryo Analizi (What-if Analysis)|What-if Analizi]] — "Sıcaklığı 5 derece düşürürsek kalite riski azalır mı?" sorusunun cevabı.
