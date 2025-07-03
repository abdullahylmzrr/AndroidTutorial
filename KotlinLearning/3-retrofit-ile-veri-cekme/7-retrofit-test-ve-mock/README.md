# 7. Retrofit Test ve Mock

Retrofit ile yazdığın API katmanını test etmek için mock web server ve sahte veri kullanabilirsin.

## 7.1. MockWebServer ile Test
MockWebServer, gerçek bir sunucuya ihtiyaç duymadan istekleri test etmeyi sağlar.

```kotlin
import okhttp3.mockwebserver.MockResponse
import okhttp3.mockwebserver.MockWebServer

val server = MockWebServer()
server.enqueue(MockResponse().setBody("[{\"id\":1,\"isim\":\"Ali\"}]").setResponseCode(200))
server.start()

val retrofit = Retrofit.Builder()
    .baseUrl(server.url("/"))
    .addConverterFactory(GsonConverterFactory.create())
    .build()

val api = retrofit.create(ApiService::class.java)
val sonuc = runBlocking { api.kullanicilariGetir() }
println(sonuc)

server.shutdown()
```

## 7.2. Sahte Veri ile Test
Gerçek API yerine sahte veri döndüren repository veya servis yazabilirsin.

```kotlin
class FakeApiService : ApiService {
    override suspend fun kullanicilariGetir(): List<Kullanici> {
        return listOf(Kullanici(1, "Ali", "ali@example.com"))
    }
}
```

## Notlar
- Testler, uygulamanın güvenilirliğini artırır.
- MockWebServer ile farklı senaryoları kolayca test edebilirsin. 