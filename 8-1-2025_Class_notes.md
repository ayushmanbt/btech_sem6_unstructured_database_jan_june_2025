# Class notes for 8/1/2025

- Key value pair database - redis
    - Uses key value pair like dictionaries and hash maps
    - extremely fast cause mostly in memory
    - redis
    - localstorage in web works similar

- Document based
    - mainly two kinds of documents - JSON and XML - JSON is predominantly used for Document based database
- Javascript deep copy vs shallow copy
    - Normal copy/reference 
    ```js
    let obj1 = { name: "John", age: 30 };
    let obj2 = obj1;  // obj2 is a reference to obj1
    obj2.age = 31;
    console.log(obj1.age); // 31
    console.log(obj2.age); // 31
    ```
    - Shallow copy 
    ```js
    let obj1 = { name: "John", age: 30, address: { city: "New York" } };
    let obj2 = Object.assign({}, obj1);  // Shallow copy

    obj2.age = 31;
    obj2.address.city = "Los Angeles";

    console.log(obj1.age);               // 30
    console.log(obj1.address.city);      // "Los Angeles"
    console.log(obj2.age);               // 31
    console.log(obj2.address.city);      // "Los Angeles"
    ```
    - deep copy
    ```js
    let obj1 = { name: "John", age: 30, address: { city: "New York" } };
    let obj2 = JSON.parse(JSON.stringify(obj1));  // Deep copy

    obj2.age = 31;
    obj2.address.city = "San Francisco";

    console.log(obj1.age);               // 30
    console.log(obj1.address.city);      // "New York"
    console.log(obj2.age);               // 31
    console.log(obj2.address.city);      // "San Francisco"
    ```
- Discussed about syllabus