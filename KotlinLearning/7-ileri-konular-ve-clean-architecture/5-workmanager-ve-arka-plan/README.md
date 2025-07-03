# 5. WorkManager ve Arka Plan İşleri

WorkManager, zamanlanmış veya uzun süren işleri arka planda güvenli şekilde çalıştırmak için kullanılır.

## 5.1. Worker Tanımı
```kotlin
class SenkronizasyonWorker @AssistedInject constructor(
    @Assisted context: Context,
    @Assisted params: WorkerParameters,
    private val repo: KullaniciRepository
) : CoroutineWorker(context, params) {
    override suspend fun doWork(): Result {
        repo.senkronizeEt()
        return Result.success()
    }
}
```

## 5.2. Hilt ile Worker Injection
- Worker'larda Hilt injection için HiltWorkerFactory kullanılır.
```kotlin
@Module
@InstallIn(SingletonComponent::class)
abstract class WorkerModule {
    @Binds
    abstract fun bindWorkerFactory(factory: MyWorkerFactory): HiltWorkerFactory
}
```

## 5.3. WorkManager ile İş Başlatma
```kotlin
val workRequest = OneTimeWorkRequestBuilder<SenkronizasyonWorker>().build()
WorkManager.getInstance(context).enqueue(workRequest)
```

## 5.4. Repository ile Entegrasyon
- Worker, repository veya usecase üzerinden veri senkronizasyonu yapar.

## Notlar
- WorkManager, arka plan işlerinde güvenli ve esnek bir çözümdür.
- Hilt ile Worker'a bağımlılık injection yapılabilir. 