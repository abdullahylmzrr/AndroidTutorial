# 14. Extension Fonksiyonlar

Extension fonksiyonlar, mevcut bir sınıfa yeni fonksiyonlar eklemeni sağlar. Sınıfın orijinal kodunu değiştirmeden yeni işlevler kazandırabilirsin.

## 1. Tanım ve Kullanım
```kotlin
fun String.tersCevir(): String {
    return this.reversed()
}

val kelime = "Kotlin"
println(kelime.tersCevir()) // niltoK
```

## 2. Koleksiyonlara Extension
```kotlin
fun List<Int>.toplam(): Int {
    var toplam = 0
    for (sayi in this) toplam += sayi
    return toplam
}

val sayilar = listOf(1, 2, 3)
println(sayilar.toplam()) // 6
```

## Notlar
- Extension fonksiyonlar, kodun okunabilirliğini ve tekrar kullanılabilirliğini artırır.
- Sınıfın orijinalini değiştirmez, sadece yeni fonksiyon ekler. 