# 4. ViewModel ve State Yönetimi

MVVM'de ViewModel, UI ile veri arasındaki köprüdür ve state yönetimini sağlar.

## 4.1. ViewModel'de Repository Kullanımı
```kotlin
@HiltViewModel
class KullaniciViewModel @Inject constructor(
    private val repo: KullaniciRepository
) : ViewModel() {
    private val _kullanicilar = MutableStateFlow<List<Kullanici>>(emptyList())
    val kullanicilar: StateFlow<List<Kullanici>> = _kullanicilar

    init { veriYukle() }

    private fun veriYukle() {
        viewModelScope.launch {
            _kullanicilar.value = repo.kullanicilariGetir()
        }
    }
}
```

## 4.2. StateFlow ile Veri Akışı
- StateFlow, Compose ile uyumlu, güncel veri akışı sağlar.
- UI, StateFlow'u observe ederek otomatik güncellenir.

## Notlar
- ViewModel, veri yönetimini ve iş mantığını UI'dan ayırır.
- StateFlow, modern ve performanslı state yönetimi sunar. 