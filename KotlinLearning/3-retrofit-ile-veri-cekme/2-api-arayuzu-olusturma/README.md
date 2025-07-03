# 2. API Arayüzü Oluşturma

Retrofit ile API'ye istek göndermek için bir arayüz (interface) tanımlanır. Bu arayüzde HTTP metodunu ve endpoint'i belirtirsin.

## 2.1. Basit GET İsteği
```kotlin
import retrofit2.http.GET

interface ApiService {
    @GET("kullanicilar")
    suspend fun kullanicilariGetir(): List<Kullanici>
}
```
- `@GET`: GET isteği yapar.
- `suspend`: Coroutine ile asenkron çalışır.

## 2.2. Path ve Query Parametreleri
```kotlin
import retrofit2.http.Path
import retrofit2.http.Query

interface ApiService {
    @GET("kullanici/{id}")
    suspend fun kullaniciGetir(@Path("id") id: Int): Kullanici

    @GET("arama")
    suspend fun ara(@Query("q") sorgu: String): List<Kullanici>
}
```
- `@Path`: URL içindeki değişkeni belirtir.
- `@Query`: Sorgu parametresi ekler.

## 2.3. POST İsteği
```kotlin
import retrofit2.http.Body
import retrofit2.http.POST

interface ApiService {
    @POST("kullanici")
    suspend fun kullaniciEkle(@Body yeniKullanici: Kullanici): Kullanici
}
```
- `@POST`: POST isteği yapar.
- `@Body`: Gövdeye veri ekler.

## Notlar
- Her endpoint için ayrı bir fonksiyon tanımlanır.
- Anotasyonlar ile istek türü ve parametreler kolayca yönetilir. 