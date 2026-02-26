

---

JSON - Java Script Object notation

Client can send txt,XL, pdf(high weighted, no encryption) -> Convert to JSON(weighted, encryption)

# What is JSON?
- JSON – Java Script Object Notation
- JSON is a syntax for storing and exchanging data.
- Basically it was designed for human-readable data interchange.
- JSON is text, written with Java Script Object Notation.
- It has been extended from the JavaScript scripting language
- The filename extension is .json
- JSON internet Media type is application/json

## JSON Data Types {only for values}
- Number - `{ "age":30 }`
- String - `{ "name":"John" }`
- Boolean - `{ "sale":true }`
- Null - `{ "middlename":null }`
- Object - `{"employee":{ "name":"John", "age":30, "city":"New York" }}`
- Array - `{"employees":["John","Anna","Peter"]}`

---

  ## JSON vs XML
| Feature           | JSON                                         | XML                                                     |
| ----------------- | -------------------------------------------- | ------------------------------------------------------- |
| Full Form         | JavaScript Object Notation                   | eXtensible Markup Language                              |
| Syntax Style      | Key–value pairs                              | Tag-based markup                                        |
| Readability       | Easy and human-readable                      | More verbose, less readable                             |
| Data Structure    | Supports objects and arrays directly         | No native array type (uses repeated tags)               |
| Data Size         | Lightweight (smaller files)                  | Heavier due to extra tags                               |
| Parsing Speed     | Faster to parse                              | Slower compared to JSON                                 |
| Data Types        | string, number, boolean, null, object, array | Text-based but can define complex structures via schema |
| Use in APIs       | Very common in REST APIs                     | Common in SOAP and legacy systems                       |
| Comments Support  | Not allowed                                  | Allowed                                                 |
| Schema Validation | JSON Schema                                  | XML Schema (XSD)                                        |
| Example Style     | `{ "name":"John" }`                          | `<name>John</name>`                                     |
| Support           | Test & Number                                | text, number,image,charts, graph etc                    |

Assertion in Postman is done by pm postman library which have functions for validations  

## Response Validations (Adding Tests)
- Status code
- Headers
- Cookies
- Response time
- Response body ( json/xml )
- size data

in java we have JUnit but in javaScript we have chai, mocka frameWork use by Postman for organising the test cases
## Chai Assertion Library
```java
// Normal function
pm.test("Test Name", function()
{
    // assertion;
});
```
```java
// Arrow function
pm.test("Test Name", () =>
{
    // assertion;
});
```

# Testing status codes
> Test for the response status code:
```java
pm.test("Status code is 200", () => {
    pm.response.to.have.status(200);
});

// If you want to test for the status code being one of a set, include them all in an array and use oneOf
pm.test("Successful POST request", () => {
    pm.expect(pm.response.code).to.be.oneOf([201,202]);
});

// Check the status code text:
pm.test("Status code name has string", () => {
    pm.response.to.have.status("Created");
});
```

# Testing headers
```java
//Check that a response header is present:
pm.test("Content-Type header is present", () => {
    pm.response.to.have.header("Content-Type");
});

//Test for a response header having a particular value:
pm.test("Content-Type header is application/json", () => {
    pm.expect(pm.response.headers.get('Content-Type'))
      .to.eql('application/json; charset=utf-8');
});
```

# Testing cookies
```java
//Test if a cookie is present in the response:
pm.test("Cookie 'language' is present", () => {
    pm.expect(pm.cookies.has('language')).to.be.true;
});

//Test for a particular cookie value:
pm.test("Cookie language has value 1", () => {
    pm.expect(pm.cookies.get('language')).to.eql('en-gb');
});

//Testing response times
//Test for the response time to be within a specified range:
pm.test("Response time is less than 200ms", () => {
    pm.expect(pm.response.responseTime).to.be.below(200);
});
```

# Asserting a value type
> Test the type of any part of the response:
```javaScript 
{
  "id": 1,
  "name": "John",
  "location": "india",
  "phone": "1234567890",
  "courses": [
    "Java",
    "Selenium"
  ]
}
const jsonData = pm.response.json();

pm.test("Test data type of the response", () => {
    pm.expect(jsonData).to.be.an("object");
    pm.expect(jsonData.name).to.be.a("string");
    pm.expect(jsonData.id).to.be.a("number");
    pm.expect(jsonData.courses).to.be.an("array");
});
```

# Asserting array properties
> Check if an array is empty and if it contains particular items:
```javaScript
{
  "id": 1,
  "name": "John",
  "location": "india",
  "phone": "1234567890",
  "courses": [
    "Java",
    "Selenium"
  ]
}
pm.test("Test array properties", () => {
    // courses includes "Java"
    pm.expect(jsonData.courses).to.include("Java");

    // courses array must include all listed
    pm.expect(jsonData.courses)
      .to.have.members(["Java", "Selenium"]);
});
```

# Validating JSON fields in Response
```javaScript
{
  "id": 1,
  "name": "John",
  "location": "india",
  "phone": "1234567890",
  "courses": [
    "Java",
    "Selenium"
  ]
}
pm.test("value of location field is India", () => {
    var jsonData = pm.response.json();

    pm.expect(jsonData.id).to.eql(1);
    pm.expect(jsonData.name).to.eql("John");
    pm.expect(jsonData.location).to.eql("india");
    pm.expect(jsonData.phone).to.eql("1234567890");
    pm.expect(jsonData.courses[0]).to.eql("Java");
    pm.expect(jsonData.courses[1]).to.eql("Selenium");
});
```
# Validating JSON Schema
## Response
```javaScript
{
  "id": 1,
  "name": "John",
  "location": "india",
  "phone": "1234567890",
  "courses": [
    "Java",
    "Selenium"
  ]
}
```
## JSON schema
```javaScript
var schema = {
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "properties": {
    "id": {
      "type": "integer"
    },
    "name": {
      "type": "string"
    },
    "location": {
      "type": "string"
    },
    "phone": {
      "type": "string"
    },
    "courses": {
      "type": "array",
      "items": [
        { "type": "string" },
        { "type": "string" }
      ]
    }
  },
  "required": [
    "id",
    "name",
    "location",
    "phone",
    "course"
  ]
};
```

# JSON schema Validation
```javaScript
pm.test('Schema is valid', function() {
    pm.expect(tv4.validate(jsonData, schema)).to.be.true;
});
```





