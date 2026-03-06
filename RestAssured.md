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























