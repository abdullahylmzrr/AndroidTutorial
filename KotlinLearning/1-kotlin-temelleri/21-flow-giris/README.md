# 21. Flow'a Giriş

Flow, Kotlin'de asenkron veri akışlarını yönetmek için kullanılır. Özellikle sürekli değişen verilerde (ör: sayaç, API'den gelen veriler) tercih edilir.

## 1. Temel Flow Oluşturma
```kotlin
import kotlinx.coroutines.flow.*
import kotlinx.coroutines.*

fun main() = runBlocking {
    val sayac = flow {
        for (i in 1..3) {
            emit(i) // Veri gönder
            delay(500L)
        }
    }
    sayac.collect { deger ->
        println("Gelen değer: $deger")
    }
}
```

## 2. emit ve collect
- `emit`: Flow'a veri gönderir.
- `collect`: Flow'dan gelen verileri toplar.

## 3. Flow'un Avantajları
- Hafif ve verimli asenkron veri akışı sağlar.
- Cancel (iptal) edilebilir.

## Notlar
- Flow, coroutines ile birlikte çalışır.
- Özellikle MVVM mimarisinde veri akışı için çok kullanılır. 