---
title: LIME (Local Interpretable Model-agnostic Explanations)
date: 2026-06-30
tags:
  - trex
  - ai
  - açıklanabilirlik
  - makine-öğrenmesi
aliases:
  - Local Interpretable Model-agnostic Explanations
  - LIME
---

# LIME (Local Interpretable Model-agnostic Explanations)

**LIME**, tıpkı [[SHAP (SHapley Additive exPlanations)|SHAP]] gibi, karmaşık yapay zeka ("kara kutu") modellerinin neden o kararı verdiğini insanlara açıklayan bir [[Açıklanabilir Yapay Zeka (Explainable AI - XAI)|XAI]] yöntemidir. 

"Model-Agnostic" olması demek, modelin XGBoost, Derin Öğrenme veya Rastgele Orman (Random Forest) olmasından bağımsız olarak, modeli değiştirmeden dışarıdan çalışabilmesi demektir.

## LIME Nasıl Çalışır?

LIME tüm modelin genel davranışını (Global Interpretability) açıklamaya çalışmaz. Sadece ilgilendiğimiz **tek bir tahmini (Lokal)** açıklamaya odaklanır.

1. **Örnek Seçimi:** Açıklanmak istenen tek bir sensör verisi örneği seçilir (Örneğin saat 14:00'daki "Anormal" tahmini).
2. **Gürültü Ekleme:** O veri noktasının etrafında çok sayıda rastgele, benzer yeni veriler üretilir (Permütasyon).
3. **Tahmin Alma:** Üretilen bu sahte veriler kara kutu modele verilip sonuçları alınır.
4. **Basit Model Kurma:** Çıkan sonuçlar baz alınarak, sadece o lokal bölgede çalışan, basit ve insanlar tarafından anlaşılabilir olan Lineer Regresyon veya Karar Ağacı gibi doğrusal bir model eğitilir.
5. **Sonuç:** O anki tahminde en çok etkili olan faktörler (ör. Sıcaklık > 90°C) çıkarılır.

## LIME vs. SHAP

| Özellik | LIME | SHAP |
| :--- | :--- | :--- |
| **Hız** | Çok hızlı çalışır. | Özellikle büyük verilerde çok yavaştır (TreeSHAP hariç). |
| **Tutarlılık (Consistency)** | Tutarlı değildir. Aynı veri için bazen farklı açıklamalar üretebilir. | Teorik olarak oyun teorisine dayandığı için her zaman tutarlıdır. |
| **Kullanım Yeri** | Hızlı sonuç gereken, metin ve görsel analizlerinde çok başarılıdır. | Endüstriyel sensör ve tablo verilerinde (Tabular Data) endüstri standardıdır. |

> [!important] Trex Sisteminde Hangisi?
> Trex'in [[Kök Neden Analizi (Root Cause Analysis - RCA)|RCA]] ekranlarında, doğruluğunun tartışılmaz (matematiksel kanıtlanmış) olması gerektiği için genellikle **SHAP** kullanılır. Ancak modelin anlık (real-time) kararlarını açıklamak için çok daha hızlı olan **LIME** da hibrit bir yapıda kullanılabilir.
