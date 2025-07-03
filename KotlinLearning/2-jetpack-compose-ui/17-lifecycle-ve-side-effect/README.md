# 17. Lifecycle ve Side Effect

Jetpack Compose'da composable'ların yaşam döngüsü ve yan etkilerin (side effect) doğru yönetilmesi önemlidir.

## 17.1. Composable Yaşam Döngüsü
- Composable fonksiyonlar, state değiştikçe yeniden çalışır (recomposition).
- Composable kaldırıldığında temizlik işlemleri yapılabilir.

## 17.2. Side Effect Yönetimi
- Yan etkiler, composable'ın dışında gerçekleşen işlemlerdir (ör: veri çekme, log, navigation).
- `LaunchedEffect`, `SideEffect`, `DisposableEffect` ile yönetilir.

```kotlin
@Composable
fun VeriCekmeOrnek() {
    var veri by remember { mutableStateOf("") }
    LaunchedEffect(Unit) {
        // Burada ağdan veri çekebilirsin
        veri = "Veri geldi!"
    }
    Text(veri)
}

@Composable
fun TemizlikOrnek() {
    DisposableEffect(Unit) {
        println("Başladı")
        onDispose { println("Bitti") }
    }
}
```

## 17.3. LifecycleOwner ile Entegrasyon
- Compose dışı lifecycle olaylarını dinlemek için `LocalLifecycleOwner` kullanılabilir.

```kotlin
import androidx.lifecycle.Lifecycle
import androidx.lifecycle.LifecycleEventObserver
import androidx.compose.runtime.getValue
import androidx.compose.runtime.setValue

@Composable
fun LifecycleOrnek() {
    val lifecycleOwner = LocalLifecycleOwner.current
    DisposableEffect(lifecycleOwner) {
        val observer = LifecycleEventObserver { _, event ->
            if (event == Lifecycle.Event.ON_START) {
                println("Başladı!")
            }
        }
        lifecycleOwner.lifecycle.addObserver(observer)
        onDispose { lifecycleOwner.lifecycle.removeObserver(observer) }
    }
}
```

## Notlar
- Yan etkiler, doğru zamanda başlatılmalı ve temizlenmelidir.
- Lifecycle yönetimi, Compose ve klasik Android kodlarının birlikte çalışmasını kolaylaştırır. 