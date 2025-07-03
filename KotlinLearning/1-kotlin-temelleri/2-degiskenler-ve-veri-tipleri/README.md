# 2. Değişkenler ve Veri Tipleri

Kotlin'de iki tür değişken tanımlanır: `val` (değiştirilemez) ve `var` (değiştirilebilir).

## Değişken Tanımlama
```kotlin
val sabitSayi: Int = 10 // Değeri değiştirilemez
var degistirilebilirSayi = 20 // Türü otomatik algılanır
```

## Temel Veri Tipleri
- `Int`: Tam sayı
- `Double`: Ondalıklı sayı
- `Boolean`: true/false
- `String`: Metin

```kotlin
val isim: String = "Ali"
val yas: Int = 25
val boy: Double = 1.75
val aktif: Boolean = true
```

## Notlar
- `val` ile tanımlanan değişkenin değeri sonradan değiştirilemez.
- `var` ile tanımlanan değişkenin değeri değiştirilebilir. 