# 16. Lambda İfadeleri

Lambda ifadeleri, isimsiz fonksiyonlardır. Özellikle koleksiyon işlemlerinde ve callback'lerde çok kullanılır.

## 1. Temel Lambda Tanımı
```kotlin
val karesi = { x: Int -> x * x }
println(karesi(4)) // 16
```

## 2. Fonksiyon Parametresi Olarak Lambda
```kotlin
fun islemYap(a: Int, b: Int, islem: (Int, Int) -> Int): Int {
    return islem(a, b)
}

val toplam = islemYap(2, 3) { x, y -> x + y }
println(toplam) // 5
```

## 3. Koleksiyon Fonksiyonlarında Lambda
```kotlin
val sayilar = listOf(1, 2, 3, 4)
val ciftler = sayilar.filter { it % 2 == 0 }
println(ciftler) // [2, 4]

val kareler = sayilar.map { it * it }
println(kareler) // [1, 4, 9, 16]
```

## Notlar
- Lambda ifadeleri, kodu daha kısa ve okunabilir yapar.
- `it` anahtar kelimesi, tek parametreli lambda'larda kullanılır. 