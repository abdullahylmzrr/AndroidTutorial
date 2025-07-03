# 3. Text ve Button Bileşenleri

Jetpack Compose'da en sık kullanılan iki temel bileşen: Text ve Button.

## 3.1. Text Bileşeni
Ekrana yazı yazdırmak için kullanılır.

```kotlin
@Composable
fun BasitText() {
    Text(text = "Merhaba, Compose!")
}
```

### Text Özellikleri
- Yazı boyutu, rengi, fontu gibi özellikler Modifier ve style ile ayarlanır.

```kotlin
import androidx.compose.ui.text.font.FontWeight
import androidx.compose.ui.unit.sp
import androidx.compose.ui.graphics.Color

@Composable
fun StilliText() {
    Text(
        text = "Stilli Yazı",
        color = Color.Blue,
        fontSize = 24.sp,
        fontWeight = FontWeight.Bold
    )
}
```

## 3.2. Button Bileşeni
Kullanıcıdan etkileşim almak için kullanılır.

```kotlin
@Composable
fun BasitButton() {
    Button(onClick = { println("Butona tıklandı!") }) {
        Text("Tıkla Beni")
    }
}
```

### Button Özellikleri
- Renk, şekil, padding gibi özellikler Modifier ve parametrelerle ayarlanır.

```kotlin
import androidx.compose.foundation.shape.RoundedCornerShape
import androidx.compose.ui.unit.dp

@Composable
fun StilliButton() {
    Button(
        onClick = { /* işlem */ },
        shape = RoundedCornerShape(12.dp),
        modifier = Modifier.padding(8.dp)
    ) {
        Text("Stilli Buton")
    }
}
```

## 3.3. Birlikte Kullanım

```kotlin
@Composable
fun TextVeButtonOrnek() {
    Column {
        StilliText()
        Spacer(modifier = Modifier.height(16.dp))
        StilliButton()
    }
}
```

## Notlar
- Text ve Button, Compose'un en temel yapı taşlarıdır.
- Özelleştirme için Modifier ve style parametrelerini kullanabilirsin. 