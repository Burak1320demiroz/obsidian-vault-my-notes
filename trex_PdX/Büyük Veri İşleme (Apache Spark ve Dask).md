---
title: Büyük Veri İşleme (Spark ve Dask)
date: 2026-06-30
tags:
  - trex
  - büyük-veri
  - veri-mühendisliği
aliases:
  - Apache Spark
  - Dask
  - Big Data
---

# Büyük Veri İşleme Teknolojileri

Kestirimci bakım projelerinde, saniyede binlerce veri üreten makineler yıllarca çalıştığında veri boyutu Terabayt (TB) ve Petabayt (PB) seviyelerine ulaşır. Standart Python kütüphaneleri (Pandas, Scikit-Learn) veriyi tek bir makinenin RAM'ine yüklemeye çalıştığı için çöker (*Out of Memory*). Bu problemi çözmek için Dağıtık Hesaplama (Distributed Computing) araçları kullanılır.

## 1. Apache Spark

Büyük veri işleme endüstri standardıdır. Veriyi birden fazla sunucuya (cluster) dağıtarak RAM (In-memory) üzerinde paralel işler.

- **Kullanım:** [[ClickHouse Veritabanı (Columnar OLAP)|ClickHouse]]'dan çekilen devasa veri setlerini model eğitimine hazırlamak (ETL süreçleri) veya büyük XGBoost modellerini dağıtık olarak eğitmek (Spark MLlib).
- **Avantaj:** Çok olgundur, hata toleransı yüksektir.
- **Dezavantaj:** Kurulumu ve yönetimi çok zordur (JVM tabanlıdır, PySpark yazarken debug zordur).

## 2. Dask

Python ekosistemine özel olarak tasarlanmış, Pandas ve Numpy gibi araçların yatayda ölçeklenmesini sağlayan modern bir dağıtık hesaplama kütüphanesidir.

- **Kullanım:** Standart Python koduyla yazılmış [[Özellik Mühendisliği (Feature Engineering)|özellik mühendisliği]] veya makine öğrenmesi kodlarını (Scikit-Learn, XGBoost) hiçbir kod değiştirmeden sadece `dask.dataframe` kullanarak cluster üzerinde çalıştırmak.
- **Avantaj:** Python ekosistemiyle (Pandas/Scikit) %100 uyumludur. Geliştirici dostudur.
- **Dezavantaj:** Spark kadar köklü ve devasa clusterlarda Spark kadar stabil değildir.

> [!tip] Trex Yaklaşımı
> Yapay zeka takımındaki Python mühendislerinin alışkanlıklarını bozmamak ve hızlı geliştirme yapmak (prototipleme) için genellikle **Dask** tercih edilir. Çok daha devasa, kurumsal ve stabil ETL (Veri Boru Hattı) işleri için ise veri mühendisleri **Apache Spark** kullanır.
