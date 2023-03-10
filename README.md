# spring-boot-flyway-jooq-postgres-swagger-java-kotlin-template

Create spring boot project from scratch:

https://start.spring.io/#!type=maven-project&language=kotlin&platformVersion=2.7.6&packaging=jar&jvmVersion=11&groupId=com.zlargon&artifactId=springdemo&name=springdemo&description=&packageName=com.zlargon.springdemo&dependencies=lombok,devtools,jooq,postgresql,web,actuator,testcontainers,flyway

## Features

| Name            | Description                      |
| --------------- | -------------------------------- |
| Kotlin          |                                  |
| ktlint          | Kotlin code format and lint      |
| Spring Web MVC  |                                  |
| Spring Devtools | Hot Reload Spring boot           |
| Lombok          | Prevent boilerplate code         |
| Docker          | Run SQL Database with container  |
| Postgres        | SQL Database                     |
| Flyway          | SQL Database Migration           |
| jOOQ            | Typesafe SQL ORM                 |
| Swagger UI      | OpenAPI documentation            |
| Junit 5         | Unit Test                        |
| Jacoco          | Code Coverage                    |
| Test Container  | Run docker container for testing |
| Prettier        | Code Formatter                   |
| Git Hooks       | Pre-commit, pre-push             |

## Prerequisite

```bash
bash

# Install by sdkman: https://sdkman.io/
sdk install kotlin 1.6.21      # Kotlin 1.6.21
sdk install java 11.0.17-zulu  # Java 11
sdk install maven 3.8.6        # Maven
sdk install jbang 0.101.0      # Jbang for running jOOQ code generator script

# Install by brew: https://brew.sh/
brew install --cask docker  # Docker Desktop
brew install pnpm           # (Optional) For running scripts in package.json
brew install curl           # (Optional) For running the testing curl script
brew install jq             # (Optional) For running the testing curl script
```

## Setup Postgres by docker compose

```bash
pnpm up      # run docker compose up
pnpm stop    # run docker compose stop
pnpm down    # run docker compose down
pnpm log     # show logs from docker compose
```

## Scripts

```bash
pnpm start         # run spring boot application
pnpm test          # run tests by console launcher
pnpm coverage      # run tests with code coverage and open the report website
pnpm clean         # clean the project
pnpm lint          # lint the source code
pnpm format        # format the source code
pnpm jooq:codegen  # run script to update jooq generated code
pnpm doc           # open swagger-ui website for API documentation
```

## Run Spring Application

1. Run postgres at port 5700 by docker

   ```bash
   pnpm up
   pnpm log  # check the logs from docker compose
   ```

2. Run Spring boot service

   ```bash
   pnpm start
   ```

3. Run curl command to check the apis

   ```bash
   ./curl/create_book.sh # POST /api/v1/books
   ./curl/get_book.sh    # GET  /api/v1/books
   ```

## Dependencies

- api

  - spring-boot-starter-web

- database

  - spring-boot-starter-jooq
  - org.flywaydb:flyway-core
  - postgresql

- document

  - springdoc-openapi-ui
    - the api document will be generated at `http://localhost:8080/swagger-ui`

- test

  - spring-boot-starter-test
  - junit-platform-console-standalone
  - org.testcontainers:testcontainers-bom
  - org.testcontainers:junit-jupiter
  - org.testcontainers:postgresql

- tools

  - lombok
  - spring-boot-devtools
  - spring-boot-starter-actuator

## Maven Plugins

- spring-boot-maven-plugin

- kotlin-maven-plugin

  - Compile Kotlin before compile Java

- maven-compiler-plugin

  - Compile Java

- exec-maven-plugin

  - Install git hook

- jacoco-maven-plugin

  - The code coverage report will be generated at `target/site/jacoco/index.html`

- prettier-maven-plugin

  - format the source code
    - printWidth: 120
    - tabWidth: 2
    - useTabs: false

- ktlint-maven-plugin

## VSCode Plugins

- [Extension Pack for Java](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-pack)
- [Spring Boot Extension Pack](https://marketplace.visualstudio.com/items?itemName=Pivotal.vscode-boot-dev-pack)
- [Java prettier formatter](https://marketplace.visualstudio.com/items?itemName=mwpb.java-prettier-formatter)

  ```json
  "[java]": {
    "editor.defaultFormatter": "mwpb.java-prettier-formatter",
    "editor.formatOnSave": true
  },
  ```

- [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)
- [ShellCheck](https://marketplace.visualstudio.com/items?itemName=timonwong.shellcheck)
