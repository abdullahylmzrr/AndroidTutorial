# 8. Koleksiyonlar

Koleksiyonlar, birden fazla veriyi bir arada tutmak için kullanılır. Kotlin'de en yaygın koleksiyon türleri: List, Set ve Map.

## 1. List
Sıralı ve tekrarlı elemanlar tutar.
```kotlin
val sayilar = listOf(1, 2, 3) // Değiştirilemez (immutable)
val isimler = mutableListOf("Ali", "Ayşe") // Değiştirilebilir (mutable)

isimler.add("Mehmet")
println(isimler) // [Ali, Ayşe, Mehmet]
```

## 2. Set
Tekrarsız elemanlar tutar.
```kotlin
val harfler = setOf('a', 'b', 'c', 'a')
println(harfler) // [a, b, c]
```

## 3. Map
Anahtar-değer (key-value) çiftleri tutar.
```kotlin
val notlar = mapOf("Ali" to 90, "Ayşe" to 85)
println(notlar["Ali"]) // 90

val mutableNotlar = mutableMapOf<String, Int>()
mutableNotlar["Mehmet"] = 70
```

## Notlar
- `listOf`, `setOf`, `mapOf`: Değiştirilemez koleksiyonlar.
- `mutableListOf`, `mutableSetOf`, `mutableMapOf`: Değiştirilebilir koleksiyonlar. 