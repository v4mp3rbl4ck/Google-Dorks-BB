# Google Dorks for Bug Bounty
Lista de Google Dorks para Bug Bounty
[Pagina](https://v4mp3rbl4ck.github.io/Google-Dorks-BB/)




Gracias a https://taksec.github.io/
</p>

---


### Reconocimiento Inicial

Estos suelen tener buen retorno porque apuntan a secretos, APIs, JS, source maps, backups, IDOR y redirects.

```
site:example.com ext:js "api"
```

```
site:example.com inurl:.js.map OR ext:map
```

```
site:example.com "api_key" OR "access_token" OR "client_secret"
```

```
site:example.com ext:env OR inurl:.env
```

```
site:example.com inurl:swagger OR inurl:openapi OR intitle:"Swagger UI"
```

```
site:example.com inurl:graphql OR intitle:"GraphQL Playground"
```

```
site:example.com intitle:"index of" "backup"
```

```
site:example.com ext:sql OR ext:db OR ext:sqlite
```

```
site:example.com inurl:redirect_uri= OR inurl:returnUrl= OR inurl:next=
```

```
site:example.com inurl:user_id= OR inurl:account_id= OR inurl:invoice_id=
```



### 1. Exposición de secretos, tokens y claves

```
site:example.com ("api_key" OR "apikey" OR "api-key" OR "access_token" OR "auth_token" OR "client_secret")
```

```
site:example.com ("AWS_ACCESS_KEY_ID" OR "AWS_SECRET_ACCESS_KEY" OR "aws_access_key_id")
```

```
site:example.com ("private_key" OR "BEGIN RSA PRIVATE KEY" OR "BEGIN OPENSSH PRIVATE KEY")
```

```
site:example.com ext:env OR ext:yml OR ext:yaml OR ext:json "secret"
```

```
site:example.com ("DB_PASSWORD" OR "DATABASE_URL" OR "MYSQL_ROOT_PASSWORD" OR "POSTGRES_PASSWORD")
```



### 2. Archivos de configuración sensibles

```
site:example.com ext:env OR ext:config OR ext:conf OR ext:ini OR ext:properties
```

```
site:example.com inurl:.env OR inurl:config OR inurl:settings OR inurl:credentials
```

```
site:example.com "APP_KEY" OR "APP_SECRET" OR "SECRET_KEY" OR "JWT_SECRET"
```

```
site:example.com "spring.datasource.password" OR "spring.datasource.username"
```

```
site:example.com "connectionString" OR "connection_string" OR "jdbc:mysql"
```



### 3. Backups y copias olvidadas

```
site:example.com ext:bak OR ext:backup OR ext:old OR ext:orig OR ext:save OR ext:tmp
```

```
site:example.com inurl:backup OR inurl:backups OR inurl:dump OR inurl:old OR inurl:archive
```

```
site:example.com ext:zip OR ext:tar OR ext:gz OR ext:7z OR ext:rar
```

```
site:example.com "index of" "backup"
```

```
site:example.com "database dump" OR "sql dump" OR "db_backup"
```



### 4. SQL dumps y bases de datos expuestas

```
site:example.com ext:sql OR ext:db OR ext:sqlite OR ext:mdb
```

```
site:example.com "INSERT INTO" "VALUES" ext:sql
```

```
site:example.com "phpMyAdmin" OR "Adminer" OR "Mongo Express"
```

```
site:example.com inurl:phpmyadmin OR inurl:adminer OR inurl:dbadmin
```

```
site:example.com "MySQL dump" OR "PostgreSQL database dump"
```



### 5. Paneles de administración

```
site:example.com inurl:admin OR inurl:administrator OR inurl:cpanel OR inurl:dashboard
```

```
site:example.com intitle:"admin panel" OR intitle:"dashboard" OR intitle:"control panel"
```

```
site:example.com inurl:manage OR inurl:management OR inurl:console
```

```
site:example.com inurl:wp-admin OR inurl:wp-login.php
```

```
site:example.com inurl:login "admin"
```



### 6. API discovery

```
site:example.com inurl:/api/ OR inurl:/v1/ OR inurl:/v2/ OR inurl:/v3/
```

```
site:example.com inurl:graphql OR inurl:graphiql OR inurl:playground
```

```
site:example.com inurl:swagger OR inurl:openapi OR inurl:api-docs OR inurl:redoc
```

```
site:example.com ext:json "swagger" OR "openapi"
```

```
site:example.com "apiKey" OR "x-api-key" OR "bearer"
```



### 7. GraphQL expuesto

```
site:example.com inurl:graphql
```

```
site:example.com inurl:graphiql OR inurl:graphql-playground
```

```
site:example.com intitle:"GraphQL Playground" OR intitle:"GraphiQL"
```

```
site:example.com "query {" "mutation"
```

```
site:example.com "GraphQL endpoint"
```



### 8. Swagger / OpenAPI mal expuesto

```
site:example.com intitle:"Swagger UI"
```

```
site:example.com inurl:swagger.json OR inurl:openapi.json OR inurl:api-docs
```

```
site:example.com ext:json "paths" "components" "securitySchemes"
```

```
site:example.com "swagger: " "basePath"
```

```
site:example.com "openapi: 3.0" OR "openapi: 3.1"
```



### 9. Parámetros para IDOR / Broken Access Control

```
site:example.com inurl:user_id= OR inurl:userid= OR inurl:uid=
```

```
site:example.com inurl:account_id= OR inurl:account= OR inurl:customer_id=
```

```
site:example.com inurl:order_id= OR inurl:invoice_id= OR inurl:document_id=
```

```
site:example.com inurl:profile= OR inurl:member= OR inurl:client=
```

```
site:example.com inurl:id= inurl:view
```



### 10. Parámetros para Open Redirect

```
site:example.com inurl:continue= OR inurl:returnUrl= OR inurl:return_url=
```

```
site:example.com inurl:callback= OR inurl:callback_url= OR inurl:redirect_uri=
```

```
site:example.com inurl:destination= OR inurl:dest= OR inurl:goto=
```

```
site:example.com inurl:next= inurl:http
```

```
site:example.com inurl:url= inurl:https
```



### 11. Parámetros para SSRF

```
site:example.com inurl:url= OR inurl:uri= OR inurl:path=
```

```
site:example.com inurl:webhook= OR inurl:webhook_url= OR inurl:callback=
```

```
site:example.com inurl:feed= OR inurl:rss= OR inurl:import=
```

```
site:example.com inurl:image_url= OR inurl:file_url= OR inurl:avatar_url=
```

```
site:example.com inurl:proxy= OR inurl:fetch= OR inurl:load=
```



### 12. Parámetros para LFI / Path Traversal

```
site:example.com inurl:file= OR inurl:filename= OR inurl:filepath=
```

```
site:example.com inurl:template= OR inurl:page= OR inurl:view=
```

```
site:example.com inurl:download= OR inurl:doc= OR inurl:document=
```

```
site:example.com inurl:path= OR inurl:folder= OR inurl:dir=
```

```
site:example.com inurl:include= OR inurl:require=
```



### 13. Parámetros para XSS

```
site:example.com inurl:search= OR inurl:q= OR inurl:s=
```

```
site:example.com inurl:query= OR inurl:keyword= OR inurl:term=
```

```
site:example.com inurl:message= OR inurl:comment= OR inurl:content=
```

```
site:example.com inurl:return= OR inurl:error= OR inurl:debug=
```

```
site:example.com inurl:lang= OR inurl:locale= OR inurl:redirect=
```



### 14. Parámetros para SQLi

```
site:example.com inurl:id= OR inurl:pid= OR inurl:product_id=
```

```
site:example.com inurl:category_id= OR inurl:cat_id= OR inurl:item_id=
```

```
site:example.com inurl:sort= OR inurl:order= OR inurl:filter=
```

```
site:example.com inurl:page= OR inurl:limit= OR inurl:offset=
```

```
site:example.com inurl:search= inurl:id=
```



### 15. Upload endpoints

```
site:example.com inurl:upload OR inurl:file-upload OR inurl:media-upload
```

```
site:example.com "drag and drop" "upload"
```

```
site:example.com "choose file" OR "select file" OR "browse file"
```

```
site:example.com inurl:attachment OR inurl:attachments
```

```
site:example.com inurl:import "csv"
```



### 16. Documentos internos

```
site:example.com ext:pdf OR ext:doc OR ext:docx OR ext:xls OR ext:xlsx OR ext:ppt OR ext:pptx
```

```
site:example.com "internal use only" OR "confidential" OR "restricted"
```

```
site:example.com "do not distribute" OR "not for public release"
```

```
site:example.com "employee handbook" OR "onboarding" OR "VPN"
```

```
site:example.com "architecture diagram" OR "network diagram" OR "threat model"
```



### 17. Logs expuestos

```
site:example.com ext:log
```

```
site:example.com "stack trace" OR "exception" OR "fatal error"
```

```
site:example.com "Traceback" "File" "line"
```

```
site:example.com "PHP Warning" OR "PHP Notice" OR "PHP Fatal error"
```

```
site:example.com "DEBUG" "password"
```



### 18. Errores tecnológicos específicos

```
site:example.com "Laravel" "APP_DEBUG"
```

```
site:example.com "Symfony Exception" OR "Whoops"
```

```
site:example.com "Django" "Traceback"
```

```
site:example.com "Express error" OR "Node.js" "stack trace"
```

```
site:example.com "ASP.NET" "Server Error in"
```



### 19. Subdominios interesantes

```
site:*.example.com -www
```

```
site:*.example.com inurl:dev OR inurl:staging OR inurl:test OR inurl:qa
```

```
site:*.example.com inurl:internal OR inurl:admin OR inurl:secure
```

```
site:*.example.com intitle:"index of"
```

```
site:*.example.com "Welcome to nginx" OR "Apache2 Ubuntu Default Page"
```



### 20. Directorios listados

```
site:example.com intitle:"index of"
```

```
site:example.com intitle:"index of" "backup"
```

```
site:example.com intitle:"index of" ".env"
```

```
site:example.com intitle:"index of" "config"
```

```
site:example.com intitle:"index of" "logs"
```



### 21. Buckets y cloud storage

```
site:s3.amazonaws.com "example.com" "index of"
```

```
site:storage.googleapis.com "example.com"
```

```
site:amazonaws.com "example.com" "backup"
```

```
site:blob.core.windows.net "example.com" "confidential"
```

```
site:sharepoint.com "example.com" "internal"
```



### 22. Jira, Confluence, GitLab, Jenkins expuestos

```
site:example.com inurl:jira OR intitle:"Jira"
```

```
site:example.com inurl:confluence OR intitle:"Confluence"
```

```
site:example.com inurl:gitlab OR intitle:"GitLab"
```

```
site:example.com inurl:jenkins OR intitle:"Dashboard [Jenkins]"
```

```
site:example.com inurl:bitbucket OR intitle:"Bitbucket"
```



### 23. CI/CD y artefactos

```
site:example.com inurl:.gitlab-ci.yml OR inurl:Jenkinsfile
```

```
site:example.com ext:yml OR ext:yaml "pipeline"
```

```
site:example.com "CI_JOB_TOKEN" OR "GITHUB_TOKEN" OR "GITLAB_TOKEN"
```

```
site:example.com "docker-compose.yml" OR "Dockerfile"
```

```
site:example.com "registry" "password"
```



### 24. Git expuesto

```
site:example.com inurl:.git
```

```
site:example.com intitle:"index of" ".git"
```

```
site:example.com inurl:.git/config
```

```
site:example.com "gitlab-ci" "password"
```

```
site:example.com ".git-credentials"
```



### 25. WordPress

```
site:example.com inurl:wp-content
```

```
site:example.com inurl:wp-admin OR inurl:wp-login.php
```

```
site:example.com inurl:wp-content/uploads
```

```
site:example.com inurl:wp-json/wp/v2/users
```

```
site:example.com "Powered by WordPress"
```



### 26. Adobe Experience Manager AEM

```
site:example.com inurl:/system/console
```

```
site:example.com inurl:/crx/packmgr
```

```
site:example.com inurl:/libs/cq
```

```
site:example.com inurl:/content/dam ext:json
```

```
site:example.com inurl:/bin/querybuilder.json
```



### 27. Firebase

```
site:firebaseio.com "example.com"
```

```
site:firebaseapp.com "example.com"
```

```
site:example.com "firebaseConfig"
```

```
site:example.com "firebaseio.com" "authDomain"
```

```
site:example.com "storageBucket" "firebase"
```



### 28. CORS / OAuth / SSO candidates

```
site:example.com inurl:oauth OR inurl:sso OR inurl:saml
```

```
site:example.com inurl:redirect_uri= OR inurl:client_id=
```

```
site:example.com inurl:authorize OR inurl:token
```

```
site:example.com "client_id" "redirect_uri"
```

```
site:example.com "SAMLRequest" OR "SAMLResponse"
```



### 29. Parámetros de pago / compras

```
site:example.com inurl:checkout OR inurl:payment OR inurl:billing
```

```
site:example.com inurl:invoice OR inurl:receipt OR inurl:order
```

```
site:example.com inurl:coupon OR inurl:discount OR inurl:promo
```

```
site:example.com inurl:price= OR inurl:amount= OR inurl:total=
```

```
site:example.com inurl:plan= OR inurl:subscription=
```



### 30. Parámetros de PII

```
site:example.com inurl:email= OR inurl:phone= OR inurl:address=
```

```
site:example.com inurl:ssn= OR inurl:dob= OR inurl:birthdate=
```

```
site:example.com inurl:first_name= OR inurl:last_name=
```

```
site:example.com inurl:customer= OR inurl:client= OR inurl:user=
```

```
site:example.com ext:xls OR ext:xlsx "email" "phone"
```



### 31. Archivos JavaScript

```
site:example.com ext:js
```

```
site:example.com ext:js "api"
```

```
site:example.com ext:js "token" OR "secret" OR "key"
```

```
site:example.com ext:js "baseURL" OR "baseUrl" OR "apiUrl"
```

```
site:example.com ext:js "sentry" OR "bugsnag" OR "datadog"
```



### 32. Source maps

```
site:example.com ext:map
```

```
site:example.com inurl:.js.map
```

```
site:example.com ext:map "sourcesContent"
```

```
site:example.com ext:map "webpack"
```

```
site:example.com inurl:main.js.map OR inurl:app.js.map
```



### 33. Documentación interna o técnica

```
site:example.com "runbook" OR "playbook"
```

```
site:example.com "postmortem" OR "incident report"
```

```
site:example.com "API documentation" OR "developer guide"
```

```
site:example.com "staging environment" OR "test environment"
```

```
site:example.com "VPN" "username"
```



### 34. Dorks externos útiles

Estos no van contra `site:example.com`, sino contra plataformas de terceros donde puede aparecer información relacionada con el objetivo.

```
site:github.com "example.com" "password"
```

```
site:github.com "example.com" "api_key"
```

```
site:gitlab.com "example.com" "secret"
```

```
site:pastebin.com "example.com" "token"
```

```
site:trello.com "example.com"
```

```
site:notion.site "example.com"
```

```
site:atlassian.net "example.com"
```

```
site:herokuapp.com "example.com"
```

```
site:vercel.app "example.com"
```

```
site:netlify.app "example.com"
```
---




Top Parameters:
https://github.com/lutfumertceylan/top25-parameter

Proviesec dorks:
https://github.com/Proviesec/google-dorks
