# 3. Hilt Nedir ve Kurulum

Hilt, Android için geliştirilmiş bir dependency injection (bağımlılık enjeksiyonu) kütüphanesidir.

## 3.1. Hilt Nedir?
- Sınıflar arası bağımlılıkları otomatik olarak yönetir.
- Kodun daha modüler ve test edilebilir olmasını sağlar.
- Google tarafından resmi olarak desteklenir.

## 3.2. Avantajları
- Otomatik bağımlılık yönetimi
- Daha az boilerplate kod
- Kolay test edilebilirlik

## 3.3. Projeye Hilt Ekleme
build.gradle dosyana aşağıdaki satırları ekle:

```gradle
dependencies {
    implementation "com.google.dagger:hilt-android:2.48"
    kapt "com.google.dagger:hilt-android-compiler:2.48"
}
```

## 3.4. Application Sınıfı
Uygulama sınıfını Hilt ile işaretle:

```kotlin
@HiltAndroidApp
class MyApp : Application()
```

AndroidManifest.xml dosyasında:
```xml
<application
    android:name=".MyApp"
    ... >
```

## Notlar
- Hilt, ViewModel, Repository, Network gibi katmanlarda bağımlılıkları otomatik sağlar.
- Daha fazla bilgi: [Hilt Dokümantasyonu](https://developer.android.com/training/dependency-injection/hilt-android) 