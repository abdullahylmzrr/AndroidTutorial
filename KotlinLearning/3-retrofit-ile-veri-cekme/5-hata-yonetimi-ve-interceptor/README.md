# 5. Hata Yönetimi ve Interceptor

Retrofit ile API isteklerinde hata yönetimi ve interceptor kullanımı önemlidir.

## 5.1. Hata Yönetimi
- API'den dönen yanıtı kontrol et.
- Hataları try-catch ile yakala.

```kotlin
try {
    val cevap = api.kullanicilariGetir()
    if (cevap.isNotEmpty()) {
        println("Veri geldi!")
    } else {
        println("Boş veri!")
    }
} catch (e: Exception) {
    println("Hata: ${e.message}")
}
```

## 5.2. Response.isSuccessful Kullanımı
```kotlin
val response = apiCall.execute()
if (response.isSuccessful) {
    val data = response.body()
    // ...
} else {
    println("API Hatası: ${response.code()}")
}
```

## 5.3. Interceptor ile İstek/Yanıtı Yakalama
Interceptor, istek veya yanıtı değiştirmek veya loglamak için kullanılır.

```kotlin
import okhttp3.Interceptor
import okhttp3.OkHttpClient

val interceptor = Interceptor { chain ->
    val request = chain.request()
    println("İstek: ${request.url}")
    val response = chain.proceed(request)
    println("Yanıt: ${response.code}")
    response
}

val client = OkHttpClient.Builder()
    .addInterceptor(interceptor)
    .build()

val retrofit = Retrofit.Builder()
    .baseUrl("https://api.ornek.com/")
    .client(client)
    .addConverterFactory(GsonConverterFactory.create())
    .build()
```

## Notlar
- Hata yönetimi, uygulamanın çökmesini önler.
- Interceptor ile loglama, header ekleme gibi işlemler kolayca yapılır. 