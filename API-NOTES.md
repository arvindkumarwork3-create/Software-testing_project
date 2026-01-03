API-way of communication between two app and may different term of tech or platform.



CLIENT-computer hardware device or software access the service made available in server.



server-run service to serve needs of other computer depending on service running file server, database, webserver.



types of api: soap, rest both web services



api vs webservice:

 1.web service is an API wrapped HTTP

 2.All web services are api but api are not web services.

  3.web service need network but API not required.







rest API HTTP Metho



request-->api-->response  using method like put, post, get, delete.





Payload: body in http req and res message



http req: URL, header, payload(json, xml)

http res: status code, response payload, string message



get-->LINK--> validation: status code, time, size data, response body, cookies, headers.



post-->link-->body, raw, json send--save.





2XX

200-ok,

201-created,

202-Accepted,

203-non authoritative info,

204-no content



4xx

400-bad req,

401-unauthorize,

403:forbidden,

404:notfound,

409:conflict.



5xx

500:internal server error,

501:not implemented,

502:bad gateway,

503:service unavailable,

504:gateway timeout,

599-network timeout.



after set node js-npm

check pc->properties-->settings-->advance settings-->environment variables-->path variable.





verify whether json server installed: **npm install-g json-server**



**JSON content file take and use-- open cmd prompt :**

**path**

**c:\\autopractise\\jsonfile\\** json-server (filename).json.



JSON-Simple read, light weight, support array, human readable, carries text and number.



XML-less compare to json, no array support, less human read, many data type support like chart, graph, image, number etc.



json object: hold key: value

key-represent string and value any data type.{-json object.



json object with string, number, Boolean, nested obj



json array of strings, numbers, Boolean, objects.



example:

"student":\[

{

"id":01

"name":"Arvind"

 "grade": "b"

}

{

"id":02

"name": "Pavithra"

 "grade": "a"

}

]}



sample: x. student\[1].grade=>path



