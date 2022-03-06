# Microservice Product

### Endpoints:

#### Save Product

````
POST /api/product HTTP/1.1
Host: localhost:3334
Authorization: Basic base64(username:password)
Content-Type: application/json
Content-Length: 42

{
    "name": "test-1",
    "price": 1.2
}
````

#### Get Products

```
GET /api/product HTTP/1.1
Host: localhost:3334
Authorization: Basic base64(username:password)
```

#### Delete Product

```
DELETE /api/product/{productId} HTTP/1.1
Host: localhost:3334
Authorization: Basic base64(username:password)
```


#### Heroku deployu için 3 dosya oluşturulmasına ihtiyaç vardır.
```
1. Procfile build jarlarını nereden alacak vs.
2. app.json proje deploy name ve build türü
3. system.properties --> java sürümü
```

#### Spring Boot 2.5.X plain.jar Problemi
```
Spring boot olarak version2.5 ve üzeri kullanıyorsanız. Bu durumda gradle build; executable jar ve plain jar üretir.

Eğer gradle tasklarından assemble'ı çağırırısanız (./gradlew assemble). libs/build altında bir tane executable.jar bir tane de plain jar göreceksiniz.



Executable.jar: classlar + tüm kütüphaneleri içerir yani bizim kuullanmamız gereken fat jardır.

plain.jar: classlar içerir. Bizim buna ihtiyacımız yoktur...



Procfile'da "build/libs/*.jar" jar'la biten herhangi bir dosyayı al diyoruz. Bu durumda elimizde iki tane jar dosyası olacağı için heroku'da hata ile karşılarız.



Çözüm:

Bunu engellemek için build.gradle'a şunu eklememiz gerekir:

jar {    
enabled = false
}


repositories'in altına ekleyebilirsiniz:

repositories {

    mavenCentral()

}

jar {    
enabled = false
}
dependencies {

...

```


#### Projeyi git e yollama

```
    1- git init
    2- git add -all
       git add .
       git add <specific-file>
    3- relate --> git remote add origin <remote-url>
    4- git commit -m "commit-message"
    5- git push -u origin <local-branch>      
```