# 6. Katmanlar Arası Entegrasyon Akışı

Clean Architecture'da veri ve iş akışı katmanlar arasında aşağıdaki gibi ilerler:

## 6.1. Akış Şeması
1. **UI (Compose/Fragment)** → ViewModel
2. **ViewModel** → UseCase
3. **UseCase** → Repository
4. **Repository** → Room DAO ve/veya API Service
5. **WorkManager** → UseCase/Repository (arka planda)

## 6.2. Örnek Akış
```kotlin
// UI
val kullanicilar by viewModel.kullanicilar.collectAsState()

// ViewModel
class KullaniciViewModel @Inject constructor(private val getKullanicilar: GetKullanicilarUseCase) : ViewModel() {
    val kullanicilar = MutableStateFlow<List<KullaniciEntity>>(emptyList())
    fun yukle() { viewModelScope.launch { kullanicilar.value = getKullanicilar() } }
}

// UseCase
class GetKullanicilarUseCase @Inject constructor(private val repo: KullaniciRepository) {
    suspend operator fun invoke() = repo.kullanicilariGetir()
}

// Repository
class KullaniciRepository @Inject constructor(private val dao: KullaniciDao) {
    suspend fun kullanicilariGetir() = dao.tumKullanicilar()
}
```

## 6.3. WorkManager ile Entegrasyon
- WorkManager, UseCase veya Repository'yi arka planda çağırabilir.

## Notlar
- Katmanlar arası bağımlılık akışı tek yönlüdür.
- Her katman sadece bir alt katmana bağımlıdır. 