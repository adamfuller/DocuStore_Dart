# DocuStore in Dart v0.0.1

An easy to use API for accessing data stored on a DocuStore instance.

## How to install
Add the following to **`pubspec.yaml`**
```yaml
dependencies:
  docustore:
    git:
      url: git://github.com/adamfuller/docustore_dart.git
      ref: 0.0.1
```

If using Android, add the Internet permissions to android/app/src/main/AndroidManifest.xml
```xml
<uses-permission android:name="android.permission.INTERNET"/>
```


## How to use

Import the DocuStore package
```dart
import 'package:docustore/docustore.dart' as ds;
```

Initialize the address and port to the DocuStore Server instance, then make calls to storeEntry, getEntry, getEntries, and deleteEntry.

```dart
// Set the server address, port, and desired timeout(optional)
ds.init(
  server: "www.example.com",
  port: 1234,
  timeout: Duration(seconds: 3),
);

// Sets the entry test_id in collection test_collection to a value of 'value'.
if (await ds.setEntry("test_id", "test_collection", "value")){
  print("Entry set");
}

// Get the entry test_id in collection test_collection.
String entry = await ds.getEntry("test_id", "test_collection");

// Create a new entry in the same collection with a value of 'value_2'.
await ds.setEntry("test_id_2", "test_collection", "value_2");

// Retrieve all entries in the collection.
List<String> allEntries = await ds.getEntries("test_collection");

// Remove the entry test_id in collection test_collection.
if (await ds.deleteEntry("test_id", "test_collection")){
  print("Entry ($entry) deleted");
}

```
