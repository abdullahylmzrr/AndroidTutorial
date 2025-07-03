# 12. Animasyon ve Transition

Jetpack Compose'da animasyonlar, arayüzü daha canlı ve kullanıcı dostu yapmak için kullanılır.

## 12.1. animate*AsState Kullanımı
Bir değerin animasyonlu şekilde değişmesini sağlar.
```kotlin
import androidx.compose.animation.core.animateDpAsState

@Composable
fun AnimasyonluKutu() {
    var genis by remember { mutableStateOf(false) }
    val genislik by animateDpAsState(targetValue = if (genis) 200.dp else 100.dp)
    Box(
        modifier = Modifier
            .size(genislik)
            .background(Color.Blue)
            .clickable { genis = !genis }
    )
}
```

## 12.2. AnimatedVisibility
Bir composable'ın görünürlüğünü animasyonlu şekilde değiştirir.
```kotlin
import androidx.compose.animation.AnimatedVisibility

@Composable
fun GorunurAnimasyon() {
    var acik by remember { mutableStateOf(true) }
    Column {
        Button(onClick = { acik = !acik }) { Text("Gizle/Göster") }
        AnimatedVisibility(visible = acik) {
            Text("Animasyonlu Metin")
        }
    }
}
```

## 12.3. updateTransition
Birden fazla değeri aynı anda animasyonla değiştirmek için kullanılır.
```kotlin
import androidx.compose.animation.core.updateTransition
import androidx.compose.animation.core.tween

@Composable
fun RenkliAnimasyon() {
    var aktif by remember { mutableStateOf(false) }
    val transition = updateTransition(targetState = aktif, label = "renk")
    val renk by transition.animateColor(label = "renkAnim") { state ->
        if (state) Color.Green else Color.Red
    }
    Box(
        modifier = Modifier
            .size(100.dp)
            .background(renk)
            .clickable { aktif = !aktif }
    )
}
```

## Notlar
- Animasyonlar, kullanıcı deneyimini artırır.
- Basit animasyonlar için animate*AsState, daha karmaşıklar için updateTransition kullanılır. 