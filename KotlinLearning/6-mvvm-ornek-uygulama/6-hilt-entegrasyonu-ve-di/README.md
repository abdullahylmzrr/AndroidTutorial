# 6. Hilt Entegrasyonu ve Dependency Injection

MVVM örnek uygulamada Hilt ile dependency injection (bağımlılık enjeksiyonu) kullanılır. Bu, nesnelerin otomatik olarak oluşturulmasını ve yönetilmesini sağlar.

## 6.1. AppModule ile Bağımlılık Sağlama
```kotlin
@Module
@InstallIn(SingletonComponent::class)
object AppModule {
    @Provides
    fun provideApiService(): ApiService = Retrofit.Builder()
        .baseUrl("https://api.ornek.com/")
        .addConverterFactory(GsonConverterFactory.create())
        .build()
        .create(ApiService::class.java)
}
```

## 6.2. Repository ve ViewModel'de Injection
Repository ve ViewModel, Hilt ile otomatik olarak oluşturulur.
```kotlin
class KullaniciRepository @Inject constructor(private val api: ApiService)

@HiltViewModel
class KullaniciViewModel @Inject constructor(private val repo: KullaniciRepository) : ViewModel() { /* ... */ }
```

## 6.3. Uygulama Sınıfı
```kotlin
@HiltAndroidApp
class MyApp : Application()
```

AndroidManifest.xml:
```xml
<application android:name=".MyApp" ... >
```

## Notlar
- Hilt, bağımlılıkları otomatik yönetir ve test yazmayı kolaylaştırır.
- AppModule ile tüm uygulama için ortak nesneler sağlanır. 