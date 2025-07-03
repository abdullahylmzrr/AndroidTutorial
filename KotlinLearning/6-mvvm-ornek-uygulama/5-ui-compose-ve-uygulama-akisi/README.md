# 5. UI (Compose) ve Uygulama Akışı

MVVM'de UI katmanı, ViewModel'den veri alır ve kullanıcıya gösterir. Jetpack Compose ile modern ve dinamik arayüzler oluşturabilirsin.

## 5.1. ViewModel'den Veri Çekme
```kotlin
@Composable
fun KullaniciListesi(viewModel: KullaniciViewModel = hiltViewModel()) {
    val kullanicilar by viewModel.kullanicilar.collectAsState()
    LazyColumn {
        items(kullanicilar) { kullanici ->
            KullaniciSatiri(kullanici)
        }
    }
}
```

## 5.2. Liste Elemanı (Row) Tasarımı
```kotlin
@Composable
fun KullaniciSatiri(kullanici: Kullanici) {
    Row(modifier = Modifier.padding(8.dp)) {
        Image(
            painter = rememberAsyncImagePainter(kullanici.avatarUrl),
            contentDescription = null,
            modifier = Modifier.size(48.dp)
        )
        Spacer(modifier = Modifier.width(8.dp))
        Text(kullanici.isim, fontWeight = FontWeight.Bold)
    }
}
```

## 5.3. Uygulama Akışı
- Kullanıcı uygulamayı açar.
- ViewModel, repository'den veri çeker.
- UI, ViewModel'den gelen veriyi gösterir.

## Notlar
- UI, sadece ViewModel'den veri alır ve gösterir.
- Compose ile modern ve performanslı arayüzler oluşturabilirsin. 