# 2. İnternetten ve Yerelden Resim Gösterme

Coil ile hem internetten hem de yerel (drawable) kaynaklardan kolayca resim gösterebilirsin.

## 2.1. İnternetten Resim Gösterme
```kotlin
import coil.compose.rememberAsyncImagePainter

@Composable
fun InternettenResim() {
    Image(
        painter = rememberAsyncImagePainter("https://picsum.photos/200"),
        contentDescription = null,
        modifier = Modifier.size(120.dp)
    )
}
```
- URL ile doğrudan resim yüklenir.

## 2.2. Yerelden (Drawable) Resim Gösterme
```kotlin
import androidx.compose.ui.res.painterResource

@Composable
fun YerelResim() {
    Image(
        painter = painterResource(id = R.drawable.ornek_resim),
        contentDescription = "Açıklama",
        modifier = Modifier.size(100.dp)
    )
}
```
- painterResource ile drawable klasöründeki resim gösterilir.

## 2.3. İç İçe Kullanım
Bir ekranda hem internetten hem yerelden resim gösterebilirsin.

```kotlin
@Composable
fun ResimOrnekleri() {
    Column {
        InternettenResim()
        Spacer(modifier = Modifier.height(16.dp))
        YerelResim()
    }
}
```

## Notlar
- Coil ile internetten resim yüklemek çok kolaydır.
- Yerel resimler için painterResource kullanılır. 