# 1. Compose Nedir ve Kurulum

Jetpack Compose, Android için modern, deklaratif bir kullanıcı arayüzü (UI) araç takımıdır. XML yerine doğrudan Kotlin kodu ile arayüz oluşturmanı sağlar.

## 1.1. Compose Nedir?
- UI'yi fonksiyonlarla tanımlarsın (Composable fonksiyonlar).
- Daha az kod, daha kolay okunabilirlik ve bakım.
- Google'ın önerdiği modern Android UI geliştirme yöntemi.

## 1.2. Avantajları
- XML olmadan arayüz tasarımı
- Kolay tema ve stil yönetimi
- Daha az hata, daha hızlı geliştirme

## 1.3. Temel Kavramlar
- **@Composable:** UI çizen fonksiyonlar bu anotasyonla işaretlenir.
- **State:** UI'ın güncel kalmasını sağlar.
- **Preview:** Kodun önizlemesini hızlıca görebilirsin.

## 1.4. Android Studio'da Compose Projesi Kurulumu
1. **Android Studio'yu aç** ve "New Project" seç.
2. "Empty Compose Activity" şablonunu seç.
3. Minimum SDK: API 21+ önerilir.
4. Proje oluşturulduğunda, `MainActivity.kt` içinde Compose kodu göreceksin.

## 1.5. build.gradle Ayarları
Aşağıdaki bağımlılıkların ekli olduğundan emin ol:
```gradle
dependencies {
    implementation "androidx.activity:activity-compose:1.7.2"
    implementation "androidx.compose.ui:ui:1.5.0"
    implementation "androidx.compose.material3:material3:1.1.2"
    implementation "androidx.compose.ui:ui-tooling-preview:1.5.0"
    debugImplementation "androidx.compose.ui:ui-tooling:1.5.0"
}
```

## 1.6. İlk Compose Fonksiyonu
```kotlin
@Composable
fun MerhabaDunya() {
    Text(text = "Merhaba, Compose!")
}
```

## Notlar
- Compose ile ilgili dökümantasyon: [developer.android.com/jetpack/compose](https://developer.android.com/jetpack/compose)
- Proje kurulumunda hata alırsan, Android Studio ve Gradle sürümlerini güncelle. 