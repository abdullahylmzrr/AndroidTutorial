# 8. Görsel Bileşenler: Image ve Icon

Jetpack Compose'da görsel göstermek için Image ve Icon bileşenleri kullanılır.

## 8.1. Image ile Yerel Resim Gösterme
```kotlin
@Composable
fun YerelResimOrnek() {
    Image(
        painter = painterResource(id = R.drawable.ornek_resim),
        contentDescription = "Açıklama",
        modifier = Modifier.size(100.dp),
        contentScale = ContentScale.Crop
    )
}
```
- `painterResource`: drawable klasöründeki resmi yükler.
- `contentDescription`: Erişilebilirlik için açıklama.
- `contentScale`: Resmin nasıl ölçekleneceğini belirler.

## 8.2. İnternetten Resim Gösterme (Coil ile)
```kotlin
import coil.compose.rememberAsyncImagePainter

@Composable
fun InternetResimOrnek() {
    Image(
        painter = rememberAsyncImagePainter("https://picsum.photos/200"),
        contentDescription = null,
        modifier = Modifier.size(120.dp),
        contentScale = ContentScale.Crop
    )
}
```

## 8.3. Icon Kullanımı
```kotlin
import androidx.compose.material.icons.Icons
import androidx.compose.material.icons.filled.Favorite

@Composable
fun IconOrnek() {
    Icon(
        imageVector = Icons.Filled.Favorite,
        contentDescription = "Favori",
        tint = Color.Red
    )
}
```

## Notlar
- Görsellerin boyutu ve hizalaması Modifier ile ayarlanır.
- İnternetten resim göstermek için Coil kütüphanesi kullanılır. 