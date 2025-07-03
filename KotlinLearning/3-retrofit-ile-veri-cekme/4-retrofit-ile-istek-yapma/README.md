# 4. Retrofit ile İstek Yapma

Retrofit ile API'ye veri çekmek veya göndermek için arayüzde tanımladığın fonksiyonları çağırırsın.

## 4.1. Coroutine ile Asenkron İstek
En modern ve önerilen yöntem coroutine ile suspend fonksiyonları çağırmaktır.

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    val api = retrofit.create(ApiService::class.java)
    val kullanicilar = api.kullanicilariGetir()
    println(kullanicilar)
}
```

## 4.2. enqueue ile Callback Kullanımı (Klasik Yöntem)
Callback ile klasik asenkron istek yapılabilir.

```kotlin
api.kullanicilariGetir().enqueue(object : Callback<List<Kullanici>> {
    override fun onResponse(call: Call<List<Kullanici>>, response: Response<List<Kullanici>>) {
        if (response.isSuccessful) {
            val data = response.body()
            println(data)
        }
    }
    override fun onFailure(call: Call<List<Kullanici>>, t: Throwable) {
        println("Hata: ${t.message}")
    }
})
```

## 4.3. Response Handling
- Başarılı ve başarısız durumları kontrol et.
- Hata yönetimi için try-catch kullanabilirsin.

```kotlin
try {
    val cevap = api.kullanicilariGetir()
    // ...
} catch (e: Exception) {
    println("Hata: ${e.message}")
}
```

## Notlar
- Coroutine ile istek yapmak modern ve daha okunabilir bir yöntemdir.
- enqueue ile callback yöntemi eski projelerde kullanılabilir. 