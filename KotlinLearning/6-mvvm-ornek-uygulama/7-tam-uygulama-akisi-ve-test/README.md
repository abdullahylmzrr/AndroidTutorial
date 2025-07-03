# 7. Tam Uygulama Akışı ve Test

Bu bölümde, MVVM mimarisiyle tam bir uygulama akışı ve test yazma örnekleri bulacaksın.

## 7.1. Tam Akış
1. Kullanıcı uygulamayı açar.
2. UI, ViewModel'den veri ister.
3. ViewModel, repository'den veri çeker.
4. Repository, API'den veriyi alır.
5. UI, ViewModel'den gelen veriyi gösterir.

## 7.2. Fake Repository ile Test
Gerçek API yerine sahte repository ile ViewModel test edebilirsin.
```kotlin
class FakeKullaniciRepository : KullaniciRepository {
    override suspend fun kullanicilariGetir() = listOf(Kullanici(1, "Test", "https://test.com/avatar.png"))
}
```

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
- Katmanları net ayır.
- Test için interface ve fake implementasyonlar kullan.
- Hilt ile bağımlılıkları otomatik yönet.

## Notlar
- Testler, uygulamanın güvenilirliğini artırır.
- Tam akış, MVVM'in tüm avantajlarını gösterir. 