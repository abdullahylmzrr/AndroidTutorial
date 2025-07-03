# 7. Null Safety (Null Güvenliği)

Kotlin'de null güvenliği, uygulamanın çökmesini önlemek için çok önemlidir. Java'daki "NullPointerException" hatalarını engellemek için tasarlanmıştır.

## 1. Nullable ve Non-nullable Tipler
- Varsayılan olarak bir değişken null olamaz:
```kotlin
var isim: String = "Ali"
isim = null // Hata verir!
```
- Null olabilen değişkenler `?` ile tanımlanır:
```kotlin
var isim: String? = "Ali"
isim = null // Sorun yok
```

## 2. Safe Call Operatörü `?.`
Bir değişken null ise işlemi atlar, değilse devam eder.
```kotlin
val uzunluk = isim?.length // isim null ise sonuç null olur
```

## 3. Elvis Operatörü `?:`
Null ise varsayılan bir değer döndürür.
```kotlin
val uzunluk = isim?.length ?: 0
```

## 4. Not-null Assertion `!!`
Değişkenin kesinlikle null olmadığını belirtir. Null ise hata fırlatır.
```kotlin
val uzunluk = isim!!.length // isim null ise uygulama çöker
```

## Notlar
- Mümkünse `!!` kullanmaktan kaçın.
- Null güvenliği, uygulamanın kararlı çalışması için çok önemlidir. 