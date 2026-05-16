## Primer proyecto de desarrollo usando Kotlin 

<img width="312" height="667" alt="Image" src="https://github.com/user-attachments/assets/e5b7591a-5769-4350-91c0-cc3c82005bfa" />

<img width="344" height="740" alt="Image" src="https://github.com/user-attachments/assets/3af8545d-207d-4cc0-bb5a-a204216be16a" />

---

Patrones de diseño
Patrones de arquitectura
Principios de SOLID 
Clean arquitectura 
Clean code

Recordatorio de la ética, código ética del Perú, colegio ingeniero del Perú, 

Bound de context y subdominio (solución) la comunicación se da por eventos, capa de dominio, reglas de negocio, separar las responsabilidades, 

Capas: 
Presentation
Infrastructure
Application
Domain

EvenStorming, realizar para este entrega, por cada Bound de contextex se hace un flujo de (Domain message Flow modeling)

Características de Android y Ios, Android versión 16, SDK es un conjunto de herramienta para el desarrollo de sistemas, Android es desarrollado por Google 
iOS, 

Materiales de alcance 

- https://github.com/ddd-crew/
- https://www.blablacar.es/ 


---

Jet pass compose, parámetros tipo función, colbach. 
Los composables no son vistas, son funciones que van a renderizar vistas, los funciones tipo unit que no devuelve nada, (unit o void)
content: @Composable () -> Unit // es una función que no retorna nada 
Un Composable puedo llamar de otro Composable 

jet pat compose, nos permite aplicar programación declarativa, interfas declarativa. 

https://dribbble.com/search/login-app

https://mvnrepository.com/artifact/androidx.compose.material/material-icons-extended

fácil de importar biblioteca de icon de pripio andor


Session 03 

Aprendizaje de GitFlow 
Guía para repositorio de doc as code, enseña de GitFlow (Manejo de la documentación), recomendación para informe colaborativo. mas usado en proyectos.
Flutter esta hecho para móvil, escritorio, sale al mercado del 2019
media hora de examen del PC1, 
Remember sirve para que el estado se mantenga. Un estado es un valor que cambia (refresque, actualicé, recompone)
Testing, casos de prueba, priorizar los historias de usuario 

Materrial Design en Jetpack Compose, materiales gracias a nuestros a amigos de NotBook 

