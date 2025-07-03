# 6. JSON Parsing ve Custom Converter

Retrofit, API'den gelen JSON verisini otomatik olarak Kotlin nesnelerine dönüştürür. Bunun için converter kullanılır.

## 6.1. Gson ile JSON Parsing
Varsayılan olarak en çok kullanılan converter Gson'dur.

```kotlin
val retrofit = Retrofit.Builder()
    .baseUrl("https://api.ornek.com/")
    .addConverterFactory(GsonConverterFactory.create())
    .build()
```
- Model sınıflarının property adları JSON ile aynı olmalı.

## 6.2. Moshi ile JSON Parsing
Alternatif olarak Moshi kullanılabilir.

```kotlin
import com.squareup.moshi.Moshi
import retrofit2.converter.moshi.MoshiConverterFactory

val moshi = Moshi.Builder().build()
val retrofit = Retrofit.Builder()
    .baseUrl("https://api.ornek.com/")
    .addConverterFactory(MoshiConverterFactory.create(moshi))
    .build()
```

## 6.3. Custom Converter Eklemek
Kendi veri formatını parse etmek için custom converter ekleyebilirsin.

```kotlin
val retrofit = Retrofit.Builder()
    .baseUrl("https://api.ornek.com/")
    .addConverterFactory(MyCustomConverterFactory())
    .build()
```

## Notlar
- Converter, JSON ile Kotlin nesneleri arasında köprü kurar.
- Farklı veri formatları için farklı converter'lar eklenebilir. 