# springboot-ssl-authority-certificate
Enable SSL Secure Sockets Layer in springboot application using Lets Encrypt Authority Certificate

* Two files from Authority Certificate Provider like [Lets Encrypt](https://letsencrypt.org/)
* * `publickey.pem` cert1.pem
* * `privatekey.pem` privkey1.pem

* RUN `openssl pkcs12 -export -in publickey.pem -inkey privatekey.pem -name springboot -out springboot.p12`
*  Provide `Enter Export Password` and `Verifying - Enter Export Password` , this password will b used as the password
 key-store-password in application.yml in springboot project.
* As the result above command a file `springboot.p12` will be created.
* Place file `springboot.p12` at `src/main/resources/`.

### application.yml file
```
server:
  ssl:
    enabled: true  # enables https
    key-store-type: pkcs12
    key-store: classpath:springboot.p12
    key-store-password: springboot [Optional]
    key-alias: springboot
  port: 8080
```


