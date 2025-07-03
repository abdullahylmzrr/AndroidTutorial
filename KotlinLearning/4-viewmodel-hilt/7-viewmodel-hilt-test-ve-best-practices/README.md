# 7. ViewModel, Hilt Test ve Best Practices

ViewModel ve Hilt ile yazdığın kodun test edilebilir ve sürdürülebilir olması için bazı en iyi uygulamalar vardır.

## 7.1. Fake Repository ile Test
Gerçek API yerine sahte repository kullanarak ViewModel test edebilirsin.
```kotlin
class FakeKullaniciRepository : KullaniciRepository {
    override suspend fun kullanicilariGetir() = listOf(Kullanici(1, "Test", "test@example.com"))
}
```

## 7.2. Hilt ile Test Module
Gerçek modül yerine test modülü tanımlayabilirsin.
```kotlin
@Module
@TestInstallIn(
    components = [SingletonComponent::class],
    replaces = [AppModule::class]
)
object TestModule {
    @Provides
    fun provideFakeRepo(): KullaniciRepository = FakeKullaniciRepository()
}
```

## 7.3. ViewModel Testi
```kotlin
@get:Rule
val hiltRule = HiltAndroidRule(this)

@Test
fun testKullanicilar() = runBlocking {
    val viewModel = KullaniciViewModel(FakeKullaniciRepository())
    assert(viewModel.kullanicilar.isNotEmpty())
}
```

## 7.4. Best Practices
- Bağımlılıkları constructor ile inject et.
- Test için interface ve fake implementasyonlar kullan.
- Modülleri küçük ve tek sorumluluklu tut.

## Notlar
- Testler, kodun güvenilirliğini ve sürdürülebilirliğini artırır.
- Hilt ile test ortamı kolayca kurulabilir. 