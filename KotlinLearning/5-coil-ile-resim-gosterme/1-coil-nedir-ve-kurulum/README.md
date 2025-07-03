# 1. Coil Nedir ve Kurulum

Coil, Android için modern, hızlı ve hafif bir resim yükleme kütüphanesidir. Jetpack Compose ile tam uyumludur.

## 1.1. Coil Nedir?
- İnternetten veya yerelden resim yüklemeyi kolaylaştırır.
- Hafif ve hızlıdır.
- Compose ile doğrudan kullanılabilir.

## 1.2. Avantajları
- Modern ve Kotlin tabanlı
- Düşük bellek kullanımı
- Animasyon, önbellekleme ve hata yönetimi desteği

## 1.3. Projeye Coil Ekleme
build.gradle dosyana aşağıdaki satırı ekle:

```gradle
dependencies {
    implementation "io.coil-kt:coil-compose:2.4.0"
}
```

## 1.4. Temel Kurulum ve Kullanım
```kotlin
import coil.compose.rememberAsyncImagePainter

@Composable
fun ResimGoster(url: String) {
    Image(
        painter = rememberAsyncImagePainter(url),
        contentDescription = null,
        modifier = Modifier.size(120.dp)
    )
}
```

## Notlar
- Coil, Compose ile resim yüklemenin en kolay yoludur.
- Daha fazla bilgi: [Coil Dokümantasyonu](https://coil-kt.github.io/coil/compose/) 