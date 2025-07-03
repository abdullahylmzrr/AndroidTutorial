# 20. Suspend Fonksiyonlar

Suspend fonksiyonlar, coroutine içinde çalışabilen, uzun süren işlemleri (ağ, dosya, vs.) asenkron olarak gerçekleştiren fonksiyonlardır.

## 1. Tanım ve Kullanım
```kotlin
suspend fun veriCek(): String {
    delay(1000L)
    return "Veri geldi!"
}

fun main() = runBlocking {
    println("Başladı")
    val sonuc = veriCek()
    println(sonuc)
}
```

## 2. Neden suspend?
- Uzun süren işlemler ana thread'i (UI) bloklamasın diye.
- Sadece coroutine içinde çağrılabilir.

## 3. Gerçek Hayatta Kullanım
- Retrofit ile ağ istekleri
- Veritabanı işlemleri

## Notlar
- `suspend` anahtar kelimesi, fonksiyonun askıya alınabilir olduğunu belirtir.
- Sadece coroutine veya başka bir suspend fonksiyon içinde çağrılabilir. 