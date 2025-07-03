# 2. StateFlow, LiveData ve State Yönetimi

ViewModel'de state yönetimi için StateFlow ve LiveData en çok kullanılan yapılardır.

## 2.1. StateFlow ile State Yönetimi
- StateFlow, Kotlin Flow'un state tutan özel bir versiyonudur.
- Compose ile doğrudan uyumludur.

```kotlin
import kotlinx.coroutines.flow.MutableStateFlow
import kotlinx.coroutines.flow.StateFlow
import androidx.lifecycle.ViewModel

class SayacViewModel : ViewModel() {
    private val _sayi = MutableStateFlow(0)
    val sayi: StateFlow<Int> = _sayi
    fun arttir() { _sayi.value++ }
}
```

### Compose'da StateFlow Kullanımı
```kotlin
@Composable
fun SayacEkrani(viewModel: SayacViewModel = viewModel()) {
    val sayi by viewModel.sayi.collectAsState()
    Column {
        Text("Sayaç: $sayi")
        Button(onClick = { viewModel.arttir() }) { Text("Arttır") }
    }
}
```

## 2.2. LiveData ile State Yönetimi
- LiveData, eski projelerde yaygın olarak kullanılır.
- Compose ile observeAsState ile kullanılır.

```kotlin
import androidx.lifecycle.LiveData
import androidx.lifecycle.MutableLiveData

class OrnekViewModel : ViewModel() {
    private val _metin = MutableLiveData("")
    val metin: LiveData<String> = _metin
    fun guncelle(yeni: String) { _metin.value = yeni }
}
```

### Compose'da LiveData Kullanımı
```kotlin
@Composable
fun MetinEkrani(viewModel: OrnekViewModel = viewModel()) {
    val metin by viewModel.metin.observeAsState("")
    Text(metin)
}
```

## 2.3. Farklar ve Notlar
- StateFlow daha modern ve Compose ile daha uyumludur.
- LiveData eski projelerde tercih edilir.
- State yönetimi, ViewModel'in en önemli görevidir. 