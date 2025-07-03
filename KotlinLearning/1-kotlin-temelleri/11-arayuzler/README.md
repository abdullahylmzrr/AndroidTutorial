# 11. Arayüzler (Interface)

Arayüzler, bir sınıfın hangi fonksiyonları içermesi gerektiğini belirler. Kotlin'de çoklu arayüz uygulanabilir.

## 1. Arayüz Tanımı
```kotlin
interface Ucan {
    fun uc()
}

class Kus : Ucan {
    override fun uc() {
        println("Kuş uçuyor")
    }
}
```

## 2. Çoklu Arayüz
Bir sınıf birden fazla arayüzü uygulayabilir.
```kotlin
interface Yuzebilen {
    fun yuz()
}

class Ordek : Ucan, Yuzebilen {
    override fun uc() { println("Ördek uçuyor") }
    override fun yuz() { println("Ördek yüzüyor") }
}
```

## 3. Default Fonksiyonlar
Arayüzde gövdesi olan fonksiyonlar tanımlanabilir.
```kotlin
interface Calisabilir {
    fun calis() { println("Çalışıyor...") }
}

class Robot : Calisabilir
```

## Notlar
- Arayüzler, çoklu kalıtım ihtiyacını karşılar.
- Sınıflar, arayüzdeki fonksiyonları override etmek zorundadır (default hariç). 