Ans: {"grade: "B"}



Assertions: cmd use to check response validation

 (status code, header, cookies, response time, response body)



**Testing status code:**



pm. test("status",()=>

{

pm. response. to. have. status(200);

});



**Testing status text:**



pm. test("status",()=>

{

pm. response. to. have. status("created");

});



**Include all in one of:**



pm. test("success post request ",()=>

{

pm. expect (pm. response.code).to .be.one of (\[200,201]);

});





**HEADER**



**Testing status headers response present:**



pm. test("content header present",()=>

{

pm. response. code.to. have("content-type");

});



**Testing status headers have particular value:**

pm. test("content header applicable",()=>

{

pm. expect (pm. response. header. get('content-type')).to. eql('application/json; charset=utf-8');

});





**cookies**



**response \& value**



pm. test("cookie 'lang' is present",()=>

{

pm. expect (pm. cookies. has('lang').to.be. true;

});



pm. test("cookie 'lang' has value",()=>

{

pm. expect (pm. cookies. get('lang').to. eql('en- gb);

});



**Response time**

pm. test("response time ",()=>

{

pm. expect (pm. response. code).to.be. below(200);

});





**Response BODY**



**{"ID":1,**

**"NAME":arvi,**

**"call":99321,**

**"course":\["java,"c#"]**

**}**



***data type:***



**const json date=pm. response. json();**

**pm. test("test data response",()=>**

**{**

**1)*data type:***

pm. expect(jsondata).to.be.an("object");

pm. expect(jsondata.name).to. be. a("string");

pm. expect(jsondata.call).to. be. a("number");

pm. expect(jsondata.courses).to. be.an("array");



**2)*array type:***

pm. expect(jsondata. course).to. include("java");

pm. expect(jsondata. course).to.have. member(\["java", "c#");



*3)json field response:*\*\*

pm. expect(jsondata. courses).to. be. eql("java");

pm. expect(jsondata. call).to. be. eql(99321);



***3)json schema validation: Afterchecking  in jsonschema tool content paste in test and validate***



pm. expect(tv4.validate(jsondata. schema).to. be. true;



**});**





**pre-request script=> used to pre before testing**



collection pre, folder pre, request pre->req->res->collection test , folder test , request test.





scope:global,collection,environment,local,data



\*\*Global-\*\*access worspace

collection-access witin collection

environment-access in all collection but switch to

local-access only witin req.



**use pre-script create global,collection,environment,local**



Local: pm.variable.set("url\_local","http://req.in");

Global: pm.global.set("user\_id","2");

Environament:pm.environment.set("user\_qa\_id","2");

collection:pm.collection.set("user\_collect","2");





**delete**

Global: pm.globals.unset("userid\_global");

Environment:pm.globals.unset("userid\_Environment");

Collection:pm.globals.unset("userid\_Collection");



**Restore**

console.log(pm.globals.get("userid\_global"));

console.log(pm.Environment.get("userid\_Environment"));

console.log(pm.Collection.get("userid\_Collection"));

console.log(pm.variable.get("userid\_local"));



**Chaining**

**Json body load in post creation**

**{"ID":1,**

**"NAME":arvi,**

**"call":99321,**

**"course":\["java,"c#"]**

**}**



**capture in test**

var jsondata=json.parse(responsebody)

pm.environment.set("id",jsondata.id);



get:http//:localhost:3000/student{{id}}

delete:http//:localhost:3000/student{{id}}



run collection with 1 iteration and result verified.







**Api token and run the collection**



normal method not accept need to genearate token



collection --> apply token



now,



**random input set in postman**



**pre req**



var random=math.random().tostring(36).substring(2);



var useremail="arvi"+random+"@gmail.com";

var username="ar"+random;



pm.environment.set("email\_envi",useremail);

pm.environment.set("name\_envi",userename);



**body**

{

"name":"{{name\_envi}}",

"email":"{{email\_envi}}",

"status":"inactive"

}



created postman 200 successfull



now capture id to verify in get,put,delete



test

var jsondata=json.parse(responsebody);

pm.environment.set("id\_envi",jsondata.id);



**get**



now,give set link withuserid:

http://go/public/v2/user/{{id\_envi}}



test



//validating field response



pm.test("value of j field",()=>



{

var jsondata=pm.response.json();



pm.expect(jsondata.id).to.eql(pm.environment.get("id\_envi");

pm.expect(jsondata.name).to.eql(pm.environment.get("name\_envi");

pm.expect(jsondata.email).to.eql(pm.environment.get("email\_envi");

});



**put** use random in pre-req and change the section as active and **delete** by capturing env id use



pm.environment.unset("id\_envi");

pm.environment.unset("name\_envi");

pm.environment.unset("email\_envi");



**Data driven testing**

prepare sheet with listed bookid \& customer name

**post** -->.apply link-->use random method "{{bookid}}","{{customer name}}"



test

check response and capture orderid in envi level



**get**-->link{{order\_envi}}

and check whether orderid  is eql



pm.test("checkid",()=>

{

var jsondata=pm.response.json();

pm.expect(jsondata.id).to.eql.(pm.environment.get("orderid\_envi");

}



delete ->using id with unset format in test level and also check response 204



run the collection and iteration set delay set,and load the data:prepared sheet data file type:test/csv



**Server upload files**

Install jar file to provide API

cMD-->c:\\Automate\\user/java-jar file-upload-RestApi.jar.





Upload file in postman

http://localhost:8080/upload

http://localhost:8080/uploadmultiplefiles



**single-file**



Create collection-->fileupload-->post single-->apply link(http://localhost:8080/upload)-->body

formdate-->key:file and value:text.txt(uploadfile) send save



**multiple file**

Create collection-->fileupload-->post single-->apply link(http://localhost:8080/uploadmultiplefile)-->body

formdate-->key:file and value:2text.txt(uploadfile) send save



**Authorization**

**Api key,bearer token,basic auth,digest auth,Oauth2.0**



**basic auth**

Create collection and file name as O.auth-->get \_\_link -->Authorization-->dropdown basic auth--username,pswd



**Digest auth**

DIGEST AUTHENCRPT AND DECRYT (pswd/username)USED IN DIGEST AUTH.

&nbsp;

O.auth-->get \_\_digestauthlink -->Authorization-->dropdown digest auth--username,pswd additional information(realm,nonce,algorithm,qop,nonce count)



**Bearer token**

Ex: using Github-->dev setting-->personal access token-->provide info-->generate token-->copy token generated.



O.auth-->get \_\_bearertokenlink -->Authorization-->dropdown bearertoken--paste copied token and send save look body



**APi key**

**get free api in weather report**

O.auth-->get \_\_apikeynlink -->Authorization-->dropdown API key--key:appid,value:paste copied apikey and addto:query parm and send save look body



OAUTH

LOGIN GITHUD--PROFILE--SETTING--DEV SET--CREATE NEW GIT--(OAUTHAPP) REGISTER NEW APP- COPY url and callback url, client id,client secret key by generate.



go to postman



get--link apply --parmeter clientid as key and value as id and callback code=code redirect back to site github



parma-client id,secret,code look body to access token and link take from here with parm adding



now auth --o.auth --access token apply and config option--body process it.





**SWAGGER INTERATIVE DOC**



CREATE collection--get --apply link

if curl link provided overall --import--raw text--apply curl link--continue--select file to import--name full link and format-curl-import as request--import and same as for post extract curl text and apply link save send check result in body.





Sample-1

Create a collection petstore



post --link

body-raw-json

{

"id":{{id}},

"name":"{{name}}",

"first":"{{firstname}}",

"lastname":"{{lastname}}",

"password":"{{password}}",

"phone":"{{phone}}",

"email":{{email}}

}



pre-req

const.randomnum=math.floor(math.random()\*100+1));

var randomstr="john"+math.random().tostring(36).substring(2);



pm.environment.set("id",randomnum);

pm.collectionvar.set("name",randomstr);

pm.collectionvar.set("first",randomstr);

pm.collectionvar.set("lastname",randomstr);

pm.collectionvar.set("password",randomstr);

pm.collectionvar.set("phone",1111111);

pm.collectionvar.set("email",randomstr+@gmail.com)





console.log(randomnum);



test

pm.test("status code",funstion(){

pm.response.to.have .status(200);

}





GET

test(DOUBT)

pm.test("status code",funstion(){

pm.response.to.have .status(200);

}

LINK:HTTPS:BHFBH/FNG/{{FIRSTNAME}}



PUT

PRE-REQ

var randomstr="john"+math.random().tostring(36).substring(2);



//UPDATE

pm.collectionvar.set("phone","222222222");



LINK:HTTPS:BHFBH/FNG/{{FIRSTNAME}}



{

"id":{{id}},

"name":"{{name}}",

"first":"{{firstname}}",

"lastname":"{{lastname}}",

"password":"{{password}}",

"phone":"{{phone}}",

"email":{{email}}

}

test

pm.test("status code",funstion(){

pm.response.to.have .status(200);

}



Delete

test

pm.environment.unset("id",randomnum);

pm.collectionvar.unset("name",randomstr);

pm.collectionvar.unset("first",randomstr);

pm.collectionvar.unset("lastname",randomstr);

pm.collectionvar.unset("password",randomstr);

pm.collectionvar.unset("phone",1111111);

pm.collectionvar.unset("email",randomstr+@gmail.com)



run and check result no var found





**XML CHECK**

COLLECTION AND NAME IT

POST--LINK

test

//conver xml to json

pm.test("check name",()=>{

var jsondata=xml2json(responsebody);

pm.expect(jsondata.pet.name).to.eql.("jimmy");

});



//capture id as collection var

var jsondata=xml2json(responsebody);

pm.collectionvar.set("petid",jsondata.pet.id)





Get

pm.test("check id",function(){

var jsondata=xml2json(responsebody);

pm.expect(jsondata.pet.id).to.eql(pm.collection variable.get("petid"));

});



}



put

pm.test("check id",function(){

var jsondata=xml2json(responsebody);

pm.expect(jsondata.pet.name).to.eql("tommy");

});



Delete

pm.collectioncariable.unset("petid");



run\& doc













