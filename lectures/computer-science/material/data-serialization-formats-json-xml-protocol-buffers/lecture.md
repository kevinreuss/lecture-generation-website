# Data Serialization Formats: JSON, XML, Protocol Buffers

## JSON (JavaScript Object Notation)

JSON is a lightweight, text-based format that is easy to read and write. It represents data structures using syntax from JavaScript. 

Here's a simple JSON example:

```json
{
  "name": "John Doe",
  "age": 30,
  "isStudent": false
}
```

Arrays and nested objects can also be represented:

```json
{
  "name": "John Doe",
  "age": 30,
  "skills": ["Java", "Python"],
  "address": {
    "street": "123 Main St",
    "city": "Anytown"
  }
}
```

## XML (eXtensible Markup Language)

XML is more verbose than JSON and uses a tag-based syntax. It's self-descriptive and supports complex data structures, but can be harder to parse.

Here's the equivalent XML:

```xml
<person>
  <name>John Doe</name>
  <age>30</age>
  <isStudent>false</isStudent>
  <skills>
    <skill>Java</skill>
    <skill>Python</skill>
  </skills>
  <address>
    <street>123 Main St</street>
    <city>Anytown</city>
  </address>
</person>
```

## Protocol Buffers

Protocol Buffers (protobuf) is a binary serialization format developed by Google. It's more efficient and faster than JSON/XML, but less readable.

First, you define your data structures in `.proto` files:

```protobuf
message Person {
  string name = 1;
  int32 age = 2;
  bool isStudent = 3;

  message Address {
    string street = 1;
    string city = 2;
  }
  Address address = 4;

  repeated string skills = 5;
}
```

Then, you compile these into code (Java, Python, etc.), which you use to serialize/deserialize data:

```python
person = Person(name="John Doe", age=30, isStudent=False, address=Person.Address(street="123 Main St", city="Anytown"), skills=["Java", "Python"])
serialized_data = person.SerializeToString()
```

Each format has its pros and cons. JSON/XML is human-readable and widely supported, but verbose and slower. Protobuf is fast and efficient, but requires a schema and isn't directly readable.