# 3. Network ve API Servisi

MVVM'de network katmanı, API ile iletişimi sağlar. Retrofit en çok kullanılan kütüphanedir.

## 3.1. Retrofit API Servisi
API'den veri çekmek için arayüz tanımlanır.
```kotlin
import retrofit2.http.GET

interface ApiService {
    @GET("kullanicilar")
    suspend fun kullanicilariGetir(): List<Kullanici>
}
```

## 3.2. Retrofit Kurulumu
```kotlin
val retrofit = Retrofit.Builder()
    .baseUrl("https://api.ornek.com/")
    .addConverterFactory(GsonConverterFactory.create())
    .build()

val api = retrofit.create(ApiService::class.java)
```

## Notlar
- API servisi, repository tarafından kullanılır.
- Network işlemleri coroutine ile asenkron yapılır. 