# 3. Model ve Veri Sınıfları

Retrofit ile API'den gelen verileri Kotlin nesnelerine dönüştürmek için model (data class) tanımlanır.

## 3.1. Basit Model Sınıfı
```kotlin
data class Kullanici(
    val id: Int,
    val isim: String,
    val email: String
)
```
- JSON'daki alan adları ile Kotlin'deki property adları aynı olmalı.

## 3.2. Farklı Alan Adı Kullanımı
Eğer JSON'daki alan adı ile property adı farklıysa @SerializedName kullanılır.
```kotlin
import com.google.gson.annotations.SerializedName

data class Kullanici(
    @SerializedName("user_id") val id: Int,
    @SerializedName("name") val isim: String
)
```

## 3.3. Liste ve İç İçe Modeller
```kotlin
data class ApiCevap(
    val kullanicilar: List<Kullanici>
)
```

## Notlar
- Model sınıfları, API'den gelen JSON yapısına uygun olmalıdır.
- Gson veya Moshi gibi converter'lar otomatik eşleme yapar. 