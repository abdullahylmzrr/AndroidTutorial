# 4. Image Transformation ve Caching

Coil ile resimlere efekt (dönüşüm) ekleyebilir ve önbellekleme (caching) işlemlerini kolayca yönetebilirsin.

## 4.1. Image Transformation (Efektler)
Coil'in transform parametresi ile resme efekt ekleyebilirsin.

```kotlin
import coil.transform.CircleCropTransformation
import coil.transform.RoundedCornersTransformation
import coil.compose.rememberAsyncImagePainter

@Composable
fun YuvarlakResim() {
    Image(
        painter = rememberAsyncImagePainter(
            model = "https://picsum.photos/200",
            transformations = listOf(CircleCropTransformation())
        ),
        contentDescription = null,
        modifier = Modifier.size(100.dp)
    )
}

@Composable
fun KoseYuvarlatmaOrnek() {
    Image(
        painter = rememberAsyncImagePainter(
            model = "https://picsum.photos/200",
            transformations = listOf(RoundedCornersTransformation(16f))
        ),
        contentDescription = null,
        modifier = Modifier.size(100.dp)
    )
}
```

## 4.2. Blur Efekti
```kotlin
import coil.transform.BlurTransformation

@Composable
fun BlurResim() {
    Image(
        painter = rememberAsyncImagePainter(
            model = "https://picsum.photos/200",
            transformations = listOf(BlurTransformation(context = LocalContext.current, radius = 10f))
        ),
        contentDescription = null,
        modifier = Modifier.size(100.dp)
    )
}
```

## 4.3. Caching (Önbellekleme)
- Coil, resimleri otomatik olarak disk ve bellek önbelleğinde saklar.
- Ekstra bir ayar yapmana gerek yoktur.

## Notlar
- Transformation ile resimlere kolayca efekt ekleyebilirsin.
- Caching, uygulamanın performansını artırır. 