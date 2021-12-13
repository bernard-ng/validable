[kotlin-version](https://img.shields.io/badge/kotlin-1.4.31-orange)
[![](https://jitpack.io/v/devscast/validable.svg)](https://jitpack.io/#devscast/validable)

# validable

Validating text fields when using jetpack compose can sometimes be challenging and verbose.

Validable is an extensible library that allows you to validate your text fields in a simpler way while having a reusable code.

This is what it looks like :

```kotlin  
@Composable  
fun MyScreen() { 
 
     val emailField = remember { EmailValidable() }  
     
     TextField(  
	     value = emailField.value,
	     onValueChange = { emailField.value = it }, // update the text  
		 isError = emailField.hasError(), // check if the field is not valid    
	)  
  
	AnimatedVisibility(visible = emailField.hasError() {
	
	    Text(
            text = emailField.errorMessage ?: "",
            modifier = Modifier.fillMaxWidth(),
            style = LocalTextStyle.current.copy(color = MaterialTheme.colors.error)
        )
        
	}  
	
	Button(onClick = {  
		 // pass all fields to the withValidable method 
		 withValidable(emailField) {  
		 
			 // will be executed if all fields are valid 		
			 Toast.makeText(context,"All fields are valid",Toast.LENGTH_SHORT).show() 
		} 
	}) { 
		Text(text = "Submit") 
	}  
}  
```

## Installation

**Step 1.** Add the JitPack repository to your build file

Add it in your root build.gradle at the end of repositories:

```groovy
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
```

**Step 2.** Add the dependency

```groovy
dependencies {
    implementation 'com.github.devscast:validable:x.y'
}
```

The latest version of this library is [![](https://jitpack.io/v/devscast/validable.svg)](https://jitpack.io/#devscast/validable)

## For full documentation, check out the [wiki](https://github.com/devscast/validable/wiki) page
