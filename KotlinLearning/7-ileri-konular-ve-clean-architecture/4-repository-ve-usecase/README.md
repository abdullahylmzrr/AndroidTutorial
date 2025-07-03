# 4. Repository ve UseCase Katmanı

Repository, veri kaynaklarını (Room, API) merkezi olarak yönetir. UseCase ise iş mantığını kapsar.

## 4.1. Repository ile Veri Yönetimi
```kotlin
class KullaniciRepository @Inject constructor(
    private val api: ApiService,
    private val dao: KullaniciDao
) {
    suspend fun kullanicilariGetir(): List<KullaniciEntity> {
        val apiSonuc = api.kullanicilariGetir()
        // API'den gelen veriyi veritabanına kaydet
        dao.insertAll(apiSonuc.map { KullaniciEntity(it.id, it.isim) })
        return dao.tumKullanicilar()
    }
}
```

## 4.2. UseCase ile İş Mantığı
```kotlin
class GetKullanicilarUseCase @Inject constructor(private val repo: KullaniciRepository) {
    suspend operator fun invoke() = repo.kullanicilariGetir()
}
```

## 4.3. Neden UseCase?
- İş mantığını domain katmanında toplar.
- Test yazmayı ve kodun sürdürülebilirliğini kolaylaştırır.

## Notlar
- Repository, veri kaynakları arasında geçişi yönetir.
- UseCase, domain mantığını izole eder. 