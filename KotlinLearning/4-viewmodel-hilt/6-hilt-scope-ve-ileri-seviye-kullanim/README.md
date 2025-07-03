# 6. Hilt Scope ve İleri Seviye Kullanım

Hilt'te scope, bir nesnenin yaşam süresini belirler. Farklı scope'lar ile nesnelerin ömrü kontrol edilir.

## 6.1. @Singleton
- Uygulama boyunca tek bir nesne oluşturur.
```kotlin
@Singleton
class ApiClient @Inject constructor() { /* ... */ }
```

## 6.2. @ActivityRetainedScoped
- Activity yaşam döngüsü boyunca nesne aynı kalır.
```kotlin
@ActivityRetainedScoped
class OturumYonetici @Inject constructor() { /* ... */ }
```

## 6.3. @ViewModelScoped
- ViewModel ömrü boyunca nesne aynı kalır.
```kotlin
@ViewModelScoped
class ViewModelHelper @Inject constructor() { /* ... */ }
```

## 6.4. Farklı Scope'lar ve Kullanım
- @Singleton: Tüm uygulama
- @ActivityRetainedScoped: Activity ve alt fragmentler
- @ViewModelScoped: Sadece ViewModel

## 6.5. İleri Seviye Injection
Birden fazla constructor parametresi, interface implementasyonu, farklı modüllerden injection örnekleri:
```kotlin
interface Logger { fun log(msg: String) }

class FileLogger @Inject constructor() : Logger { override fun log(msg: String) { /* ... */ } }

@Module
@InstallIn(SingletonComponent::class)
object LoggerModule {
    @Singleton
    @Provides
    fun provideLogger(): Logger = FileLogger()
}

@HiltViewModel
class OrnekViewModel @Inject constructor(private val logger: Logger) : ViewModel() { /* ... */ }
```

## Notlar
- Doğru scope seçimi, bellek ve performans için önemlidir.
- İleri seviye kullanımda interface ve farklı modüllerle esnek yapı kurabilirsin. 