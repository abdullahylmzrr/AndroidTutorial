# 13. Object ve Singleton

Kotlin'de `object` anahtar kelimesi ile tekil (singleton) nesneler oluşturabilirsin. Ayrıca, object expression ve companion object gibi yapılar da vardır.

## 1. Singleton Object
Bir sınıfın tek bir örneği olması gerektiğinde kullanılır.
```kotlin
object Ayarlar {
    var tema = "Açık"
    fun goster() = println("Tema: $tema")
}

Ayarlar.tema = "Koyu"
Ayarlar.goster() // Tema: Koyu
```

## 2. Object Expression
Anonim (isimsiz) nesne oluşturmak için kullanılır.
```kotlin
val o = object {
    val x = 10
    fun yaz() = println(x)
}
o.yaz() // 10
```

## 3. Companion Object
Bir sınıfa ait, static benzeri üyeler tanımlamak için kullanılır.
```kotlin
class Kullanici {
    companion object {
        fun olustur(): Kullanici = Kullanici()
    }
}

val k = Kullanici.olustur()
```

## Notlar
- `object` ile oluşturulan nesne, uygulama boyunca tektir.
- `companion object`, Java'daki static üyelerin karşılığıdır. 