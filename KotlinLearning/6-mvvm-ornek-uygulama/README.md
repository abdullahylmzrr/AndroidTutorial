# 6. MVVM Örnek Uygulama

Bu bölümde, önceki tüm adımları birleştirerek tam bir MVVM (Model-View-ViewModel) mimarisiyle örnek bir Android uygulaması geliştireceğiz. Kullanılan teknolojiler: Jetpack Compose, Retrofit, ViewModel, Hilt, Coil.

## 6.1. Proje Klasör Yapısı Önerisi
```
app/
  ├─ di/           # Hilt modülleri
  ├─ model/        # Veri modelleri
  ├─ network/      # Retrofit API servisleri
  ├─ repository/   # Veri kaynakları
  ├─ ui/           # Compose ekranları
  ├─ viewmodel/    # ViewModel sınıfları
```

## 6.2. Akış Şeması
1. Kullanıcı uygulamayı açar.
2. ViewModel, Repository üzerinden API'den veri çeker.
3. Gelen veri UI'da gösterilir (resim için Coil kullanılır).

## 6.3. Temel Kod Parçaları

### Model
```kotlin
data class Kullanici(
    val id: Int,
    val isim: String,
    val avatarUrl: String
)
```

### API Servisi
```kotlin
interface ApiService {
    @GET("kullanicilar")
    suspend fun kullanicilariGetir(): List<Kullanici>
}
```

### Repository
```kotlin
class KullaniciRepository @Inject constructor(private val api: ApiService) {
    suspend fun kullanicilariGetir() = api.kullanicilariGetir()
}
```

### ViewModel
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

### Hilt Modülü
```kotlin
@Module
@InstallIn(SingletonComponent::class)
object AppModule {
    @Provides
    fun provideApiService(): ApiService = Retrofit.Builder()
        .baseUrl("https://ornekapi.com/")
        .addConverterFactory(GsonConverterFactory.create())
        .build()
        .create(ApiService::class.java)
}
```

### Compose UI
```kotlin
@Composable
fun KullaniciListesi(viewModel: KullaniciViewModel = hiltViewModel()) {
    LazyColumn {
        items(viewModel.kullanicilar) { kullanici ->
            Row {
                ResimGoster(url = kullanici.avatarUrl)
                Text(kullanici.isim)
            }
        }
    }
}
```

### Resim Gösterme (Coil)
```kotlin
@Composable
fun ResimGoster(url: String) {
    Image(
        painter = rememberAsyncImagePainter(url),
        contentDescription = null,
        modifier = Modifier.size(48.dp),
        contentScale = ContentScale.Crop
    )
}
```

## 6.4. Notlar
- Gerçek projede hata yönetimi, loading durumu ve testler de eklenmelidir.
- Tüm bağımlılıklar (Retrofit, Hilt, Coil, Compose) build.gradle dosyasında tanımlanmalıdır.

---

Tebrikler! Artık modern Android uygulamaları geliştirmek için temel bilgiye sahipsin. Her adımı kendi projenle deneyerek pekiştirebilirsin. 