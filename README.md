# swagger-nodegen-cli

A convenience package for the **node/npm** environment that wraps the Java library [**swagger-codegen-cli-2.4.4.jar**](http://repo1.maven.org/maven2/io/swagger/swagger-codegen-cli/2.4.2/swagger-codegen-cli-2.4.2.jar).

## Prerequisites

The following dependencies would need to be installed on your machine before running the Swagger Codegen.

- Java, version 7 or higher
- The Java execution path must be on your environment variable `PATH`

## Installation

- npm install -g swagger-nodegen-cli

## Usage

Same as **swagger-codegen-cli.jar** without `java -jar ...`
The main command is **swagger-codegen-cli** or **swagger-nodegen-cli**

`usage: swagger-codegen-cli <command> [<args>]`

`usage: swagger-nodegen-cli <command> [<args>]`

## Examples

### Display help

```console
swagger-codegen-cli help
```

### Display list of available languages

```console
swagger-nodegen-cli
```

### Generate a typescript-angular (4.3) service from a `swagger`-file

#### Features

- Generates an Angular service per defined swagger resource
- Generates models with custom property name flavours: camelCase, PascalCase, snake_case ... (see `swagger-nodegen-cli config-help -l typescript-angular`)
- Base path injection with InjectionToken

```console

swagger-nodegen-cli generate -i swagger.yaml -l typescript-angular -o src/services

```

#### Integration into an Angular >= 4.3 application

```tree

|-- angular-application
|-- src
|   |-- app
|   |   |-- app.component.html
|   |   |-- app.component.ts
|   |   |-- app.component.css
|   |   |-- app.module.ts
|   `-- services
|       |-- ...

```

`./src/app/app.module.ts`

```typescript
import { NgModule } from '@angular/core';
import { HttpClientModule } from '@angular/common/http';
import { BrowserModule }  from '@angular/platform-browser';
import { AppComponent } from './app.component';
import { ApiModule, BASE_PATH } from '../services';

@NgModule({
  imports: [
    BrowserModule,
    HttpClientModule,
    ApiModule
  ],
  declarations: [
    AppComponent
  ],
  providers: [
    { provide: BASE_PATH, useValue: 'http://localhost:10010' }
  ],
  bootstrap: [ AppComponent ]
})
export class AppModule { }

```

### Generate a nodjs-server skelton from a `swagger`-file

```console

swagger-nodegen-cli generate -i swagger.yaml -l nodejs-server -o my-service

```

## Links

- [swagger-codegen-cli](https://oss.sonatype.org/content/repositories/releases/io/swagger/swagger-codegen-cli/)

- [swagger-codegen](https://github.com/swagger-api/swagger-codegen)

- [swagger-tools](https://swagger.io/docs/swagger-tools/)
