# 5. Döngüler

Döngüler, bir işlemi birden fazla kez tekrarlamak için kullanılır. Kotlin'de en çok kullanılan döngüler: `for`, `while` ve `do-while`.

## 1. for Döngüsü
Bir aralık veya koleksiyon üzerinde gezinmek için kullanılır.

```kotlin
for (i in 1..5) {
    println(i)
}
// 1, 2, 3, 4, 5 yazdırır

val isimler = listOf("Ali", "Ayşe", "Mehmet")
for (isim in isimler) {
    println(isim)
}
```

## 2. while Döngüsü
Koşul doğru olduğu sürece çalışır.

```kotlin
var sayac = 0
while (sayac < 3) {
    println("Sayaç: $sayac")
    sayac++
}
```

## 3. do-while Döngüsü
Koşul en az bir kez çalıştırılır, sonra kontrol edilir.

```kotlin
var x = 0
do {
    println("x: $x")
    x++
} while (x < 2)
```

## Notlar
- `break` ile döngüden çıkılır.
- `continue` ile döngünün bir sonraki adımına geçilir. 