# 4. ViewModel + Hilt Entegrasyonu

Bu bölümde, ViewModel ile veri yönetimini ve Hilt ile bağımlılık enjeksiyonunu öğreneceksin. Modern Android uygulamalarında veri ve bağımlılık yönetimi için bu ikili çok önemlidir.

## 4.1. ViewModel Nedir?
- Ekran (UI) ile veri arasındaki köprüdür.
- UI'dan bağımsız olarak veriyi saklar ve yönetir.
- Ekran döndüğünde (ör: telefon yatay- dikey) veri kaybolmaz.

### Basit ViewModel Örneği
```kotlin
import androidx.lifecycle.ViewModel
import kotlinx.coroutines.flow.MutableStateFlow
import kotlinx.coroutines.flow.StateFlow

class SayacViewModel : ViewModel() {
    private val _sayi = MutableStateFlow(0)
    val sayi: StateFlow<Int> = _sayi

    fun arttir() {
        _sayi.value++
    }
}
```

## 4.2. Hilt Nedir?
- Android için geliştirilmiş bir bağımlılık enjeksiyonu (Dependency Injection) kütüphanesidir.
- Sınıflar arası bağımlılıkları otomatik olarak yönetir.
- Kodun daha modüler ve test edilebilir olmasını sağlar.

### Hilt ile ViewModel Kullanımı

1. **build.gradle** dosyasına Hilt bağımlılıklarını ekle.
2. Uygulama sınıfını `@HiltAndroidApp` ile işaretle.
3. ViewModel'i `@HiltViewModel` ile işaretle ve constructor'a `@Inject` ekle.

```kotlin
import dagger.hilt.android.lifecycle.HiltViewModel
import javax.inject.Inject

@HiltViewModel
class OrnekViewModel @Inject constructor() : ViewModel() {
    // ViewModel içeriği
}
```

### Compose'da ViewModel Kullanımı
```kotlin
import androidx.hilt.navigation.compose.hiltViewModel

@Composable
fun OrnekEkran(viewModel: OrnekViewModel = hiltViewModel()) {
    // viewModel'den veri alıp kullanabilirsin
}
```

## 4.3. Notlar
- Hilt ile bağımlılıkları yönetmek, kodun okunabilirliğini ve test edilebilirliğini artırır.
- ViewModel, UI ile veri arasındaki en iyi köprüdür.

---

Bir sonraki adımda Coil ile resim göstermeyi öğreneceğiz. 