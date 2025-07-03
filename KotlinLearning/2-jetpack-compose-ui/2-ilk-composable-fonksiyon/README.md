# 2. İlk Composable Fonksiyon

Jetpack Compose'da arayüzü oluşturan temel yapı taşları composable fonksiyonlardır. Her composable fonksiyon, ekranda bir şey çizer.

## 2.1. @Composable Anotasyonu
Bir fonksiyonun ekrana bir şey çizebilmesi için başına `@Composable` eklenir.

```kotlin
@Composable
fun MerhabaDunya() {
    Text(text = "Merhaba, Compose!")
}
```
- `Text`: Ekrana yazı yazdırır.
- `text` parametresiyle gösterilecek metni belirleriz.

## 2.2. Button ile Etkileşim
Kullanıcıdan etkileşim almak için `Button` kullanılır.

```kotlin
@Composable
fun SelamButonu() {
    Button(onClick = { println("Butona tıklandı!") }) {
        Text("Tıkla Beni")
    }
}
```
- `onClick`: Butona tıklanınca çalışacak kod bloğu.

## 2.3. Birden Fazla Composable Kullanmak
Birden fazla composable fonksiyonu bir arada kullanabilirsin.

```kotlin
@Composable
fun SelamEkrani() {
    Column {
        MerhabaDunya()
        SelamButonu()
    }
}
```
- `Column`: Alt alta sıralama yapar.

## 2.4. Preview ile Önizleme
Android Studio'da kodunu hızlıca görebilmek için `@Preview` anotasyonu kullanılır.

```kotlin
@Preview(showBackground = true)
@Composable
fun Onizleme() {
    SelamEkrani()
}
```
- `showBackground = true`: Arka planı gösterir.

## Notlar
- Composable fonksiyonlar, küçük ve tekrar kullanılabilir olmalıdır.
- Her UI parçası için ayrı bir composable fonksiyon yazmak kodun okunabilirliğini artırır. 