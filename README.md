# Google Dorks for Bug Bounty
Lista de Google Dorks para Bug Bounty
Gracias a https://taksec.github.io/

[Pagina](https://v4mp3rbl4ck.github.io/Google-Dorks-BB/)

</p>

---
# Google Dorks Mejorados para Bug Bounty

> Basado en una lista inicial de Google Dorks para Bug Bounty y ampliado con búsquedas orientadas a encontrar superficies interesantes por tipo de vulnerabilidad.

## Uso base

Reemplaza `example.com` por el dominio del programa autorizado.

```txt
site:example.com
```

Para reducir ruido:

```txt
site:example.com -www -blog -shop -careers -support
```

Para centrarte en aplicaciones:

```txt
site:example.com inurl:app OR inurl:portal OR inurl:dashboard OR inurl:account
```

Para excluir resultados poco útiles:

```txt
site:example.com -blog -news -press -careers -jobs
```

---

# Pack recomendado para añadir primero

Estos suelen tener buen retorno porque apuntan a secretos, APIs, JS, source maps, backups, IDOR y redirects.

```txt
site:example.com ext:js "api"
```

```txt
site:example.com inurl:.js.map OR ext:map
```

```txt
site:example.com "api_key" OR "access_token" OR "client_secret"
```

```txt
site:example.com ext:env OR inurl:.env
```

```txt
site:example.com inurl:swagger OR inurl:openapi OR intitle:"Swagger UI"
```

```txt
site:example.com inurl:graphql OR intitle:"GraphQL Playground"
```

```txt
site:example.com intitle:"index of" "backup"
```

```txt
site:example.com ext:sql OR ext:db OR ext:sqlite
```

```txt
site:example.com inurl:redirect_uri= OR inurl:returnUrl= OR inurl:next=
```

```txt
site:example.com inurl:user_id= OR inurl:account_id= OR inurl:invoice_id=
```

---

# 1. Exposición de secretos, tokens y claves

```txt
site:example.com ("api_key" OR "apikey" OR "api-key" OR "access_token" OR "auth_token" OR "client_secret")
```

```txt
site:example.com ("AWS_ACCESS_KEY_ID" OR "AWS_SECRET_ACCESS_KEY" OR "aws_access_key_id")
```

```txt
site:example.com ("private_key" OR "BEGIN RSA PRIVATE KEY" OR "BEGIN OPENSSH PRIVATE KEY")
```

```txt
site:example.com ext:env OR ext:yml OR ext:yaml OR ext:json "secret"
```

```txt
site:example.com ("DB_PASSWORD" OR "DATABASE_URL" OR "MYSQL_ROOT_PASSWORD" OR "POSTGRES_PASSWORD")
```

---

# 2. Archivos de configuración sensibles

```txt
site:example.com ext:env OR ext:config OR ext:conf OR ext:ini OR ext:properties
```

```txt
site:example.com inurl:.env OR inurl:config OR inurl:settings OR inurl:credentials
```

```txt
site:example.com "APP_KEY" OR "APP_SECRET" OR "SECRET_KEY" OR "JWT_SECRET"
```

```txt
site:example.com "spring.datasource.password" OR "spring.datasource.username"
```

```txt
site:example.com "connectionString" OR "connection_string" OR "jdbc:mysql"
```

---

# 3. Backups y copias olvidadas

```txt
site:example.com ext:bak OR ext:backup OR ext:old OR ext:orig OR ext:save OR ext:tmp
```

```txt
site:example.com inurl:backup OR inurl:backups OR inurl:dump OR inurl:old OR inurl:archive
```

```txt
site:example.com ext:zip OR ext:tar OR ext:gz OR ext:7z OR ext:rar
```

```txt
site:example.com "index of" "backup"
```

```txt
site:example.com "database dump" OR "sql dump" OR "db_backup"
```

---

# 4. SQL dumps y bases de datos expuestas

```txt
site:example.com ext:sql OR ext:db OR ext:sqlite OR ext:mdb
```

```txt
site:example.com "INSERT INTO" "VALUES" ext:sql
```

```txt
site:example.com "phpMyAdmin" OR "Adminer" OR "Mongo Express"
```

```txt
site:example.com inurl:phpmyadmin OR inurl:adminer OR inurl:dbadmin
```

```txt
site:example.com "MySQL dump" OR "PostgreSQL database dump"
```

---

# 5. Paneles de administración

```txt
site:example.com inurl:admin OR inurl:administrator OR inurl:cpanel OR inurl:dashboard
```

```txt
site:example.com intitle:"admin panel" OR intitle:"dashboard" OR intitle:"control panel"
```

```txt
site:example.com inurl:manage OR inurl:management OR inurl:console
```

```txt
site:example.com inurl:wp-admin OR inurl:wp-login.php
```

```txt
site:example.com inurl:login "admin"
```

---

# 6. API discovery

```txt
site:example.com inurl:/api/ OR inurl:/v1/ OR inurl:/v2/ OR inurl:/v3/
```

```txt
site:example.com inurl:graphql OR inurl:graphiql OR inurl:playground
```

```txt
site:example.com inurl:swagger OR inurl:openapi OR inurl:api-docs OR inurl:redoc
```

```txt
site:example.com ext:json "swagger" OR "openapi"
```

```txt
site:example.com "apiKey" OR "x-api-key" OR "bearer"
```

---

# 7. GraphQL expuesto

```txt
site:example.com inurl:graphql
```

```txt
site:example.com inurl:graphiql OR inurl:graphql-playground
```

```txt
site:example.com intitle:"GraphQL Playground" OR intitle:"GraphiQL"
```

```txt
site:example.com "query {" "mutation"
```

```txt
site:example.com "GraphQL endpoint"
```

---

# 8. Swagger / OpenAPI mal expuesto

```txt
site:example.com intitle:"Swagger UI"
```

```txt
site:example.com inurl:swagger.json OR inurl:openapi.json OR inurl:api-docs
```

```txt
site:example.com ext:json "paths" "components" "securitySchemes"
```

```txt
site:example.com "swagger: " "basePath"
```

```txt
site:example.com "openapi: 3.0" OR "openapi: 3.1"
```

---

# 9. Parámetros para IDOR / Broken Access Control

```txt
site:example.com inurl:user_id= OR inurl:userid= OR inurl:uid=
```

```txt
site:example.com inurl:account_id= OR inurl:account= OR inurl:customer_id=
```

```txt
site:example.com inurl:order_id= OR inurl:invoice_id= OR inurl:document_id=
```

```txt
site:example.com inurl:profile= OR inurl:member= OR inurl:client=
```

```txt
site:example.com inurl:id= inurl:view
```

---

# 10. Parámetros para Open Redirect

```txt
site:example.com inurl:continue= OR inurl:returnUrl= OR inurl:return_url=
```

```txt
site:example.com inurl:callback= OR inurl:callback_url= OR inurl:redirect_uri=
```

```txt
site:example.com inurl:destination= OR inurl:dest= OR inurl:goto=
```

```txt
site:example.com inurl:next= inurl:http
```

```txt
site:example.com inurl:url= inurl:https
```

---

# 11. Parámetros para SSRF

```txt
site:example.com inurl:url= OR inurl:uri= OR inurl:path=
```

```txt
site:example.com inurl:webhook= OR inurl:webhook_url= OR inurl:callback=
```

```txt
site:example.com inurl:feed= OR inurl:rss= OR inurl:import=
```

```txt
site:example.com inurl:image_url= OR inurl:file_url= OR inurl:avatar_url=
```

```txt
site:example.com inurl:proxy= OR inurl:fetch= OR inurl:load=
```

---

# 12. Parámetros para LFI / Path Traversal

```txt
site:example.com inurl:file= OR inurl:filename= OR inurl:filepath=
```

```txt
site:example.com inurl:template= OR inurl:page= OR inurl:view=
```

```txt
site:example.com inurl:download= OR inurl:doc= OR inurl:document=
```

```txt
site:example.com inurl:path= OR inurl:folder= OR inurl:dir=
```

```txt
site:example.com inurl:include= OR inurl:require=
```

---

# 13. Parámetros para XSS

```txt
site:example.com inurl:search= OR inurl:q= OR inurl:s=
```

```txt
site:example.com inurl:query= OR inurl:keyword= OR inurl:term=
```

```txt
site:example.com inurl:message= OR inurl:comment= OR inurl:content=
```

```txt
site:example.com inurl:return= OR inurl:error= OR inurl:debug=
```

```txt
site:example.com inurl:lang= OR inurl:locale= OR inurl:redirect=
```

---

# 14. Parámetros para SQLi

```txt
site:example.com inurl:id= OR inurl:pid= OR inurl:product_id=
```

```txt
site:example.com inurl:category_id= OR inurl:cat_id= OR inurl:item_id=
```

```txt
site:example.com inurl:sort= OR inurl:order= OR inurl:filter=
```

```txt
site:example.com inurl:page= OR inurl:limit= OR inurl:offset=
```

```txt
site:example.com inurl:search= inurl:id=
```

---

# 15. Upload endpoints

```txt
site:example.com inurl:upload OR inurl:file-upload OR inurl:media-upload
```

```txt
site:example.com "drag and drop" "upload"
```

```txt
site:example.com "choose file" OR "select file" OR "browse file"
```

```txt
site:example.com inurl:attachment OR inurl:attachments
```

```txt
site:example.com inurl:import "csv"
```

---

# 16. Documentos internos

```txt
site:example.com ext:pdf OR ext:doc OR ext:docx OR ext:xls OR ext:xlsx OR ext:ppt OR ext:pptx
```

```txt
site:example.com "internal use only" OR "confidential" OR "restricted"
```

```txt
site:example.com "do not distribute" OR "not for public release"
```

```txt
site:example.com "employee handbook" OR "onboarding" OR "VPN"
```

```txt
site:example.com "architecture diagram" OR "network diagram" OR "threat model"
```

---

# 17. Logs expuestos

```txt
site:example.com ext:log
```

```txt
site:example.com "stack trace" OR "exception" OR "fatal error"
```

```txt
site:example.com "Traceback" "File" "line"
```

```txt
site:example.com "PHP Warning" OR "PHP Notice" OR "PHP Fatal error"
```

```txt
site:example.com "DEBUG" "password"
```

---

# 18. Errores tecnológicos específicos

```txt
site:example.com "Laravel" "APP_DEBUG"
```

```txt
site:example.com "Symfony Exception" OR "Whoops"
```

```txt
site:example.com "Django" "Traceback"
```

```txt
site:example.com "Express error" OR "Node.js" "stack trace"
```

```txt
site:example.com "ASP.NET" "Server Error in"
```

---

# 19. Subdominios interesantes

```txt
site:*.example.com -www
```

```txt
site:*.example.com inurl:dev OR inurl:staging OR inurl:test OR inurl:qa
```

```txt
site:*.example.com inurl:internal OR inurl:admin OR inurl:secure
```

```txt
site:*.example.com intitle:"index of"
```

```txt
site:*.example.com "Welcome to nginx" OR "Apache2 Ubuntu Default Page"
```

---

# 20. Directorios listados

```txt
site:example.com intitle:"index of"
```

```txt
site:example.com intitle:"index of" "backup"
```

```txt
site:example.com intitle:"index of" ".env"
```

```txt
site:example.com intitle:"index of" "config"
```

```txt
site:example.com intitle:"index of" "logs"
```

---

# 21. Buckets y cloud storage

```txt
site:s3.amazonaws.com "example.com" "index of"
```

```txt
site:storage.googleapis.com "example.com"
```

```txt
site:amazonaws.com "example.com" "backup"
```

```txt
site:blob.core.windows.net "example.com" "confidential"
```

```txt
site:sharepoint.com "example.com" "internal"
```

---

# 22. Jira, Confluence, GitLab, Jenkins expuestos

```txt
site:example.com inurl:jira OR intitle:"Jira"
```

```txt
site:example.com inurl:confluence OR intitle:"Confluence"
```

```txt
site:example.com inurl:gitlab OR intitle:"GitLab"
```

```txt
site:example.com inurl:jenkins OR intitle:"Dashboard [Jenkins]"
```

```txt
site:example.com inurl:bitbucket OR intitle:"Bitbucket"
```

---

# 23. CI/CD y artefactos

```txt
site:example.com inurl:.gitlab-ci.yml OR inurl:Jenkinsfile
```

```txt
site:example.com ext:yml OR ext:yaml "pipeline"
```

```txt
site:example.com "CI_JOB_TOKEN" OR "GITHUB_TOKEN" OR "GITLAB_TOKEN"
```

```txt
site:example.com "docker-compose.yml" OR "Dockerfile"
```

```txt
site:example.com "registry" "password"
```

---

# 24. Git expuesto

```txt
site:example.com inurl:.git
```

```txt
site:example.com intitle:"index of" ".git"
```

```txt
site:example.com inurl:.git/config
```

```txt
site:example.com "gitlab-ci" "password"
```

```txt
site:example.com ".git-credentials"
```

---

# 25. WordPress

```txt
site:example.com inurl:wp-content
```

```txt
site:example.com inurl:wp-admin OR inurl:wp-login.php
```

```txt
site:example.com inurl:wp-content/uploads
```

```txt
site:example.com inurl:wp-json/wp/v2/users
```

```txt
site:example.com "Powered by WordPress"
```

---

# 26. Adobe Experience Manager AEM

```txt
site:example.com inurl:/system/console
```

```txt
site:example.com inurl:/crx/packmgr
```

```txt
site:example.com inurl:/libs/cq
```

```txt
site:example.com inurl:/content/dam ext:json
```

```txt
site:example.com inurl:/bin/querybuilder.json
```

---

# 27. Firebase

```txt
site:firebaseio.com "example.com"
```

```txt
site:firebaseapp.com "example.com"
```

```txt
site:example.com "firebaseConfig"
```

```txt
site:example.com "firebaseio.com" "authDomain"
```

```txt
site:example.com "storageBucket" "firebase"
```

---

# 28. CORS / OAuth / SSO candidates

```txt
site:example.com inurl:oauth OR inurl:sso OR inurl:saml
```

```txt
site:example.com inurl:redirect_uri= OR inurl:client_id=
```

```txt
site:example.com inurl:authorize OR inurl:token
```

```txt
site:example.com "client_id" "redirect_uri"
```

```txt
site:example.com "SAMLRequest" OR "SAMLResponse"
```

---

# 29. Parámetros de pago / compras

```txt
site:example.com inurl:checkout OR inurl:payment OR inurl:billing
```

```txt
site:example.com inurl:invoice OR inurl:receipt OR inurl:order
```

```txt
site:example.com inurl:coupon OR inurl:discount OR inurl:promo
```

```txt
site:example.com inurl:price= OR inurl:amount= OR inurl:total=
```

```txt
site:example.com inurl:plan= OR inurl:subscription=
```

---

# 30. Parámetros de PII

```txt
site:example.com inurl:email= OR inurl:phone= OR inurl:address=
```

```txt
site:example.com inurl:ssn= OR inurl:dob= OR inurl:birthdate=
```

```txt
site:example.com inurl:first_name= OR inurl:last_name=
```

```txt
site:example.com inurl:customer= OR inurl:client= OR inurl:user=
```

```txt
site:example.com ext:xls OR ext:xlsx "email" "phone"
```

---

# 31. Archivos JavaScript

```txt
site:example.com ext:js
```

```txt
site:example.com ext:js "api"
```

```txt
site:example.com ext:js "token" OR "secret" OR "key"
```

```txt
site:example.com ext:js "baseURL" OR "baseUrl" OR "apiUrl"
```

```txt
site:example.com ext:js "sentry" OR "bugsnag" OR "datadog"
```

---

# 32. Source maps

```txt
site:example.com ext:map
```

```txt
site:example.com inurl:.js.map
```

```txt
site:example.com ext:map "sourcesContent"
```

```txt
site:example.com ext:map "webpack"
```

```txt
site:example.com inurl:main.js.map OR inurl:app.js.map
```

---

# 33. Documentación interna o técnica

```txt
site:example.com "runbook" OR "playbook"
```

```txt
site:example.com "postmortem" OR "incident report"
```

```txt
site:example.com "API documentation" OR "developer guide"
```

```txt
site:example.com "staging environment" OR "test environment"
```

```txt
site:example.com "VPN" "username"
```

---

# 34. Dorks externos útiles

Estos no van contra `site:example.com`, sino contra plataformas de terceros donde puede aparecer información relacionada con el objetivo.

```txt
site:github.com "example.com" "password"
```

```txt
site:github.com "example.com" "api_key"
```

```txt
site:gitlab.com "example.com" "secret"
```

```txt
site:pastebin.com "example.com" "token"
```

```txt
site:trello.com "example.com"
```

```txt
site:notion.site "example.com"
```

```txt
site:atlassian.net "example.com"
```

```txt
site:herokuapp.com "example.com"
```

```txt
site:vercel.app "example.com"
```

```txt
site:netlify.app "example.com"
```

---

# Mejoras de sintaxis

## Usar `OR` en lugar de `|`

Mejor:

```txt
site:example.com ext:log OR ext:txt OR ext:conf OR ext:env
```

Evita depender de:

```txt
site:example.com ext:log | ext:txt | ext:conf | ext:env
```

## Reducir ruido general

```txt
site:example.com -github.com -gitlab.com -stackoverflow.com
```

```txt
site:example.com -blog -news -press -careers -jobs
```

## Buscar solo zonas de aplicación

```txt
site:example.com inurl:app OR inurl:portal OR inurl:dashboard OR inurl:account
```


---


Top Parameters:
https://github.com/lutfumertceylan/top25-parameter

Proviesec dorks:
https://github.com/Proviesec/google-dorks
