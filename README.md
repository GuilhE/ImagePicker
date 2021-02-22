# About this Fork

I've forked this project to migrate to new [Android Activity Result APIs](https://developer.android.com/training/basics/intents/result).

Usage:
```kotlin
private val launcher = registerForActivityResult(ActivityResultContracts.StartActivityForResult()) {
    if (it.resultCode == Activity.RESULT_OK) {
        val file = ImagePicker.getFile(it.data)!!
        mProfileFile = file
        imgProfile.setLocalImage(file, true)
    }
}

//If you want both Camera and Gallery
ImagePicker.with(this)
    //...
    .createIntentFromDialog { launcher.launch(it) }

//If you want just one option
launcher.launch(
    ImagePicker.with(this)
        //...
        .cameraOnly() // or galleryOnly()
        .createIntent()
)
```

See the original repository README [here](https://github.com/Dhaval2404/ImagePicker)!

# Changelog

## Fork 1.9.1
- Removed all startForActivityResult from library since caller is responsible to provide an `ActivityResultLauncher<Intent>`
- Removed https://github.com/florent37/InlineActivityResult dependency

---

## Fork 1.9.0
- Added [Android Activity Result APIs](https://developer.android.com/training/basics/intents/result)
