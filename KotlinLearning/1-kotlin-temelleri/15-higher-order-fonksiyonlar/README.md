# 15. Higher-Order Fonksiyonlar

Higher-order fonksiyonlar, fonksiyon parametresi alan veya fonksiyon döndüren fonksiyonlardır. Kotlin'de fonksiyonlar birer değişken gibi kullanılabilir.

## 1. Fonksiyon Parametresi Alan Fonksiyon
```kotlin
fun islemYap(a: Int, b: Int, islem: (Int, Int) -> Int): Int {
    return islem(a, b)
}

val toplam = islemYap(3, 5) { x, y -> x + y }
println(toplam) // 8
```

## 2. Fonksiyon Döndüren Fonksiyon
```kotlin
fun carpmaFonksiyonu(): (Int, Int) -> Int {
    return { a, b -> a * b }
}

val carp = carpmaFonksiyonu()
println(carp(2, 4)) // 8
```

## Notlar
- Higher-order fonksiyonlar, fonksiyonel programlamanın temelini oluşturur.
- Özellikle koleksiyon işlemlerinde ve callback yapılarında çok kullanılır. 