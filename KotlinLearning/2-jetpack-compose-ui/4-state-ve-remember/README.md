# 4. State ve remember

Jetpack Compose'da arayüzün güncel kalması için state (durum) yönetimi çok önemlidir.

## 4.1. State Nedir?
Bir değişkenin değerinin değişmesiyle UI'ın otomatik olarak güncellenmesini sağlar.

## 4.2. remember ve mutableStateOf
- `remember`: Değişkenin Compose ömrü boyunca saklanmasını sağlar.
- `mutableStateOf`: Değişkenin değiştiğinde UI'ı günceller.

```kotlin
import androidx.compose.runtime.*

@Composable
fun Sayac() {
    var sayi by remember { mutableStateOf(0) }
    Column {
        Text("Sayaç: $sayi")
        Button(onClick = { sayi++ }) {
            Text("Arttır")
        }
    }
}
```

## 4.3. State Güncelleme
- State değiştiğinde ilgili composable otomatik olarak yeniden çizilir.

## 4.4. State Kapsamı
- State'i mümkün olduğunca küçük tutmak kodun okunabilirliğini artırır.

## Notlar
- State yönetimi, Compose'un en güçlü özelliklerinden biridir.
- State değiştikçe sadece ilgili composable yeniden çizilir. 