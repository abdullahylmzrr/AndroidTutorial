# 2. Jetpack Compose ile UI

Bu bölümde, Android'de modern arayüzler oluşturmak için kullanılan Jetpack Compose'u öğreneceksin. XML yerine tamamen Kotlin ile arayüz tasarlayacağız.

## 2.1. Jetpack Compose Nedir?
- Android için modern, deklaratif bir UI araç takımıdır.
- XML yerine doğrudan Kotlin kodu ile arayüz oluşturulur.
- Daha az kod, daha kolay okunabilirlik ve bakım sağlar.

## 2.2. Temel Kavramlar
- **Composable Fonksiyonlar:** `@Composable` ile işaretlenen fonksiyonlar, ekranda bir şeyler çizer.
- **State (Durum):** UI'ın güncel kalmasını sağlar.

## 2.3. Basit Bir Örnek

```kotlin
import androidx.compose.material3.*
import androidx.compose.runtime.*
import androidx.compose.ui.tooling.preview.Preview

@Composable
fun MerhabaDunya() {
    Text(text = "Merhaba, Jetpack Compose!")
}

@Preview
@Composable
fun Onizleme() {
    MerhabaDunya()
}
```

## 2.4. Buton ve State Kullanımı

```kotlin
@Composable
fun Sayac() {
    var sayi by remember { mutableStateOf(0) }
    Button(onClick = { sayi++ }) {
        Text("Tıkla: $sayi")
    }
}
```
- `remember` ve `mutableStateOf`: Değişkenin UI ile birlikte güncel kalmasını sağlar.

## 2.5. Layout (Yerleşim) Örnekleri

```kotlin
import androidx.compose.foundation.layout.*
import androidx.compose.ui.Modifier
import androidx.compose.ui.unit.dp

@Composable
fun DikeyDizilim() {
    Column(modifier = Modifier.padding(16.dp)) {
        Text("Başlık")
        Sayac()
    }
}
```

---

Bir sonraki adımda, uygulamaya veri çekmeyi (Retrofit ile) ekleyeceğiz. 