# 13. Custom Composable (Özel Bileşen)

Jetpack Compose'da kendi özel composable bileşenlerini oluşturabilirsin. Bu, kodun tekrarını azaltır ve okunabilirliği artırır.

## 13.1. Basit Custom Composable
```kotlin
@Composable
fun BaslikYazi(metin: String) {
    Text(
        text = metin,
        fontSize = 24.sp,
        fontWeight = FontWeight.Bold
    )
}

@Composable
fun OrnekEkran() {
    Column {
        BaslikYazi("Hoş Geldin!")
        BaslikYazi("Jetpack Compose Öğreniyoruz")
    }
}
```

## 13.2. Parametreli ve Özelleştirilebilir Bileşen
```kotlin
@Composable
fun RenkliButon(
    metin: String,
    renk: Color = Color.Blue,
    onTikla: () -> Unit
) {
    Button(
        onClick = onTikla,
        colors = ButtonDefaults.buttonColors(containerColor = renk)
    ) {
        Text(metin)
    }
}

@Composable
fun OrnekKullanim() {
    RenkliButon(metin = "Kaydet", renk = Color.Green) {
        println("Kaydet tıklandı")
    }
}
```

## Notlar
- Custom composable'lar, büyük projelerde kodun düzenli ve sürdürülebilir olmasını sağlar.
- Parametrelerle esnek ve tekrar kullanılabilir bileşenler yazabilirsin. 