# 7. Test ve Best Practices

Modern Android projelerinde test yazmak ve en iyi uygulamaları takip etmek sürdürülebilirlik için çok önemlidir.

## 7.1. Fake Repository ile Test
Gerçek veri kaynağı yerine sahte repository ile ViewModel veya UseCase test edebilirsin.
```kotlin
class FakeKullaniciRepository : KullaniciRepository {
    override suspend fun kullanicilariGetir() = listOf(KullaniciEntity(1, "Test"))
}
```

## 7.2. Room ve WorkManager Testi
- Room için in-memory database kullanabilirsin.
- WorkManager için TestWorkerFactory ile bağımlılıkları inject edebilirsin.

## 7.3. UI Testi (Compose)
```kotlin
@get:Rule
val composeTestRule = createComposeRule()

@Test
fun kullaniciListesiGorunuyor() {
    composeTestRule.setContent {
        KullaniciListesi(viewModel = KullaniciViewModel(FakeKullaniciRepository()))
    }
    composeTestRule.onNodeWithText("Test").assertExists()
}
```

## 7.4. Best Practices
- Katmanları net ayır, interface ve fake implementasyonlar kullan.
- Hilt ile bağımlılıkları otomatik yönet.
- Testler için bağımlılıkları kolayca değiştirilebilir yap.
- Kodun okunabilirliğini ve sürdürülebilirliğini ön planda tut.

## Notlar
- Testler, uygulamanın güvenilirliğini artırır.
- Best practices ile büyük projelerde kod yönetimi kolaylaşır. 