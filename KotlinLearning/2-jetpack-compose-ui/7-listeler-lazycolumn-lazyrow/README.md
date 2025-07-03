# 7. Listeler: LazyColumn ve LazyRow

Jetpack Compose'da uzun listeleri performanslı şekilde göstermek için LazyColumn ve LazyRow kullanılır.

## 7.1. LazyColumn (Dikey Liste)
Birçok öğeyi dikey olarak, sadece ekranda görünenleri çizerek gösterir.

```kotlin
@Composable
fun DikeyListe() {
    val isimler = listOf("Ali", "Ayşe", "Mehmet", "Zeynep", "Ahmet")
    LazyColumn {
        items(isimler.size) { index ->
            Text(text = isimler[index], modifier = Modifier.padding(8.dp))
        }
    }
}
```

## 7.2. LazyRow (Yatay Liste)
Yatayda kaydırılabilir liste oluşturur.

```kotlin
@Composable
fun YatayListe() {
    val sayilar = (1..10).toList()
    LazyRow {
        items(sayilar.size) { index ->
            Box(
                modifier = Modifier
                    .size(60.dp)
                    .padding(4.dp)
                    .background(Color.LightGray)
            ) {
                Text(text = sayilar[index].toString(), modifier = Modifier.align(Alignment.Center))
            }
        }
    }
}
```

## 7.3. Scroll ve Performans
- LazyColumn/LazyRow, sadece ekranda görünen item'ları oluşturur.
- Büyük veri setlerinde performanslıdır.

## Notlar
- Listelerde her item için ayrı bir composable fonksiyon yazmak kodun okunabilirliğini artırır. 