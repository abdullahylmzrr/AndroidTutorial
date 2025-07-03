# 22. Hata Yönetimi

Hata yönetimi, programın beklenmeyen durumlarda çökmesini önler. Kotlin'de hata yönetimi için try-catch-finally blokları ve throw anahtar kelimesi kullanılır.

## 1. try-catch
```kotlin
try {
    val bolum = 10 / 0
} catch (e: ArithmeticException) {
    println("Hata: ${e.message}")
}
```

## 2. finally
Her durumda çalışan bloktur (hata olsa da olmasa da).
```kotlin
try {
    println("İşlem başlıyor")
} finally {
    println("Her durumda çalışır")
}
```

## 3. throw ile Hata Fırlatma
```kotlin
fun pozitifMi(sayi: Int) {
    if (sayi < 0) throw IllegalArgumentException("Sayı pozitif olmalı!")
}

pozitifMi(-5) // Hata fırlatır
```

## 4. Özel Hata Sınıfı
```kotlin
class BenimHata(mesaj: String) : Exception(mesaj)

throw BenimHata("Özel hata mesajı")
```

## Notlar
- Hataları yakalamak, uygulamanın kararlı çalışmasını sağlar.
- Hata mesajlarını kullanıcıya dostça göstermek önemlidir. 