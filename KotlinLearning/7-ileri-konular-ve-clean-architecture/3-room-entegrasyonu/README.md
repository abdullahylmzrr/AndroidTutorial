# 3. Room ile Veritabanı Entegrasyonu

Room, Android'de SQLite veritabanı ile kolay ve güvenli veri saklama sağlar. Hilt ile kolayca entegre edilir.

## 3.1. Entity (Tablo Sınıfı)
```kotlin
import androidx.room.Entity
import androidx.room.PrimaryKey

@Entity
data class KullaniciEntity(
    @PrimaryKey val id: Int,
    val isim: String
)
```

## 3.2. DAO (Veri Erişim Arayüzü)
```kotlin
import androidx.room.Dao
import androidx.room.Query

@Dao
interface KullaniciDao {
    @Query("SELECT * FROM KullaniciEntity")
    suspend fun tumKullanicilar(): List<KullaniciEntity>
}
```

## 3.3. RoomDatabase Tanımı
```kotlin
import androidx.room.Database
import androidx.room.RoomDatabase

@Database(entities = [KullaniciEntity::class], version = 1)
abstract class AppDatabase : RoomDatabase() {
    abstract fun kullaniciDao(): KullaniciDao
}
```

## 3.4. Hilt ile Room Kurulumu
```kotlin
@Module
@InstallIn(SingletonComponent::class)
object DatabaseModule {
    @Provides
    fun provideDatabase(@ApplicationContext context: Context): AppDatabase =
        Room.databaseBuilder(context, AppDatabase::class.java, "app_db").build()

    @Provides
    fun provideKullaniciDao(db: AppDatabase): KullaniciDao = db.kullaniciDao()
}
```

## Notlar
- Room ile veriler güvenli ve kolayca saklanır.
- Hilt ile Room ve DAO'lar otomatik olarak inject edilir. 