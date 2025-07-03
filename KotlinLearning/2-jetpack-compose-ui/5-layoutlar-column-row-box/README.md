# 5. Layoutlar: Column, Row, Box

Jetpack Compose'da arayüzdeki bileşenleri düzenlemek için layout bileşenleri kullanılır. En temel layoutlar: Column, Row ve Box.

## 5.1. Column
Bileşenleri dikey olarak alt alta dizer.

```kotlin
@Composable
fun DikeyDizilim() {
    Column {
        Text("Birinci Satır")
        Text("İkinci Satır")
        Button(onClick = {}) { Text("Buton") }
    }
}
```

### Column Özellikleri
- `verticalArrangement`: Dikeyde hizalama
- `horizontalAlignment`: Yatayda hizalama

```kotlin
Column(
    verticalArrangement = Arrangement.SpaceBetween,
    horizontalAlignment = Alignment.CenterHorizontally,
    modifier = Modifier.fillMaxHeight()
) {
    // ...
}
```

## 5.2. Row
Bileşenleri yatay olarak yan yana dizer.

```kotlin
@Composable
fun YatayDizilim() {
    Row {
        Text("Sol")
        Spacer(modifier = Modifier.width(16.dp))
        Text("Sağ")
    }
}
```

### Row Özellikleri
- `horizontalArrangement`: Yatayda hizalama
- `verticalAlignment`: Dikeyde hizalama

## 5.3. Box
Bileşenleri üst üste veya köşelere yerleştirmek için kullanılır.

```kotlin
@Composable
fun UstUsteBilesenler() {
    Box(modifier = Modifier.size(100.dp)) {
        Text("Altta", modifier = Modifier.align(Alignment.BottomEnd))
        Text("Üstte", modifier = Modifier.align(Alignment.TopStart))
    }
}
```

## Notlar
- Layoutlar, arayüzün düzenini ve hizalamasını kontrol eder.
- Modifier ile boyut, padding, hizalama gibi özellikler eklenebilir. 