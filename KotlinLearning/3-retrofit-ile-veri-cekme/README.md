# 3. Retrofit ile Veri Çekme

Bu bölümde, Android uygulamasında internetten veri çekmek için kullanılan Retrofit kütüphanesini öğreneceksin. API'den veri almak için en çok tercih edilen yöntemlerden biridir.

## 3.1. Retrofit Nedir?
- REST API'lerle kolayca iletişim kurmamızı sağlayan bir kütüphanedir.
- JSON verilerini otomatik olarak Kotlin nesnelerine dönüştürebilir.

## 3.2. Temel Kavramlar
- **API:** Uygulamanın veri aldığı internet servisi.
- **Model:** API'den gelen verinin Kotlin'deki karşılığı (data class).
- **Service:** API isteklerinin tanımlandığı arayüz.

## 3.3. Basit Kullanım Adımları

### 1. Model Sınıfı Oluştur
```kotlin
data class Kullanici(
    val id: Int,
    val isim: String
)
```

### 2. API Servisi Tanımla
```kotlin
import retrofit2.http.GET

interface ApiService {
    @GET("kullanicilar")
    suspend fun kullanicilariGetir(): List<Kullanici>
}
```

### 3. Retrofit Nesnesi Oluştur
```kotlin
import retrofit2.Retrofit
import retrofit2.converter.gson.GsonConverterFactory

val retrofit = Retrofit.Builder()
    .baseUrl("https://ornekapi.com/")
    .addConverterFactory(GsonConverterFactory.create())
    .build()

val api = retrofit.create(ApiService::class.java)
```

### 4. Veriyi Çek (Coroutine ile)
```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    val kullanicilar = api.kullanicilariGetir()
    println(kullanicilar)
}
```

## 3.4. Notlar
- Gerçek uygulamada ağ işlemleri ViewModel içinde ve hata yönetimiyle yapılır.
- AndroidManifest.xml dosyasında internet izni (`<uses-permission android:name="android.permission.INTERNET" />`) eklenmelidir.

---

Bir sonraki adımda ViewModel ve Hilt ile bağımlılık yönetimini öğreneceğiz. 