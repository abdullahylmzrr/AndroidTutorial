# 3. Placeholder, Hata ve Animasyon

Coil ile resim yüklenirken placeholder, hata durumunda error resmi ve animasyon ekleyebilirsin.

## 3.1. Placeholder (Yükleniyor Resmi)
```kotlin
@Composable
fun PlaceholderOrnek() {
    Image(
        painter = rememberAsyncImagePainter(
            model = "https://picsum.photos/200",
            placeholder = painterResource(R.drawable.placeholder)
        ),
        contentDescription = null,
        modifier = Modifier.size(120.dp)
    )
}
```

## 3.2. Hata Resmi
```kotlin
@Composable
fun HataOrnek() {
    Image(
        painter = rememberAsyncImagePainter(
            model = "https://hataliresim.com/404.jpg",
            error = painterResource(R.drawable.error)
        ),
        contentDescription = null,
        modifier = Modifier.size(120.dp)
    )
}
```

## 3.3. Yükleme Animasyonu
Coil ile animasyon için crossfade kullanılabilir.
```kotlin
@Composable
fun AnimasyonOrnek() {
    Image(
        painter = rememberAsyncImagePainter(
            model = "https://picsum.photos/200",
            placeholder = painterResource(R.drawable.placeholder),
            error = painterResource(R.drawable.error),
            // crossfade parametresi ile animasyon
            // (Coil 2.x ile crossfade default açık)
        ),
        contentDescription = null,
        modifier = Modifier.size(120.dp)
    )
}
```

## Notlar
- Placeholder ve hata resmi için painterResource kullanılır.
- Animasyon için crossfade parametresi eklenebilir. 