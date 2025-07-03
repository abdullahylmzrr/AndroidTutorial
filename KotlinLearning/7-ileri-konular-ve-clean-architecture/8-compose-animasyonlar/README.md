# 8. Compose Animasyonlar

Jetpack Compose, modern ve kolay animasyon API'leri sunar. UI'ya canlılık ve etkileşim katmak için animasyonları kullanabilirsin.

## 8.1. animate*AsState ile Temel Animasyon
Bir değerin animasyonlu şekilde değişmesini sağlar.
```kotlin
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

## 8.2. AnimatedVisibility ile Görünürlük Animasyonu
Bir composable'ın görünürlüğünü animasyonlu şekilde değiştirir.
```kotlin
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

## 8.3. updateTransition ile Çoklu Animasyon
Birden fazla değeri aynı anda animasyonla değiştirmek için kullanılır.
```kotlin
@Composable
fun RenkliAnimasyon() {
    var aktif by remember { mutableStateOf(false) }
    val transition = updateTransition(targetState = aktif, label = "renk")
    val renk by transition.animateColor(label = "renkAnim") { state ->
        if (state) Color.Green else Color.Red
    }
    val boyut by transition.animateDp(label = "boyutAnim") { state ->
        if (state) 150.dp else 80.dp
    }
    Box(
        modifier = Modifier
            .size(boyut)
            .background(renk)
            .clickable { aktif = !aktif }
    )
}
```

## 8.4. Gesture ile Animasyon
Kullanıcı etkileşimiyle animasyon başlatmak için gesture kullanabilirsin.
```kotlin
@Composable
fun SürükleAnimasyon() {
    var offsetX by remember { mutableStateOf(0f) }
    Box(
        modifier = Modifier
            .offset { IntOffset(offsetX.roundToInt(), 0) }
            .size(80.dp)
            .background(Color.Magenta)
            .pointerInput(Unit) {
                detectDragGestures { change, dragAmount ->
                    offsetX += dragAmount.x
                }
            }
    )
}
```

## 8.5. Diğer Animasyon API'leri
- animateColorAsState, animateFloatAsState, animateIntAsState, vb.
- Crossfade, InfiniteTransition, Animatable

## Notlar
- Animasyonlar, kullanıcı deneyimini artırır.
- Basit animasyonlar için animate*AsState, daha karmaşıklar için updateTransition kullanılır.
- Gesture ile animasyonları birleştirerek etkileşimli UI'lar oluşturabilirsin. 