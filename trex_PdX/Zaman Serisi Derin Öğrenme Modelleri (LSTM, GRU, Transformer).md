---
title: Zaman Serisi Derin Öğrenme Modelleri
date: 2026-06-30
tags:
  - trex
  - derin-öğrenme
  - zaman-serisi
  - makine-öğrenmesi
aliases:
  - LSTM
  - GRU
  - Transformer
---

# Zaman Serisi Derin Öğrenme Modelleri

Kestirimci bakımda toplanan sensör verileri tarihsel bir sıraya sahiptir (zaman serisi). Standart algoritmalar sadece anlık duruma bakarken, zaman serisi derin öğrenme (Deep Learning) modelleri **geçmiş trendleri ve zamansal bağımlılıkları** "hatırlar".

## 1. LSTM (Long Short-Term Memory)

Geleneksel RNN'lerin (Recurrent Neural Network) uzun vadeli bağımlılıkları unutma sorununu (vanishing gradient) çözen, "hücre durumu" (cell state) ve geçit (gate) mekanizmalarına sahip derin öğrenme mimarisidir.

- **Kullanım:** Makinenin son 1 aydaki kademeli aşınmasını hatırlamak ve buna göre Kalan Faydalı Ömür (RUL - Remaining Useful Life) tahmini yapmak.
- **Avantaj:** Uzun zaman serilerinde mükemmel başarı.
- **Dezavantaj:** Eğitimi yavaş ve maliyetlidir.

## 2. GRU (Gated Recurrent Unit)

LSTM'in biraz daha sadeleştirilmiş ve optimize edilmiş versiyonudur. Hücre durumu yerine sadece gizli durum (hidden state) kullanır ve geçit sayısı daha azdır.

- **Kullanım:** LSTM ile aynı alanlarda kullanılır ancak daha az hesaplama gücü (Edge cihazlarda) gerektiğinde tercih edilir.
- **Avantaj:** LSTM'den daha hızlı eğitilir, benzer performans gösterir.

## 3. Transformer Modelleri (Time-Series Transformers)

NLP (Doğal Dil İşleme) alanında devrim yaratan (örn. ChatGPT) Transformer mimarisinin (Attention mekanizması) zaman serilerine uyarlanmış halidir. Veriyi sırayla okumak yerine **tüm zaman serisine aynı anda bakar** ve hangi zaman adımlarının birbiriyle ilişkili olduğuna odaklanır.

- **Kullanım:** Çok sayıda farklı sensörden (sıcaklık, basınç, akım, vibrasyon) gelen veriler arasındaki karmaşık çapraz ilişkileri (cross-correlation) yakalamak.
- **Avantaj:** Paralel işlenebildiği için çok büyük veri setlerinde (Spark/Dask kümelerinde) hızlı eğitilir. Uzun vadeli bağlamı LSTM'den bile daha iyi yakalar.

> [!important] Neden XGBoost yerine Derin Öğrenme?
> [[Özellik Mühendisliği (Feature Engineering)|Özellik Mühendisliği]] mükemmel yapıldığında XGBoost zaman serilerinde iyi sonuç verir. Ancak veri çok karmaşıksa, manuel özellik mühendisliği yapmadan (ham veriyi doğrudan vererek) zamansal trendleri çıkartmak için LSTM veya Transformer modelleri vazgeçilmezdir.

## İlişkili Kavramlar
- [[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]] — Zaman serisi verilerinin saklandığı yer.
- [[Anomali Tespiti Modelleri (Autoencoder)|Autoencoder]] — Zaman serilerinde anomali tespiti alternatifi.
