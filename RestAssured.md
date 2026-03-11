- RestAssured is an API/Library through which we can automate RestAPI
- we get some class & methods from RestAssured
- RestAssured by default support cucumber style of writing test cases (BDD)


framework, report


BDD -> behaviour driven development

gerkin language which have some keyword which we use in BDD

static package 

hashmap -> json -> post req 

xmlpath xpath

```
/*
given()
    content type, set cookies, add auth, add param, set headers info etc....

when()
    get, post, put, delete

then()
    validate status code, extract response, extract headers cookies & response body....

/*
```

## How many ways we can create a request body
1) HashMap
2) using org.json
3) using pojo(plain old java object) class
4) using external json file
> throughout follow one 


# Path & Query parameters 
# Cookies & headers
```
String cookie = res.getCookie();
Map<String,String> cookies = res.getCookies();

String header = res.getHeader("Content-Type");
Headers myheader = res.getHeaders();
for(Header hd: myheader)
{
   sout(hd.getName()+ "    " +hd.getValue());
}
```
# log  
```
.log().body()
.log.cookies();
.log().headers();
```
---
<img width="1222" height="711" alt="image" src="https://github.com/user-attachments/assets/94d1c6b2-65b3-4906-bcd2-8485ef7d1555" />

---

# JSON Parsing

<img width="1369" height="640" alt="image" src="https://github.com/user-attachments/assets/9819f2a2-a9eb-49fa-9976-751ef0aa34fd" />
<img width="1143" height="415" alt="image" src="https://github.com/user-attachments/assets/a891d522-8af8-47b6-bc0d-6cac6411025e" />

---

# XML Parsing

<img width="1404" height="496" alt="image" src="https://github.com/user-attachments/assets/bc621f9b-0af8-42c3-9cd1-3e1af28bd230" />

---

<img width="1359" height="471" alt="image" src="https://github.com/user-attachments/assets/c589a351-8712-4a92-929a-c50444389087" />

---

<img width="1479" height="653" alt="image" src="https://github.com/user-attachments/assets/a889f6ae-30ce-488e-89d4-4a0f915e0854" />

---

<img width="1039" height="601" alt="image" src="https://github.com/user-attachments/assets/6ddd5e96-ee93-40b5-b2ea-26269296c4cb" />

<img width="973" height="563" alt="image" src="https://github.com/user-attachments/assets/0f3fd7dd-bb11-4e7b-9a53-3f72707af73c" />

<img width="893" height="353" alt="image" src="https://github.com/user-attachments/assets/0c785fc3-e8e3-4dfd-8694-906d84168a97" />

---

# Response validation - Data
# Schema validation - type of data
















