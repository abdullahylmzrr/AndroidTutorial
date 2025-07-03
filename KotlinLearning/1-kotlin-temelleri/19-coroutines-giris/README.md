# 19. Coroutines'e Giriş

Coroutines, Kotlin'de asenkron ve paralel işlemler yapmak için kullanılır. Özellikle uzun süren işlemlerde (ağ, dosya, vs.) ana thread'i meşgul etmeden çalışmayı sağlar.

## 1. Temel Kavramlar
- `Coroutine`: Hafif, durdurulabilir iş parçacığı.
- `launch`: Yeni bir coroutine başlatır.
- `async`: Sonuç döndüren coroutine başlatır.
- `runBlocking`: Coroutine'leri başlatmak için ana fonksiyonda kullanılır.
- `delay`: Belirli bir süre bekler (asenkron uyku).

## 2. Basit Coroutine Örneği
```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    launch {
        delay(1000L)
        println("1 saniye sonra çalıştı!")
    }
    println("Coroutine başlatıldı")
}
```

## 3. async ile Sonuç Döndürme
```kotlin
fun main() = runBlocking {
    val sonuc = async {
        delay(500L)
        42
    }
    println("Sonuç: ${sonuc.await()}")
}
```

## Notlar
- Coroutines, performans ve verimlilik için modern Android uygulamalarında çok önemlidir.
- Coroutines kullanmak için `kotlinx-coroutines-core` kütüphanesi eklenmelidir. 