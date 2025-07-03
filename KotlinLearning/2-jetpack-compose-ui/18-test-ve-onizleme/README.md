# 18. Test ve Önizleme

Jetpack Compose'da arayüzü test etmek ve hızlıca önizlemek için çeşitli araçlar bulunur.

## 18.1. @Preview ile Önizleme
- Composable fonksiyonları Android Studio'da anında görebilirsin.

```kotlin
@Preview(showBackground = true)
@Composable
fun OnizlemeOrnek() {
    Text("Önizleme!")
}
```

## 18.2. UI Testleri
- Compose UI testleri için `compose.ui.test` kütüphanesi kullanılır.

```kotlin
@get:Rule
val composeTestRule = createComposeRule()

@Test
fun butonTiklamaTesti() {
    composeTestRule.setContent {
        Button(onClick = { /* ... */ }) { Text("Tıkla") }
    }
    composeTestRule.onNodeWithText("Tıkla").performClick()
}
```

## 18.3. Test Edilebilirlik için Modifier
- Bileşenlere test etiketleri ekleyebilirsin.

```kotlin
Button(
    onClick = {},
    modifier = Modifier.testTag("kaydetButonu")
) { Text("Kaydet") }

// Testte:
composeTestRule.onNodeWithTag("kaydetButonu").assertExists()
```

## Notlar
- @Preview ile hızlıca tasarımını görebilirsin.
- UI testleri, uygulamanın güvenilirliğini artırır. 