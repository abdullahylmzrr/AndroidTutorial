# 10. Navigation Compose

Jetpack Compose'da ekranlar arası geçiş için Navigation Compose kütüphanesi kullanılır.

## 10.1. Temel Kullanım
```kotlin
import androidx.navigation.compose.*

@Composable
fun NavigationOrnek() {
    val navController = rememberNavController()
    NavHost(navController, startDestination = "ana") {
        composable("ana") { AnaEkran(navController) }
        composable("detay") { DetayEkran() }
    }
}

@Composable
fun AnaEkran(navController: NavController) {
    Button(onClick = { navController.navigate("detay") }) {
        Text("Detaya Git")
    }
}

@Composable
fun DetayEkran() {
    Text("Detay Ekranı")
}
```

## 10.2. Argüman Geçme
Bir ekrandan diğerine veri gönderebilirsin.
```kotlin
composable("detay/{id}") { backStackEntry ->
    val id = backStackEntry.arguments?.getString("id")
    Text("ID: $id")
}
// Geçiş: navController.navigate("detay/42")
```

## Notlar
- Navigation Compose, ekranlar arası geçişi kolaylaştırır.
- NavController ile istediğin ekrana kolayca gidebilirsin. 