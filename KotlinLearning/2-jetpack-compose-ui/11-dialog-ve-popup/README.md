# 11. Dialog ve Popup

Jetpack Compose'da kullanıcıya bilgi vermek veya onay almak için Dialog ve Popup bileşenleri kullanılır.

## 11.1. AlertDialog Kullanımı
```kotlin
@Composable
fun DialogOrnek() {
    var acik by remember { mutableStateOf(false) }
    Column {
        Button(onClick = { acik = true }) {
            Text("Dialog Aç")
        }
        if (acik) {
            AlertDialog(
                onDismissRequest = { acik = false },
                title = { Text("Başlık") },
                text = { Text("Bu bir dialog örneğidir.") },
                confirmButton = {
                    Button(onClick = { acik = false }) {
                        Text("Tamam")
                    }
                },
                dismissButton = {
                    Button(onClick = { acik = false }) {
                        Text("İptal")
                    }
                }
            )
        }
    }
}
```

## 11.2. Custom Dialog
Kendi tasarımını oluşturmak için Dialog bileşeni kullanılabilir.
```kotlin
@Composable
fun CustomDialog(acik: Boolean, onDismiss: () -> Unit) {
    if (acik) {
        Dialog(onDismissRequest = onDismiss) {
            Box(
                modifier = Modifier
                    .size(200.dp)
                    .background(Color.White, shape = RoundedCornerShape(16.dp))
            ) {
                Text("Özel Dialog", modifier = Modifier.align(Alignment.Center))
            }
        }
    }
}
```

## Notlar
- Dialog ve Popup, kullanıcıdan onay almak veya bilgi göstermek için idealdir.
- Dialog'un açık/kapalı durumu state ile kontrol edilir. 