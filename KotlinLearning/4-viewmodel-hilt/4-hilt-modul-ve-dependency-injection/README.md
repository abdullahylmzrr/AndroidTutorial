# 4. Hilt Modül ve Dependency Injection

Hilt ile bağımlılıkları yönetmek için modül tanımlanır. Modül, uygulamanın farklı yerlerinde kullanılacak nesneleri sağlar.

## 4.1. Modül Tanımı
```kotlin
import dagger.Module
import dagger.Provides
import dagger.hilt.InstallIn
import dagger.hilt.components.SingletonComponent

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
- `@Module`: Modül olduğunu belirtir.
- `@InstallIn`: Hangi yaşam döngüsünde olacağını belirtir.
- `@Provides`: Sağlayıcı fonksiyon.

## 4.2. Singleton ve Scope
- `SingletonComponent`: Uygulama boyunca tek nesne oluşturur.
- Farklı scope'lar: ActivityRetainedComponent, ViewModelComponent, vb.

## 4.3. ViewModel'de Constructor Injection
```kotlin
@HiltViewModel
class KullaniciViewModel @Inject constructor(
    private val repo: KullaniciRepository
) : ViewModel() {
    // ...
}
```

## Notlar
- Modüller, bağımlılıkların merkezi olarak yönetilmesini sağlar.
- Hilt ile test ve modülerlik kolaylaşır. 