# Browser Storage Systems

Browser Storage Systems allow web applications to store data directly in a user's browser. There are three main types: Cookies, Local Storage, and Session Storage.

**Cookies** are small text files stored on the client-side, typically used to track user sessions and behavior. They are included with every HTTP request, thus affecting server performance. They can store up to 4KB of data.

**Local Storage** is a part of the Web Storage API, allowing you to save key-value pairs in a web browser with no expiration time. Data persists even when the browser is closed and reopened. Unlike cookies, local storage data is not sent with every HTTP request. It can store up to 5MB of data.

```javascript
// Setting data
localStorage.setItem('key', 'value');

// Retrieving data
var data = localStorage.getItem('key');
```

**Session Storage** is also a part of the Web Storage API but differs from local storage in that it stores data only for one session i.e., the data is lost when the browser tab is closed. It can also store up to 5MB of data.

```javascript
// Setting data
sessionStorage.setItem('sessionKey', 'sessionValue');

// Retrieving data
var sessionData = sessionStorage.getItem('sessionKey');
```

**IndexedDB** is a low-level API for client-side storage of significant amounts of structured data and for high performance searches on this data using indexes.

```javascript
// Creating or opening a database
let db;
let request = window.indexedDB.open("myDB", 1);

request.onsuccess = function(event) {
  db = request.result;
};
```

**Web SQL** is a web page API for storing data in databases that can be queried using a variant of SQL. However, it's no longer being maintained. 

These storage systems vary in their capacities, data persistence, and data accessibility. Use them judiciously based on requirements of your web application.