# Google Play Store - Veri Analizi ve Özellik Mühendisliği (EDA & Feature Engineering)

Bu proje, Google Play Store uygulamalarına ait veri seti üzerinde Keşifsel Veri Analizi (EDA) ve Özellik Mühendisliği (Feature Engineering) işlemlerini gerçekleştirmek amacıyla oluşturulmuştur. Proje kapsamında kirli/düzensiz ham veriler analiz edilebilir, sayısal formatlara dönüştürülmüş ve modellemeye hazır hale getirilmiştir.

## 🛠️ Kullanılan Teknolojiler ve Kütüphaneler

Veri işleme ve görselleştirme süreçleri için aşağıdaki Python kütüphaneleri kullanılmıştır:
* **Veri İşleme:** `pandas`, `numpy`
* **Veri Görselleştirme:** `seaborn`, `matplotlib.pyplot`

## 📂 Veri Seti
Projede `17-googleplaystore.csv` isimli veri seti kullanılmıştır. Orijinal veri seti 10.841 satır ve 13 sütundan (`App`, `Category`, `Rating`, `Reviews`, `Size`, `Installs`, `Type`, `Price`, vb.) oluşmaktadır.

## 🚀 Proje Adımları

Notebook içerisinde sırasıyla aşağıdaki veri temizleme ve dönüştürme adımları uygulanmıştır:

### 1. Veri Temizleme (Data Cleaning)
* **Reviews Sütunu:** İçerisindeki metinsel (non-numeric) değerler ayıklanarak tam sayı (`int`) formatına dönüştürülmüştür.
* **Size Sütunu:** Boyut verisindeki "M" (Megabayt) ve "k" (Kilobayt) gibi ibareler sayısal katsayılara dönüştürülmüş, "Varies with device" gibi belirsiz değerler temizlenerek standart bir sayısal formata getirilmiştir.
* **Installs ve Price Sütunları:** Verilerin içerisinde yer alan `+`, `,`, ve `$` gibi matematiksel işleme engel olan özel karakterler temizlenmiştir. `Price` sütunu `float` tipine dönüştürülmüştür.
* **Tekrar Eden Veriler:** `App` (Uygulama adı) sütunu baz alınarak tekrar eden (duplicate) kayıtlar veri setinden çıkarılmıştır.

### 2. Özellik Mühendisliği (Feature Engineering)
* **Tarih Değişkenleri Üretimi:** `Last Updated` sütunu öncelikle `datetime` objesine dönüştürülmüştür. Ardından bu sütun kullanılarak `Day` (Gün), `Month` (Ay) ve `Year` (Yıl) adında üç yeni özellik (feature) elde edilmiştir.
* **Hedef Kodlama (Mean Encoding):** `Genres` (Türler) gibi kategorik veriler, `Installs` değerlerinin ortalaması baz alınarak sayısal değerlere (`Genres Encoded`) dönüştürülmüştür.
* **Değişken Ayrımı:** İleriki makine öğrenmesi adımları için özellikler sayısal (numerical) ve kategorik (categorical) olmak üzere iki farklı listeye ayrıştırılmıştır.

## ⚙️ Nasıl Çalıştırılır?

1. Kodu çalıştırmak için proje dizininde bir sanal ortam oluşturun veya gerekli kütüphaneleri kurun:
   ```bash
   pip install pandas numpy matplotlib seaborn
   
