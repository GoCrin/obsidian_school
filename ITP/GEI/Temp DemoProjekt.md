```kotlin
package com.example.demoproject  
  
import android.content.Context  
import androidx.compose.foundation.layout.Arrangement  
import androidx.compose.foundation.layout.Column  
import androidx.compose.foundation.layout.Row  
import androidx.compose.foundation.layout.Spacer  
import androidx.compose.foundation.layout.fillMaxSize  
import androidx.compose.foundation.layout.fillMaxWidth  
import androidx.compose.foundation.layout.height  
import androidx.compose.foundation.layout.padding  
import androidx.compose.material3.Button  
import androidx.compose.material3.Text  
import androidx.compose.material3.TextField  
import androidx.compose.runtime.Composable  
import androidx.compose.runtime.getValue  
import androidx.compose.runtime.mutableStateOf  
import androidx.compose.runtime.remember  
import androidx.compose.runtime.setValue  
import androidx.compose.ui.Modifier  
import androidx.compose.ui.platform.LocalContext  
import androidx.compose.ui.unit.dp  
import androidx.navigation.compose.NavHost  
import androidx.navigation.compose.composable  
  
@Composable  
fun HomeScreen(onSettingsClick: () -> Unit) {  
    var text by remember { mutableStateOf("") }  
    var output by remember { mutableStateOf("") }  
  
    // Almost always the correct way to get the context in a Composeable  
    val context = LocalContext.current  
  
    Column(  
        modifier = Modifier  
            .fillMaxSize()  
            .padding(16.dp)  
    ) {  
        Button(  
            onClick = onSettingsClick  
        ) {  
            Text("Settings")  
        }  
  
        Spacer(modifier = Modifier.height(16.dp))  
  
        TextField(  
            value = text,  
            onValueChange = { text = it },  
            label = { Text("Enter something") },  
            modifier = Modifier.fillMaxWidth()  
        )  
  
        Spacer(modifier = Modifier.height(16.dp))  
  
        Row(  
            modifier = Modifier.fillMaxWidth(),  
            horizontalArrangement = Arrangement.spacedBy(8.dp)  
        ) {  
            Button(  
                onClick = { output = onLoadButton(context) },  
                modifier = Modifier  
                    .weight(1f)  
                //.padding(5.dp, 0.dp)  
            ) {  
                Text("Load")  
            }  
            Button(  
                onClick = { onSaveButton(context, text) },  
                modifier = Modifier  
                    .weight(1f)  
                //   .padding(5.dp, 0.dp)  
            ) {  
                Text("Save")  
            }  
        }  
        Spacer(modifier = Modifier.height(0.dp))  
  
        Text("You entered: $output")  
    }  
}  
  
fun onLoadButton(context: Context): String {  
    return loadShit(context, "myfile")  
}  
  
fun onSaveButton(context: Context, content: String) {  
    saveShit(context, content)  
}  
  
fun saveShit(context: Context, content: String) {  
    val filename = "myfile"  
    context.openFileOutput(filename, Context.MODE_PRIVATE).use {  
        it.write(content.toByteArray())  
    }  
}  
  
fun loadShit(context: Context, filename: String): String {  
  
    return context.openFileInput(  
        filename  
    ).bufferedReader().useLines { lines ->  
        lines.fold("") { some, text ->  
            "$some\n$text"  
        }  
    }}
```

```kotlin
package com.example.demoproject  
  
import android.content.Context  
import android.os.Bundle  
import androidx.activity.ComponentActivity  
import androidx.activity.compose.setContent  
import androidx.activity.enableEdgeToEdge  
import androidx.compose.foundation.layout.fillMaxSize  
import androidx.compose.foundation.layout.padding  
import androidx.compose.material3.Scaffold  
import androidx.compose.material3.Text  
import androidx.compose.runtime.Composable  
import androidx.compose.ui.Modifier  
import androidx.compose.ui.tooling.preview.Preview  
import com.example.demoproject.ui.theme.DemoProjectTheme  
import androidx.activity.compose.setContent  
import androidx.compose.foundation.gestures.DraggableState  
import androidx.compose.foundation.gestures.draggable  
import androidx.compose.foundation.layout.*  
import androidx.compose.material3.*  
import androidx.compose.runtime.*  
import androidx.compose.ui.unit.dp  
import androidx.navigation.compose.NavHost  
import androidx.navigation.compose.composable  
import androidx.navigation.compose.rememberNavController  
  
class MainActivity : ComponentActivity() {  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
  
        enableEdgeToEdge()  
        setContent {  
            DemoProjectTheme {  
                MyApp(applicationContext)  
            }  
        }    }  
}  
  
@Composable  
fun Greeting(name: String, modifier: Modifier = Modifier) {  
    Text(  
        text = "Hello $name!",  
        modifier = modifier  
    )  
}  
  
@Preview(showBackground = true)  
@Composable  
fun GreetingPreview() {  
    DemoProjectTheme {  
        Greeting("Android")  
    }  
}  
  
@Composable  
fun MyApp(context: Context) {  
    val navController = rememberNavController()  
  
    NavHost(  
        navController = navController,  
        startDestination = "home"  
    ) {  
        composable("home") {  
            HomeScreen(  
                onSettingsClick = { navController.navigate("settings") }  
            )  
        }  
        composable("settings") {  
            SettingsScreen(  
                onBackClick = { navController.popBackStack() }  
            )  
        }  
    }}
```