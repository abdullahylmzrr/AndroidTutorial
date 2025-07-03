# 16. Efektler ve Gesture

Jetpack Compose'da efektler, composable'ın yaşam döngüsüne bağlı yan etkiler oluşturmak için kullanılır. Gesture ise kullanıcı etkileşimlerini (tıklama, sürükleme, uzun basma) yönetir.

## 16.1. LaunchedEffect
Composable ilk oluşturulduğunda veya belirli bir anahtar değiştiğinde çalışır.
```kotlin
@Composable
fun LaunchedEffectOrnek() {
    var sayi by remember { mutableStateOf(0) }
    LaunchedEffect(sayi) {
        println("Sayı değişti: $sayi")
    }
    Button(onClick = { sayi++ }) { Text("Arttır") }
}
```

## 16.2. SideEffect ve DisposableEffect
- `SideEffect`: Her recomposition sonrası çalışır.
- `DisposableEffect`: Composable kaldırıldığında temizlik işlemleri için kullanılır.

```kotlin
@Composable
fun SideEffectOrnek() {
    SideEffect { println("Her recomposition sonrası çalışır") }
}

@Composable
fun DisposableEffectOrnek() {
    DisposableEffect(Unit) {
        println("Başladı")
        onDispose { println("Bitti") }
    }
}
```

## 16.3. Gesture Kullanımı
- Tıklama, uzun basma, sürükleme gibi etkileşimler Modifier ile eklenir.

```kotlin
@Composable
fun GestureOrnek() {
    Box(
        modifier = Modifier
            .size(100.dp)
            .background(Color.Gray)
            .pointerInput(Unit) {
                detectTapGestures(
                    onLongPress = { println("Uzun basıldı") },
                    onTap = { println("Tıklandı") }
                )
            }
    )
}
```

## Notlar
- Efektler, yan etkili işlemler için kullanılır (ör: veri çekme, log).
- Gesture ile kullanıcı etkileşimleri kolayca yönetilir. 