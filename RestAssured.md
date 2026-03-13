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

<img width="534" height="402" alt="image" src="https://github.com/user-attachments/assets/6781b648-efd2-404e-a59a-901d80076760" />

2) using org.json

<img width="604" height="453" alt="image" src="https://github.com/user-attachments/assets/f17d1d6f-f2a2-4804-bc76-06f684db259f" />

3) using pojo(plain old java object) class

<img width="642" height="455" alt="image" src="https://github.com/user-attachments/assets/ae86ef07-d0ff-4b2b-9aa9-226fb0896d8b" />

4) using external json file
> throughout follow one 

{gson}

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

- Response validation - Data
- Schema validation - type of data

- Json Response(.json) -> Json schema(.json)
- XML Response(.XML) -> xml schema(.xsd)

<img width="1353" height="381" alt="image" src="https://github.com/user-attachments/assets/22d18661-27c3-43a8-85dd-b7558af64752" />

<img width="1190" height="380" alt="image" src="https://github.com/user-attachments/assets/80dcdbc4-485e-4c91-b54c-7d0a5fb9fc36" />


- postman only support JSON validataion schema (directly)
> import com.fasterxml.jackson.databind.ObjectMapper;
# Serialization - pojo(high weigth & less secure) ---> json
<img width="1164" height="448" alt="image" src="https://github.com/user-attachments/assets/e454d77e-f416-4373-83ee-bb050406de59" />

# De-serilization - json ---> pojo
<img width="837" height="437" alt="image" src="https://github.com/user-attachments/assets/87971618-f407-4740-b374-f468f3db10c6" />

# Authorizations 
- Basic

  <img width="877" height="464" alt="image" src="https://github.com/user-attachments/assets/942fcdf6-d1cf-4f68-a946-1c1b35a87483" />
  
- Digest

<img width="690" height="405" alt="image" src="https://github.com/user-attachments/assets/3778484a-5a5d-4fe7-8215-07391f866769" />

- Preemtpive

<img width="901" height="468" alt="image" src="https://github.com/user-attachments/assets/f67e28e6-06fd-4db2-b345-d8566dd5f9e0" />

- Bearer token

<img width="948" height="467" alt="image" src="https://github.com/user-attachments/assets/5419d844-69e3-4eda-9155-b2263d17f1d1" />

- oauth 1.0, 2.0

<img width="1203" height="346" alt="image" src="https://github.com/user-attachments/assets/115f6dc5-d28d-4906-89a9-7286e8b5c950" />
> 32:00
<img width="1000" height="316" alt="image" src="https://github.com/user-attachments/assets/ee772d5c-72ea-4403-a7e4-9594fc627371" />

- API key
- 
<img width="1297" height="354" alt="image" src="https://github.com/user-attachments/assets/3c125a4d-7412-4e78-a558-17f55e41324f" />

# Faker library
- JSON Object - {}
- JSON Array - []
- JSON Element - can be Object or Array
 
<img width="518" height="80" alt="image" src="https://github.com/user-attachments/assets/1ecbef76-219c-4f46-9026-94eda4054139" />

- practice of extracting

# Chaining
ITestContext context - pass as argument 
- context.setAttribute("user_id",id) // test level
- context.getSuite().setAttribute("user_id",id) // suite level

---

# FrameWork
- What, How, Folder Structure,useability is objective of designing framework
- Every automation tool 
- diff URLs, end points. pojo, test cases, reports so many things we need to import
  
 # Objective
 - Re-usuability
 - Maintainability
 - Readability

## Hybrid Driven - combination of data driven & modular driven

# Phases
1. understanding requirement (what kind of urls we have, req, res)
   - Functional specifications (static) {start preparing test cases}
   - Swagger ( format  of req, res)
2. Choose automation tool {librarys}
   - RestAssured Library
3. Design
   - What kind of folder structure is there
   - what kind of files we need to create.
4. Developement
5. Execution + CI






















