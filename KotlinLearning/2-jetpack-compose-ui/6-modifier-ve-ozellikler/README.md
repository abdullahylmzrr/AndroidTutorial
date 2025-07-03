# 6. Modifier ve Özellikler

Modifier, Compose'da bir bileşenin görünümünü ve davranışını değiştirmek için kullanılır. Her bileşene zincirleme şekilde eklenebilir.

## 6.1. Padding ve Margin
```kotlin
@Composable
fun PaddingOrnek() {
    Text(
        text = "Paddingli Yazı",
        modifier = Modifier.padding(16.dp)
    )
}
```

## 6.2. Boyutlandırma
```kotlin
@Composable
fun BoyutOrnek() {
    Box(
        modifier = Modifier
            .width(120.dp)
            .height(60.dp)
    ) {
        Text("Boyutlu Kutu")
    }
}
```

## 6.3. Arka Plan ve Renk
```kotlin
import androidx.compose.ui.graphics.Color

@Composable
fun ArkaPlanOrnek() {
    Text(
        text = "Renkli Yazı",
        modifier = Modifier.background(Color.Yellow)
    )
}
```

## 6.4. Tıklama Olayı
```kotlin
@Composable
fun TiklanabilirOrnek() {
    Text(
        text = "Tıkla Beni",
        modifier = Modifier.clickable { println("Tıklandı!") }
    )
}
```

## 6.5. Zincirleme Kullanım
Modifier'lar birleştirilerek daha karmaşık stiller oluşturulabilir.

```kotlin
@Composable
fun ZincirOrnek() {
    Text(
        text = "Zincirli Modifier",
        modifier = Modifier
            .padding(8.dp)
            .background(Color.LightGray)
            .clickable { }
    )
}
```

## Notlar
- Modifier, Compose'da stil ve davranış eklemenin ana yoludur.
- Her bileşene birden fazla modifier eklenebilir. 