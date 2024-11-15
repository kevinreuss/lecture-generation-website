# Client-Side Storage with IndexedDB and LocalStorage

## LocalStorage

LocalStorage is a type of web storage that allows Javascript websites and apps to store and access data right in the browser with no expiration time. This data persists even after the browser window is closed. 

Example use of localStorage:

```javascript
// Setting an item
localStorage.setItem('key', 'value');

// Getting an item
var data = localStorage.getItem('key');

// Removing an item
localStorage.removeItem('key');

// Clear all items
localStorage.clear();
```

Note: LocalStorage data is saved as strings. To store objects, you need to use `JSON.stringify()` when saving the data and `JSON.parse()` when reading the data.

## IndexedDB

IndexedDB is a low-level API for client-side storage of significant amounts of structured data, including files/blobs. It's a NoSQL storage system, where data is stored as "object stores" in "databases".

To use IndexedDB, you have to open a database, create an object store and then perform transactions.

Example use of IndexedDB:

```javascript
// Open a database
var openRequest = indexedDB.open('myDatabase', 1);

openRequest.onupgradeneeded = function(e) {
  var db = e.target.result;
  console.log('running onupgradeneeded');
  if (!db.objectStoreNames.contains('store')) {
    db.createObjectStore('store', {keyPath: 'key'});
  }
};

openRequest.onsuccess = function(e) {
  console.log('running onsuccess');
  var db = e.target.result;
  var tx = db.transaction('store', 'readwrite');
  var store = tx.objectStore('store');

  // Use the object store
  var request = store.add({key: 'key', value: 'value'});

  request.onsuccess = function(e) {
    console.log('Woot! Did it');
  };
};
```

Remember, LocalStorage is synchronous and blocking, whereas IndexedDB is asynchronous and non-blocking. Choose the right storage mechanism based on your application's needs.
