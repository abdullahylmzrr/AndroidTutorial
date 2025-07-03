# 12. Data Class

Data class'lar, veri tutmak için kullanılan özel sınıflardır. Otomatik olarak `toString`, `equals`, `hashCode` ve `copy` fonksiyonlarını sağlar.

## 1. Tanım ve Kullanım
```kotlin
data class Kullanici(val isim: String, val yas: Int)

val ali = Kullanici("Ali", 25)
println(ali) // Kullanici(isim=Ali, yas=25)
```

## 2. copy Fonksiyonu
Bir nesnenin kopyasını oluşturup bazı alanları değiştirebilirsin.
```kotlin
val ayse = ali.copy(isim = "Ayşe")
println(ayse) // Kullanici(isim=Ayşe, yas=25)
```

## 3. Otomatik Fonksiyonlar
- `toString()`: Nesneyi okunabilir şekilde yazdırır.
- `equals()`: İçerik karşılaştırması yapar.
- `hashCode()`: Hash kodu üretir.

## Notlar
- Data class'lar en az bir property (val/var) içermelidir.
- Genellikle model/veri taşımak için kullanılır. 