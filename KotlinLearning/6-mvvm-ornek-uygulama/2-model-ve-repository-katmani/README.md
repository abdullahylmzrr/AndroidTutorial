# 2. Model ve Repository Katmanı

MVVM'de Model ve Repository, verinin yönetildiği ve işlendiği katmanlardır.

## 2.1. Model (Data Class)
Model, API'den veya veritabanından gelen veriyi temsil eder.
```kotlin
data class Kullanici(
    val id: Int,
    val isim: String,
    val avatarUrl: String
)
```

## 2.2. Repository Katmanı
Repository, veri kaynaklarını (API, veritabanı, cache) merkezi olarak yönetir.
```kotlin
class KullaniciRepository @Inject constructor(private val api: ApiService) {
    suspend fun kullanicilariGetir(): List<Kullanici> = api.kullanicilariGetir()
}
```

## 2.3. Neden Repository Kullanılır?
- Veri yönetimini merkezi hale getirir.
- Test yazmayı ve kodun sürdürülebilirliğini kolaylaştırır.

## Notlar
- Model ve repository, MVVM'in temel yapı taşlarındandır.
- Repository, ViewModel ile Model arasındaki köprüdür. 