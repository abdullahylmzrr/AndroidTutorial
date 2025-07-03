# 18. Koleksiyon Fonksiyonları

Kotlin'de koleksiyonlar üzerinde işlem yapmak için birçok fonksiyon bulunur. Bunlar kodu daha kısa ve okunabilir yapar.

## 1. filter
Belirli bir koşula uyan elemanları seçer.
```kotlin
val sayilar = listOf(1, 2, 3, 4, 5)
val ciftler = sayilar.filter { it % 2 == 0 }
println(ciftler) // [2, 4]
```

## 2. map
Her elemanı dönüştürür.
```kotlin
val kareler = sayilar.map { it * it }
println(kareler) // [1, 4, 9, 16, 25]
```

## 3. forEach
Her eleman için işlem yapar.
```kotlin
sayilar.forEach { println(it) }
```

## 4. find
İlk eşleşen elemanı bulur.
```kotlin
val uc = sayilar.find { it == 3 }
println(uc) // 3
```

## 5. any & all
- `any`: En az bir eleman koşulu sağlıyorsa true döner.
- `all`: Tüm elemanlar koşulu sağlıyorsa true döner.
```kotlin
println(sayilar.any { it > 4 }) // true
println(sayilar.all { it > 0 }) // true
```

## 6. groupBy
Elemanları gruplar.
```kotlin
val isimler = listOf("Ali", "Ayşe", "Mehmet", "Ahmet")
val gruplar = isimler.groupBy { it.first() }
println(gruplar) // {A=[Ali, Ayşe, Ahmet], M=[Mehmet]}
```

## 7. sortedBy
Belirli bir kritere göre sıralar.
```kotlin
val sirali = isimler.sortedBy { it.length }
println(sirali) // [Ali, Ayşe, Ahmet, Mehmet]
```

## Notlar
- Koleksiyon fonksiyonları zincirleme (chaining) ile birlikte kullanılabilir. 