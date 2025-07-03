# 1. Kotlin Temelleri

Bu bölümde Kotlin dilinin temellerini öğreneceksin. Hiç bilmeyen biri için sade ve bol örnekli bir anlatım olacak. Kodları kendi bilgisayarında çalıştırarak denemeni öneririm.

## 1.1. Değişkenler ve Veri Tipleri

```kotlin
val sabitSayi: Int = 10 // Değeri değiştirilemez
var degistirilebilirSayi = 20 // Türü otomatik algılanır, değeri değiştirilebilir
degistirilebilirSayi = 30
```

## 1.2. Fonksiyonlar

```kotlin
fun topla(a: Int, b: Int): Int {
    return a + b
}

val sonuc = topla(3, 5) // sonuc: 8
```

## 1.3. Sınıflar ve Nesneler

```kotlin
class Ogrenci(val isim: String, var yas: Int) {
    fun selamla() {
        println("Merhaba, ben $isim ve $yas yaşındayım.")
    }
}

val ogrenci = Ogrenci("Ayşe", 21)
ogrenci.selamla() // Merhaba, ben Ayşe ve 21 yaşındayım.
```

## 1.4. Coroutines (Asenkron Programlama)
Kotlin'de coroutines, arka planda işlemler yapmak için kullanılır. Özellikle Android'de ana thread'i (UI) meşgul etmeden işlemler yapmak için çok önemlidir.

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

- `runBlocking`: Ana thread'i coroutine bitene kadar bekletir (örneklerde kullanılır).
- `launch`: Yeni bir coroutine başlatır.
- `delay`: Belirtilen süre kadar bekler (asenkron uyku).

## 1.5. Flow (Akışlar)
Akışlar, veri akışını yönetmek için kullanılır. Özellikle sürekli değişen verilerde (ör: sayaç, API'den gelen veriler) kullanılır.

```kotlin
import kotlinx.coroutines.*
import kotlinx.coroutines.flow.*

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

- `flow { ... }`: Akış başlatır.
- `emit`: Akışa veri gönderir.
- `collect`: Akıştan gelen verileri toplar.

---

Bir sonraki adımda Jetpack Compose ile modern Android arayüzü geliştirmeyi öğreneceğiz. 