dp es la unidad medida y para texto es sp (Scaleble Pixels), es como rem en la web - la regla de 8 (espaciados en múltiplos de 8dp
Diseño Edge-to-Edge

Composable no retorna vista por que unit no retorna nada, genera vista

https://fonts.google.com/icons // es mas eficiente para icosn descargar(Android descargar)

material 3

Figma exporter
Lotte animations 

Cuarto video imagenes (01: 50)m imagen generada por gpt y figma exporter 

---

```kotlin

package upc.edu.pe
// ES METADATA
import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.activity.enableEdgeToEdge
import androidx.compose.foundation.layout.Column
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.foundation.layout.padding
import androidx.compose.material3.Scaffold
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable
import androidx.compose.ui.Modifier
import androidx.compose.ui.tooling.preview.Preview
import upc.edu.pe.ui.theme.EasyShopTheme

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContent {
            EasyShopTheme {
                Scaffold(modifier = Modifier.fillMaxSize()) { innerPadding ->
                    Greeting(
                        name = "Android",
                        modifier = Modifier.padding(innerPadding)
                    )
                }
            }
        }
    }
}

// Es una funcion que genera vista, las funciones puedes recibir los parametros
@Composable
fun Greeting(name: String, modifier: Modifier = Modifier) {
    Column(modifier = Modifier.fillMaxSize()) {  // cuando el ultimo parametro de Column es una función
        Text(
            text = "Hello $name!",
            modifier = modifier
        )
        Text("Universidad Peruana de Ciencias Aplicadas")
    }
}

// UNIT, es para pasar parametro de una función a otra funciones

@Preview(showBackground = true)

@Composable // Función composable
fun GreetingPreview() {
    EasyShopTheme {  // Son composable
        Greeting("Android")
    }
}

// ALT + Enter para importar en el mismpo código

// ANOTES
/*
fun Greeting(name: String, modifier: Modifier = Modifier) {
    Text( // Text es un Composable, donde ya tiene un valor por defecto
        text = "Hello $name!",
        modifier = modifier.fillMaxSize()  // es una parametro, fillMaxSize es para cubrir todo el espacio.
    )
}
*/

```


---

Regla de 8: Jet pass composable 
Edge to Edge pantalla completa. 
responsing design 

el uso de imágenes estáticas, tener distintas resoluciones
usamos gpt para generar imágenes y pasamos para renderizar con figma exportert a figma, son fondo

https://material-foundation.github.io/material-theme-builder/  // Para colores y descargar en jet pass compose

Opción code -> optimizas // es para limiar cuando remplazas


```kotlin
// var email = ""  // Deckaración implicita
    val email = remember { // Un valor que se puede cambiar
        mutableStateOf("")  // Estado mutable
    }

    var password by remember { // Nos permite generar estados, By (alt + enter)
        mutableStateOf("")
    }

    val isVisible = remember {
        mutableStateOf(false)
    }

    Column(
        modifier = Modifier.fillMaxSize(),
        verticalArrangement = Arrangement.Center
    ) { // para cubrir todo el espacio
        OutlinedTextField(value = email.value, onValueChange = {
            email.value = it
        }, modifier = Modifier
            .fillMaxSize()
            .padding(8.dp))

        OutlinedTextField(
            value = password, onValueChange = {
                password = it
            }, modifier = Modifier
                .fillMaxSize()
                .padding(8.dp),
            visualTransformation = if (isVisible.value){
                VisualTransformation.None
            } else {
                PasswordVisualTransformation()
            }
        )

        OutlinedButton(onClick = {

        }, modifier = Modifier
            .fillMaxSize()
            .padding(8.dp)) {
            Text(text = "Login")
        }
    }
```
---

A continuación de describe todo el código a nivel de desarrollo de software. 

Se muestra 4 imagenes de animales, consume API Rest - Home.kt

```kotlin
package pe.edu.upc.easyschop

import androidx.compose.foundation.Image
import androidx.compose.foundation.layout.Column
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.foundation.layout.size
import androidx.compose.foundation.lazy.LazyRow
import androidx.compose.foundation.lazy.items
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.graphics.painter.Painter
import androidx.compose.ui.res.painterResource
import androidx.compose.ui.text.font.FontWeight
import androidx.compose.ui.tooling.preview.Preview
import androidx.compose.ui.unit.dp
import pe.edu.upc.easyschop.ui.theme.AppTheme

@Composable
fun Home(modifier: Modifier = Modifier) {

    val categories = listOf(
        Category(painter = painterResource(R.drawable.dogcategory), name = "Dog"),
        Category(painter = painterResource(R.drawable.catcategory), name = "Cat"),
        Category(painter = painterResource(R.drawable.birdcategory), name = "Bird"),
        Category(painter = painterResource(R.drawable.fishcategory), name = "Fish")
    )

    Column(modifier = Modifier.fillMaxSize()) {
        Text(text = "Categories", fontWeight = FontWeight.Bold)
        LazyRow {
            items(categories) {
                Column(horizontalAlignment = Alignment.CenterHorizontally) {
                    Image(
                        painter = it.painter,
                        contentDescription = it.name,
                        modifier = Modifier.size(64.dp)
                    )
                    Text(text = it.name)
                }
            }
        }
    }
}

@Preview
@Composable
fun HomePreview() {
    AppTheme() {
        Home()
    }
}

data class Category(
    val painter: Painter,
    val name: String
)
```

Se muestra una imagen mas user and password (boton inicio), esta en Login.kt

```kotlin
package pe.edu.upc.easyschop

import androidx.compose.foundation.Image
import androidx.compose.foundation.layout.Arrangement
import androidx.compose.foundation.layout.Column
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.foundation.layout.fillMaxWidth
import androidx.compose.foundation.layout.height
import androidx.compose.foundation.layout.padding
import androidx.compose.material3.Button
import androidx.compose.material3.Icon
import androidx.compose.material3.IconButton
import androidx.compose.material3.OutlinedTextField
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable
import androidx.compose.runtime.getValue
import androidx.compose.runtime.mutableStateOf
import androidx.compose.runtime.remember
import androidx.compose.runtime.setValue
import androidx.compose.ui.Modifier
import androidx.compose.ui.layout.ContentScale
import androidx.compose.ui.res.painterResource
import androidx.compose.ui.text.input.PasswordVisualTransformation
import androidx.compose.ui.text.input.VisualTransformation
import androidx.compose.ui.tooling.preview.Preview
import androidx.compose.ui.unit.dp
import pe.edu.upc.easyschop.ui.theme.AppTheme

@Composable
fun Login(modifier: Modifier = Modifier) {
    var email = remember { mutableStateOf("") }

    var password = remember { mutableStateOf("") }

    val isVisible = remember {
        mutableStateOf(false)
    }

    Column(
        modifier = Modifier.fillMaxSize(),
        verticalArrangement = Arrangement.Center // Centre verticalmente, un composable no retorna nada (unit), genera vistas
    ) {

        Image(
            painter = painterResource(
                id = R.drawable.background
            ),
            contentDescription = null,
            modifier = Modifier.height(256.dp).fillMaxSize(),
            contentScale = ContentScale.Fit
        )

        OutlinedTextField(
            value = email.value, onValueChange = {
            email.value = it
        }, placeholder = {
            Text("Email")
        }, modifier = Modifier
                .fillMaxWidth()
                .padding(8.dp)
        )

        OutlinedTextField(
            value = password.value,
            onValueChange = {
                password.value = it
            },
            placeholder = {
                Text("Password")
            },
            modifier = Modifier
                .fillMaxWidth()
                .padding(8.dp),
            visualTransformation = if (isVisible.value) {
                VisualTransformation.None
            } else {
                PasswordVisualTransformation()
            },
            trailingIcon = {
                IconButton(
                    onClick = {
                        isVisible.value = !isVisible.value
                    }) {
                    Icon(
                        painter = painterResource(
                            if (isVisible.value) {
                                R.drawable.visibility
                            } else {
                                R.drawable.visibility_off
                            }
                        ), contentDescription = null
                    )
                }
            })

        Button(
            onClick = {},
            modifier = Modifier
                .fillMaxWidth()
                .padding(8.dp)
        ) {
            Text("Login")
        }
    }
}


@Preview
@Composable
fun LoginPreview() {
    AppTheme() {
        Login()
    }
}
```

Aqui de detalla el MainActivity

```kotlin
package pe.edu.upc.easyschop

import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.activity.enableEdgeToEdge
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.foundation.layout.padding
import androidx.compose.material3.Scaffold
import androidx.compose.ui.Modifier
import pe.edu.upc.easyschop.ui.theme.AppTheme

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContent {
            AppTheme {
                Scaffold(modifier = Modifier.fillMaxSize()) { innerPadding ->
                    Login(Modifier.padding(innerPadding))
                }
            }
        }
    }
}
```
