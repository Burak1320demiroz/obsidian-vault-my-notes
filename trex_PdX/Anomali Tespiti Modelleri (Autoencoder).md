---
title: Anomali Tespiti Modelleri (Autoencoder)
date: 2026-06-30
tags:
  - trex
  - derin-öğrenme
  - anomali-tespiti
aliases:
  - Autoencoder
  - Otonkodlayıcı
---

# Anomali Tespiti Modelleri: Autoencoder

**Autoencoder (Otokodlayıcı)**, girdiyi önce sıkıştıran (darboğaz - bottleneck) sonra da girdinin aynısını tekrar oluşturmaya (reconstruct) çalışan bir yapay sinir ağı mimarisidir. Bu model **Gözetimsiz Öğrenme (Unsupervised Learning)** ile çalışır.

## Kestirimci Bakımda (PdM) Nasıl Çalışır?

Endüstriyel verilerde en büyük sorun **arızalı verinin (etiketin) çok az, normal çalışma verisinin ise çok fazla** olmasıdır. 

1. **Eğitim:** Autoencoder, makinenin **sadece sağlam (normal) çalıştığı** dönemlerdeki sensör verileriyle eğitilir. Ağ, normal veriyi nasıl sıkıştırıp yeniden oluşturacağını (decode) çok iyi öğrenir.
2. **Tahmin (İzleme):** Makine çalışırken yeni sensör verileri ağa beslenir.
3. **Anomali Tespiti:** Eğer makinede bir arıza belirtisi veya anormallik (örneğin daha önce hiç görülmemiş bir frekansta titreşim) başlarsa, ağ bunu daha önce görmediği için düzgün bir şekilde yeniden oluşturamaz.
4. **Reconstruction Error (Yeniden Oluşturma Hatası):** Girdi ile ağın çıktısı arasındaki fark (hata) aniden yükselir. Bu hata bir eşiği aştığında [[Nightwatch (Anomali Tespiti ve İzleme Sistemi)|Nightwatch]] sistemi alarm üretir.

## Avantajları

- **Etiketli Veriye İhtiyaç Yoktur:** "Bu arızadır" diye işaretlenmiş geçmiş veri (log) olmasa bile kullanılabilir.
- **Bilinmeyen Arızaları Yakalar:** Model "normal"i öğrendiği için, daha önce tarihte hiç yaşanmamış **yepyeni bir arıza türünü** bile tespit edebilir (Zero-day anomaly).
- Sinyal gürültüsünü (noise) filtreleme özelliğine sahiptir.

## Mimarisi

- **Encoder:** Yüksek boyutlu sensör verisini (ör. 100 sensör) daha düşük boyutlu (gizli uzay / latent space) bir forma sıkıştırır.
- **Bottleneck:** Sıkıştırılmış bilginin bulunduğu en dar katman. Model burada verinin "özünü" öğrenmeye zorlanır.
- **Decoder:** Sıkıştırılmış veriyi tekrar orijinal 100 sensör boyutuna açmaya çalışır.

> [!note] Hibrit Yaklaşımlar
> Zaman serilerinde anomali tespiti için standart ileri beslemeli ağlar yerine genellikle **LSTM-Autoencoder** mimarisi kullanılır. Bu sayede hem zaman sırası hem de boyut indirgeme aynı anda yapılır.
