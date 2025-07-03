# 9. Sınıflar ve Nesneler

Sınıflar, nesne tabanlı programlamanın temelidir. Nesneler ise sınıflardan üretilen gerçek örneklerdir.

## 1. Sınıf Tanımı
```kotlin
class Ogrenci(val isim: String, var yas: Int) {
    fun selamla() {
        println("Merhaba, ben $isim ve $yas yaşındayım.")
    }
}
```

## 2. Nesne Oluşturma
```kotlin
val ogrenci = Ogrenci("Ayşe", 21)
ogrenci.selamla() // Merhaba, ben Ayşe ve 21 yaşındayım.
```

## 3. Property ve Method
- **Property:** Sınıfın özellikleri (isim, yas)
- **Method:** Sınıfın fonksiyonları (selamla)

## 4. Primary ve Secondary Constructor
```kotlin
class Araba(val marka: String) {
    var model: String = ""
    constructor(marka: String, model: String) : this(marka) {
        this.model = model
    }
}
```

## Notlar
- Sınıflar, kodun daha düzenli ve tekrar kullanılabilir olmasını sağlar.
- Nesneler, sınıfların gerçek hayattaki karşılığıdır. 