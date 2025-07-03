# 5. Coil ile Resim Gösterme

Bu bölümde, Android uygulamasında internetten veya yerelden resim göstermek için kullanılan Coil kütüphanesini öğreneceksin. Jetpack Compose ile birlikte çok kolay kullanılır.

## 5.1. Coil Nedir?
- Android için modern, hızlı ve hafif bir resim yükleme kütüphanesidir.
- Jetpack Compose ile tam uyumludur.

## 5.2. Temel Kullanım
- build.gradle dosyasına Coil Compose bağımlılığını ekle:
  ```gradle
  implementation "io.coil-kt:coil-compose:2.4.0"
  ```

## 5.3. Basit Kullanım Örneği
```kotlin
import androidx.compose.foundation.Image
import androidx.compose.runtime.Composable
import coil.compose.rememberAsyncImagePainter
import androidx.compose.ui.Modifier
import androidx.compose.ui.layout.ContentScale

@Composable
fun ResimGoster(url: String) {
    Image(
        painter = rememberAsyncImagePainter(url),
        contentDescription = null,
        modifier = Modifier,
        contentScale = ContentScale.Crop
    )
}
```

## 5.4. Notlar
- `rememberAsyncImagePainter` ile internetten veya yerelden resim kolayca yüklenir.
- `contentScale` ile resmin nasıl ölçekleneceğini ayarlayabilirsin.

---

Bir sonraki adımda, öğrendiğimiz her şeyi birleştirerek tam bir MVVM uygulaması yazacağız. 