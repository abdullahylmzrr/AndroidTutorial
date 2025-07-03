# 5. Repository ve ViewModel'de Kullanım

Repository, veri kaynaklarını (API, veritabanı, cache) ViewModel'den ayıran katmandır. Hilt ile kolayca inject edilir.

## 5.1. Repository Tanımı
```kotlin
class KullaniciRepository @Inject constructor(private val api: ApiService) {
    suspend fun kullanicilariGetir() = api.kullanicilariGetir()
}
```

## 5.2. ViewModel'de Repository Kullanımı
```kotlin
@HiltViewModel
class KullaniciViewModel @Inject constructor(
    private val repo: KullaniciRepository
) : ViewModel() {
    var kullanicilar by mutableStateOf<List<Kullanici>>(emptyList())
        private set
    init {
        veriYukle()
    }
    private fun veriYukle() {
        viewModelScope.launch {
            kullanicilar = repo.kullanicilariGetir()
        }
    }
}
```

## 5.3. Compose'da Kullanım
```kotlin
@Composable
fun KullaniciListesi(viewModel: KullaniciViewModel = hiltViewModel()) {
    LazyColumn {
        items(viewModel.kullanicilar) { kullanici ->
            Text(kullanici.isim)
        }
    }
}
```

## Notlar
- Repository, veri yönetimini merkezi hale getirir.
- Hilt ile bağımlılıklar otomatik olarak ViewModel'e aktarılır. 