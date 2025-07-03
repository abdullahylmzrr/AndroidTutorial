# 1. MVVM Mimari ve Proje Yapısı

MVVM (Model-View-ViewModel), modern Android uygulamalarında en çok tercih edilen mimari desenlerden biridir.

## 1.1. MVVM Nedir?
- **Model:** Veri ve iş mantığı katmanı (API, veritabanı, repository).
- **View:** Kullanıcı arayüzü (Compose ekranları, Activity, Fragment).
- **ViewModel:** View ile Model arasında köprü, veri yönetimi ve UI state'i.

## 1.2. Avantajları
- Kodun okunabilirliği ve sürdürülebilirliği artar.
- Test yazmak kolaylaşır.
- Katmanlar arası bağımlılık azalır.

## 1.3. Tipik Proje Klasör Yapısı
```
app/
  ├─ di/           # Hilt modülleri
  ├─ model/        # Veri modelleri
  ├─ network/      # Retrofit API servisleri
  ├─ repository/   # Veri kaynakları
  ├─ ui/           # Compose ekranları
  ├─ viewmodel/    # ViewModel sınıfları
```

## 1.4. MVVM Akış Şeması
1. Kullanıcı arayüzü (View) bir ViewModel'den veri ister.
2. ViewModel, Repository üzerinden Model katmanına ulaşır.
3. Model'den gelen veri ViewModel'de işlenir ve View'a aktarılır.

## Notlar
- MVVM, modern Android projelerinde standarttır.
- Katmanlar arası bağımlılığı azaltmak için dependency injection (Hilt) kullanılır. 