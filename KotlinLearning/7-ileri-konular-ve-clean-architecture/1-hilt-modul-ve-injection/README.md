# 1. Dagger Hilt ile Dependency Injection

Dagger Hilt, Android'de dependency injection (bağımlılık enjeksiyonu) işlemlerini kolaylaştırır.

## 1.1. Hilt Kurulumu
- build.gradle dosyana ekle:
```gradle
dependencies {
    implementation "com.google.dagger:hilt-android:2.48"
    kapt "com.google.dagger:hilt-android-compiler:2.48"
}
```
- Application sınıfını işaretle:
```kotlin
@HiltAndroidApp
class MyApp : Application()
```

## 1.2. Hilt Modül Tanımı
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

## 1.3. ViewModel ve Repository'de Injection
```kotlin
class KullaniciRepository @Inject constructor(private val api: ApiService)

@HiltViewModel
class KullaniciViewModel @Inject constructor(private val repo: KullaniciRepository) : ViewModel() { /* ... */ }
```

## 1.4. Singleton ve Scope
- `@Singleton`: Uygulama boyunca tek nesne oluşturur.
- Farklı scope'lar: ActivityRetainedScoped, ViewModelScoped, vb.

## Notlar
- Hilt ile bağımlılıklar otomatik yönetilir.
- Test ve modülerlik için idealdir. 