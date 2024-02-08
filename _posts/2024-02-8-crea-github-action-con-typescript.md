---
layout: post
title: ¡Crea una Github custom action con TypeScript!
description: >
  Con esta guía vas a conocer todo lo que necesitas para preparar el scaffolding de tu custom action con TypeScript
sitemap: false
accent_image: '#0388fc'
accent_color: '#ccc'
theme_color: '#ccc'
hide_last_modified: true
invert_sidebar: true
---

![Header image](https://cdn.hashnode.com/res/hashnode/image/upload/v1648546102552/z5hSWxNIx.jpg)

Crear una **Action de Github con TypeScript** puede ser una tarea tediosa, ya que Github sólo soporta de manera nativa el código JavaScript.

Si buscas por la [documentación de Github](https://docs.github.com/en/actions/creating-actions/creating-a-javascript-action#template-repositories-for-creating-javascript-actions "https://docs.github.com/en/actions/creating-actions/creating-a-javascript-action#template-repositories-for-creating-javascript-actions") no vas a encontrar mucha información acerca de cómo crear una Action con TypeScript más allá de [ofrecerte una template](https://github.com/actions/typescript-action "https://github.com/actions/typescript-action").

Por eso mismo he decidido crear este post, para tener una pequeña guía en español. Y aunque hay muchos ficheros de esa template de los que sí hacemos uso, hay otros muchos que no me parecen tan relevantes, y podemos quitarnos bastante carga de nuestra Action.

## Toolkit para trabajar con JavaScript y TypeScript

Es importante conocer el [paquete de dependencias que nos ofrece Github](https://github.com/actions/toolkit/tree/master "https://github.com/actions/toolkit/tree/master") para nuestras custom actions con JavaScript y TypeScript.

A la que más uso vamos a darle será la de `@actions/core` . Esta nos permite realizar las tareas más comunes, como por ejemplo leer los inputs, los outputs, secretos, variables...

Es interesante echarle un vistazo al [repositorio](https://github.com/actions/toolkit/tree/master "https://github.com/actions/toolkit/tree/master") para ver las posibilidades que nos ofrece cada una de ellas.

Nosotros vamos a cargar nuestras dependencias agregándolas directamente en nuestro archivo `package.json` , pero no está demás saber que podemos instalarla desde la línea de comandos de nuestra terminal:

```bash
npm install @actions/core
```

## Archivo de metadatos (action.yml)

Pasamos a hablar del archivo de metadatos. Lo único distintivo de las actions de *JavaScript* en comparación a las *Composite* o de *Docker* es la parte de `runs:` .

Vamos a ver un ejemplo de archivo `action.yml` :

```
name: "TypeScript Custom Action"
description: "This is a Custom Action made on TypeScript"

inputs:
  myname:
    description: "Your name"
    required: true
    default: "Nedd"

runs:
  using: node20
  main: dist/index.js
```

Como podemos observar realmente estamos ejecutando un archivo *JavaScript* llamado `index.js` . Esto es porque realmente sólo programamos en *TypeScript* de manera local. A la hora de ejecutar la Action, esta correrá de un archivo *JavaScript* que se crea a partir de buildear nuestro código *TypeScript*.

De versión de *Node* vamos a usar la última que esté disponible. En el momento en el que estoy escribiendo esto es la `node20` . Y en el campo `main: dist/index.js` estamos definiendo el archivo inicial que queremos que lea nuestra Action.

## Archivo package.json

En el fichero `package.json`  definimos algunos metadatos de nuestro proyecto, y lo más importante, las dependencias necesarias para trabajar con él.

Además también definimos una serie de comandos npm, que nos van a ser útiles para construir la build de nuestro programa, entre otras cosas, como ejecutar el linter, etc...

Voy a mostrar un ejemplo de archivo `package.json`  que uso para todos mis proyectos de *TypeScript* para crear mis custom actions, aunque a veces no use muchos de los comandos predefinidos, pero está bien tenerlos ya configurados para hacer uso de ellos en un futuro:

```json
{
    "name": "testaction",
    "version": "1.0.0",
    "description": "",
    "main": "index.js",
    "compilerOptions": {
        "esModuleInterop": true
    },
    "scripts": {
        "bundle": "npm run format:write && npm run package",
        "ci-test": "jest",
        "coverage": "make-coverage-badge --output-path ./badges/coverage.svg",
        "format:write": "prettier --write **/*.ts",
        "format:check": "prettier --check **/*.ts",
        "lint": "npx eslint . -c ./.github/linters/.eslintrc.yml",
        "package": "ncc build src/index.ts --license licenses.txt",
        "package:watch": "npm run package -- --watch",
        "test": "jest",
        "all": "npm run format:write && npm run lint && npm run test && npm run coverage && npm run package"
    },
    "keywords": [],
    "author": "",
    "license": "ISC",
    "devDependencies": {
        "@types/jest": "^29.5.11",
        "@types/node": "^20.11.10",
        "@typescript-eslint/eslint-plugin": "^6.19.1",
        "@typescript-eslint/parser": "^6.19.1",
        "@vercel/ncc": "^0.38.1",
        "eslint": "^8.56.0",
        "eslint-plugin-github": "^4.10.1",
        "eslint-plugin-jest": "^27.6.3",
        "eslint-plugin-jsonc": "^2.13.0",
        "eslint-plugin-prettier": "^5.1.3",
        "jest": "^29.7.0",
        "make-coverage-badge": "^1.2.0",
        "prettier": "^3.2.4",
        "prettier-eslint": "^16.3.0",
        "ts-jest": "^29.1.2",
        "typescript": "^5.3.3"
    },
    "dependencies": {
        "@actions/core": "^1.10.1"
    }
}
```

## Archivo tsconfig.json

Para este ejemplo vamos a usar este fichero `tsconfig.json` . Aquí se define el directorio en el que se guarda nuestra build por ejemplo. En este caso, queremos que se guarde en `./dist` , también definimos que nuestro código *TypeScript* se encuentra en el directorio `./src` .

Copia este código y pégalo en la raíz del proyecto:

```json
{
    "$schema": "https://json.schemastore.org/tsconfig",
    "compilerOptions": {
        "target": "ES2022",
        "module": "NodeNext",
        "rootDir": "./src",
        "moduleResolution": "NodeNext",
        "baseUrl": "./",
        "sourceMap": true,
        "outDir": "./dist",
        "noImplicitAny": true,
        "esModuleInterop": true,
        "forceConsistentCasingInFileNames": true,
        "strict": true,
        "skipLibCheck": true,
        "newLine": "lf"
    },
    "exclude": ["./dist", "./node_modules", "./__tests__", "./coverage"]
}
```

## Archivo de workflow

Como ya sabemos, para correr un workflow tenemos que disponer de nuestro archivo en el directorio `.github/workflows/nombre.yml` .

En este caso, voy a dejar un workflow previamente listo para que corra la build de nuestro código cada vez que este se ejecute. Esto lo conseguimos usando el comando `npm run bundle` .

Previamente, hacemos un `actions/checkout@v4`  para leer el contenido del repositorio en el que nos encontramos. Y por último, corremos nuestra action, que ya sabemos que tira del archivo `./dist/index.js` .

Este es el código del workflow:

```yaml
name: Purped TypeScript Custom Action

on:
    workflow_dispatch:

jobs:
    test:
        runs-on: ubuntu-latest
        steps:
            - name: Checkout code
              uses: actions/checkout@v4

            - name: Build Action
              run: |
                  npm install
                  npm run bundle

            - name: Run TypeScript Action
              uses: ./
              with:
                  myname: Nedd
```

## Archivo .gitignore

Me gustaría dejar un archivo `.gitignore`  para no llenar nuestro repositorio de archivos innecesarios:

```
# Dependency directory
node_modules

# Rest pulled from https://github.com/github/gitignore/blob/master/Node.gitignore
# Logs
logs
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*
lerna-debug.log*

# Diagnostic reports (https://nodejs.org/api/report.html)
report.[0-9]*.[0-9]*.[0-9]*.[0-9]*.json

# Runtime data
pids
*.pid
*.seed
*.pid.lock

# Directory for instrumented libs generated by jscoverage/JSCover
lib-cov

# Coverage directory used by tools like istanbul
coverage
*.lcov

# nyc test coverage
.nyc_output

# Grunt intermediate storage (https://gruntjs.com/creating-plugins#storing-task-files)
.grunt

# Bower dependency directory (https://bower.io/)
bower_components

# node-waf configuration
.lock-wscript

# Compiled binary addons (https://nodejs.org/api/addons.html)
build/Release

# Dependency directories
jspm_packages/

# TypeScript v1 declaration files
typings/

# TypeScript cache
*.tsbuildinfo

# Optional npm cache directory
.npm

# Optional eslint cache
.eslintcache

# Optional REPL history
.node_repl_history

# Output of 'npm pack'
*.tgz

# Yarn Integrity file
.yarn-integrity

# dotenv environment variables file
.env
.env.test

# parcel-bundler cache (https://parceljs.org/)
.cache

# next.js build output
.next

# nuxt.js build output
.nuxt

# vuepress build output
.vuepress/dist

# Serverless directories
.serverless/

# FuseBox cache
.fusebox/

# DynamoDB Local files
.dynamodb/

# OS metadata
.DS_Store
Thumbs.db

# Ignore built ts files
__tests__/runner/*

# IDE files
.idea
.vscode
*.code-workspace
```

## Archivo TypeScript

Por último, creamos nuestro fichero o ficheros *TypeScript* dentro del directorio `./src` . El archivo principal de nuestro script deberá llamarse `./src/index.ts` .

Ya las funcionalidades que vayas a crear con el código dependen de ti.

Un código simple podría ser este:

```typescript
import * as core from "@actions/core";

console.log(`Hola ${core.getInput("myname")}`);
```

## Arbol de ficheros final

```
$ tree -I .git -I node_modules
.
├── action.yml
├── package-lock.json
├── package.json
├── src
│   └── index.ts
└── tsconfig.json

2 directories, 5 files
```

## Conclusión

Aprender a crear Github Custom Actions usando *TypeScript* puede resultar algo complicado si nunca has usado el lenguaje de programación *JavaScript*, pero si es cierto que profesionalmente puede marcar una diferencia.

Hacer uso de un lenguaje de programación como *TypeScript* nos aporta mucha seguridad y mucha eficiencia en nuestro código, además a aportarnos mucha capacidad de cómputo para nuestros workflows, y que funciona de manera nativa con Github.

Bajo mi punto de vista, lo más complicado ha sido entender el por qué se hacen las cosas de unas maneras u otras, ya que la documentación no deja nada en claro. Merecen que les abran algunas issues.

Yo te animo a ti lector, a que pruebes a crear una Action con TypeScript. De seguro que vas a aprender mucho sobre esta tecnología, y quizás pueda marcar la diferencia frente a otros desarrolladores.
