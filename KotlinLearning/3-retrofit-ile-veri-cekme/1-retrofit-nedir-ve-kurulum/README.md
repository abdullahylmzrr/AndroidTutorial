# 1. Retrofit Nedir ve Kurulum

Retrofit, Android'de REST API'lerle kolayca iletişim kurmak için kullanılan popüler bir kütüphanedir.

## 1.1. Retrofit Nedir?
- HTTP isteklerini (GET, POST, PUT, DELETE) kolayca yapmanı sağlar.
- JSON verilerini otomatik olarak Kotlin nesnelerine dönüştürür.
- Temiz, okunabilir ve test edilebilir kod yazmanı kolaylaştırır.

## 1.2. Avantajları
- Kolay kullanım
- Otomatik veri dönüşümü (Gson, Moshi, vb.)
- Hata yönetimi ve asenkron istek desteği

## 1.3. Projeye Retrofit Ekleme
build.gradle dosyana aşağıdaki satırları ekle:

```gradle
dependencies {
    implementation 'com.squareup.retrofit2:retrofit:2.9.0'
    implementation 'com.squareup.retrofit2:converter-gson:2.9.0'
}
```

## 1.4. Temel Kurulum
```kotlin
import retrofit2.Retrofit
import retrofit2.converter.gson.GsonConverterFactory

val retrofit = Retrofit.Builder()
    .baseUrl("https://api.ornek.com/")
    .addConverterFactory(GsonConverterFactory.create())
    .build()
```

## Notlar
- API ile iletişim için internet izni eklemeyi unutma:
  `<uses-permission android:name="android.permission.INTERNET" />`
- Daha fazla bilgi: [Retrofit Dokümantasyonu](https://square.github.io/retrofit/) 