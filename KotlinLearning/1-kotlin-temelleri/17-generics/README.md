# 17. Generics (Jenerik Tipler)

Generics, kodun farklı veri tipleriyle çalışmasını sağlar. Tek bir sınıf veya fonksiyon, farklı tiplerle güvenli şekilde kullanılabilir.

## 1. Generic Sınıf
```kotlin
class Kutu<T>(val icerik: T)

val intKutu = Kutu(5)
val stringKutu = Kutu("Merhaba")
println(intKutu.icerik) // 5
println(stringKutu.icerik) // Merhaba
```

## 2. Generic Fonksiyon
```kotlin
fun <T> yazdir(deger: T) {
    println(deger)
}

yazdir(10)
yazdir("Kotlin")
```

## 3. Neden Generics Kullanılır?
- Kod tekrarını azaltır.
- Tip güvenliğini artırır.

## Notlar
- Koleksiyonlar (List, Set, Map) da generic yapılar kullanır: `List<String>`, `Set<Int>` gibi. 