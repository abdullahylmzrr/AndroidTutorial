# 6. Fonksiyonlar

Fonksiyonlar, belirli bir işlemi gerçekleştiren kod bloklarıdır. Kodun tekrarını önler ve daha düzenli olmasını sağlar.

## 1. Temel Fonksiyon Tanımı
```kotlin
fun topla(a: Int, b: Int): Int {
    return a + b
}

val sonuc = topla(3, 5) // sonuc: 8
```
- `fun`: Fonksiyon tanımlamak için kullanılır.
- `a: Int, b: Int`: Parametreler ve türleri.
- `: Int`: Fonksiyonun dönüş tipi.

## 2. Birim (Unit) Fonksiyonlar
Dönüş tipi belirtmezseniz veya `Unit` yazarsanız, fonksiyon değer döndürmez.
```kotlin
fun selamla(isim: String) {
    println("Merhaba, $isim!")
}
```

## 3. Varsayılan ve İsimli Parametreler
```kotlin
fun carp(a: Int, b: Int = 2): Int {
    return a * b
}

val sonuc1 = carp(4)      // 8 (b=2 varsayılan)
val sonuc2 = carp(4, 3)   // 12
val sonuc3 = carp(b = 5, a = 2) // 10 (isimli parametre)
```

## 4. Tek Satırlık Fonksiyonlar
```kotlin
fun karesi(x: Int) = x * x
```

## Notlar
- Fonksiyonlar kodun okunabilirliğini ve tekrar kullanılabilirliğini artırır.
- Parametreler ve dönüş tipleri ile esnek fonksiyonlar yazabilirsin. 