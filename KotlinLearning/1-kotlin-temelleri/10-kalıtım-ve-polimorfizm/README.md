# 10. Kalıtım ve Polimorfizm

Kalıtım, bir sınıfın başka bir sınıftan özellik ve davranışları devralmasını sağlar. Polimorfizm ise, bir nesnenin birden fazla biçimde davranabilmesidir.

## 1. open ve override
- Kotlin'de bir sınıfın miras alınabilmesi için `open` anahtar kelimesiyle tanımlanması gerekir.

```kotlin
open class Hayvan {
    open fun sesCikar() {
        println("Hayvan ses çıkarıyor")
    }
}

class Kedi : Hayvan() {
    override fun sesCikar() {
        println("Miyav")
    }
}

val hayvan: Hayvan = Kedi()
hayvan.sesCikar() // Miyav
```

## 2. super ile Üst Sınıfa Erişim
```kotlin
class Kopek : Hayvan() {
    override fun sesCikar() {
        super.sesCikar()
        println("Hav hav")
    }
}
```

## 3. abstract Sınıflar
- Soyut sınıflar, bazı fonksiyonları alt sınıflarda zorunlu kılar.

```kotlin
abstract class Sekil {
    abstract fun alan(): Double
}

class Kare(val kenar: Double) : Sekil() {
    override fun alan() = kenar * kenar
}
```

## Notlar
- Kalıtım, kod tekrarını azaltır.
- Polimorfizm, esnek ve genişletilebilir kod yazmayı sağlar. 