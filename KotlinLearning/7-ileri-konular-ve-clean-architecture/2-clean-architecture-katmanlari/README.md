# 2. Clean Architecture Katmanları

Clean Architecture, kodun sürdürülebilirliğini ve test edilebilirliğini artıran bir mimari yaklaşımdır.

## 2.1. Katmanlar
- **Data:** Room DAO, Retrofit API, veri kaynakları (local/remote)
- **Domain:** UseCase'ler, saf iş mantığı (Android bağımsız)
- **Presentation:** ViewModel, UI (Compose/Fragment/Activity)

## 2.2. Bağımlılık Akışı
- UI → ViewModel → UseCase → Repository → (API/Room)
- Her katman bir alt katmana bağımlı, üst katmana bağımlı değil.

## 2.3. UseCase Örneği
```kotlin
class GetKullanicilarUseCase @Inject constructor(private val repo: KullaniciRepository) {
    suspend operator fun invoke() = repo.kullanicilariGetir()
}
```

## 2.4. Örnek Klasör Yapısı
```
app/
  ├─ data/
  ├─ domain/
  ├─ presentation/
```

## Notlar
- Clean Architecture, büyük projelerde kodun yönetimini kolaylaştırır.
- Katmanlar arası bağımlılık minimumda tutulur. 