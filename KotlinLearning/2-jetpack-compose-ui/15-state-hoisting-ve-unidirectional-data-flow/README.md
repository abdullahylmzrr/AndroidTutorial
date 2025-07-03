# 15. State Hoisting ve Unidirectional Data Flow

Jetpack Compose'da state hoisting, bir composable'ın state'ini üst composable'a taşıma işlemidir. Bu, veri akışının tek yönlü (unidirectional) olmasını sağlar.

## 15.1. State Hoisting Nedir?
- State, alt composable yerine üst composable'da tutulur.
- Alt composable, state'i ve güncelleme fonksiyonunu parametre olarak alır.

## 15.2. Neden Kullanılır?
- Tek yönlü veri akışı sağlar.
- Kodun test edilebilirliğini ve yeniden kullanılabilirliğini artırır.

## 15.3. Örnek
```kotlin
@Composable
fun AnaEkran() {
    var metin by remember { mutableStateOf("") }
    InputAlani(metin = metin, onMetinDegisti = { metin = it })
}

@Composable
fun InputAlani(metin: String, onMetinDegisti: (String) -> Unit) {
    TextField(
        value = metin,
        onValueChange = onMetinDegisti,
        label = { Text("Metin girin") }
    )
}
```

## 15.4. Unidirectional Data Flow
- Veri, üstten alta doğru akar.
- State ve güncelleme fonksiyonu, alt composable'a parametre olarak verilir.

## Notlar
- Büyük uygulamalarda state hoisting, veri yönetimini kolaylaştırır.
- Her zaman state'i mümkün olan en üst seviyede tutmak iyi bir pratiktir. 