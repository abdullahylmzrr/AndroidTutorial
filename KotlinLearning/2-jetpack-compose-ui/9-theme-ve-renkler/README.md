# 9. Theme ve Renkler

Jetpack Compose'da uygulamanın genel görünümünü ve renklerini tema ile yönetirsin. MaterialTheme, renk, tipografi ve şekil ayarlarını merkezi olarak sağlar.

## 9.1. MaterialTheme Kullanımı
```kotlin
@Composable
fun TemaliEkran() {
    MaterialTheme {
        Surface(color = MaterialTheme.colorScheme.background) {
            Text(
                text = "Tema ile Yazı",
                color = MaterialTheme.colorScheme.primary
            )
        }
    }
}
```
- `MaterialTheme.colorScheme.primary`: Temanın ana rengi.
- `Surface`: Arka plan rengi ve stil sağlar.

## 9.2. Renk Paleti Oluşturma
Renkleri merkezi olarak tanımlayabilirsin.
```kotlin
val Mavi = Color(0xFF2196F3)
val Kirmizi = Color(0xFFF44336)
```

## 9.3. Dark ve Light Theme
Karanlık ve aydınlık tema desteği ekleyebilirsin.
```kotlin
@Composable
fun UygulamaTemasi(darkTheme: Boolean = isSystemInDarkTheme(), content: @Composable () -> Unit) {
    val renkler = if (darkTheme) {
        darkColorScheme(primary = Mavi)
    } else {
        lightColorScheme(primary = Mavi)
    }
    MaterialTheme(
        colorScheme = renkler,
        content = content
    )
}
```

## Notlar
- Tema yönetimi, uygulamanın tutarlı ve profesyonel görünmesini sağlar.
- Renkleri ve stilleri merkezi olarak değiştirmek kolaydır. 