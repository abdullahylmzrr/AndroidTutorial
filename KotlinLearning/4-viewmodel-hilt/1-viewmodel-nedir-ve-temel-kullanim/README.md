# 1. ViewModel Nedir ve Temel Kullanım

ViewModel, Android'de ekran (UI) ile veri arasındaki köprüdür. Veriyi saklar ve yönetir, ekran döndüğünde veri kaybolmaz.

## 1.1. ViewModel Nedir?
- UI'dan bağımsız olarak veriyi saklar.
- Ekran döndüğünde (ör: telefon yatay-dikey) veri kaybolmaz.
- MVVM mimarisinin temel taşıdır.

## 1.2. Temel ViewModel Oluşturma
```kotlin
import androidx.lifecycle.ViewModel

class SayacViewModel : ViewModel() {
    var sayi = 0
        private set
    fun arttir() { sayi++ }
}
```

## 1.3. Compose'da ViewModel Kullanımı
```kotlin
import androidx.lifecycle.viewmodel.compose.viewModel

@Composable
fun SayacEkrani(viewModel: SayacViewModel = viewModel()) {
    Column {
        Text("Sayaç: ${viewModel.sayi}")
        Button(onClick = { viewModel.arttir() }) {
            Text("Arttır")
        }
    }
}
```

## Notlar
- ViewModel, UI ile veri arasındaki en iyi köprüdür.
- ViewModel'de state yönetimi için StateFlow veya LiveData kullanmak önerilir. 