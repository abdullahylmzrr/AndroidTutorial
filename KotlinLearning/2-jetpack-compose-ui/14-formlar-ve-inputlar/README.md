# 14. Formlar ve Inputlar

Jetpack Compose'da kullanıcıdan veri almak için TextField ve OutlinedTextField gibi input bileşenleri kullanılır.

## 14.1. TextField Kullanımı
```kotlin
@Composable
fun BasitInput() {
    var metin by remember { mutableStateOf("") }
    TextField(
        value = metin,
        onValueChange = { metin = it },
        label = { Text("Adınızı girin") }
    )
}
```

## 14.2. OutlinedTextField
Daha modern ve çerçeveli bir input alanı sağlar.
```kotlin
@Composable
fun CizgiliInput() {
    var metin by remember { mutableStateOf("") }
    OutlinedTextField(
        value = metin,
        onValueChange = { metin = it },
        label = { Text("E-posta") }
    )
}
```

## 14.3. Form ve Doğrulama
Birden fazla input ile form oluşturabilir, state ile kontrol edebilirsin.
```kotlin
@Composable
fun GirisFormu() {
    var email by remember { mutableStateOf("") }
    var sifre by remember { mutableStateOf("") }
    var hata by remember { mutableStateOf("") }
    Column {
        OutlinedTextField(
            value = email,
            onValueChange = { email = it },
            label = { Text("E-posta") }
        )
        OutlinedTextField(
            value = sifre,
            onValueChange = { sifre = it },
            label = { Text("Şifre") },
            visualTransformation = PasswordVisualTransformation()
        )
        if (hata.isNotEmpty()) Text(hata, color = Color.Red)
        Button(onClick = {
            if (email.isEmpty() || sifre.isEmpty()) {
                hata = "Tüm alanları doldurun!"
            } else {
                hata = ""
                println("Giriş başarılı!")
            }
        }) {
            Text("Giriş Yap")
        }
    }
}
```

## Notlar
- Inputların değeri state ile kontrol edilir.
- Form doğrulama için state ve koşullu ifadeler kullanılır. 