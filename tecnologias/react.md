# React

## Introducción

[React](https://reactjs.org) es una librería de JavaScript para contruir interfaces de ususario. Es importante tener claro que React es sólo para construir la interfaz de una forma declarativa y basada en componentes. Para realizar otras tareas como AJAX, la sesión y persistencia de datos se utilizan otras librerías.

Si no has trabajado con esta librería te recomiendo que des tus primero pasos en [la guía oficial](https://reactjs.org/docs/hello-world.html).

## Create React App

Configurar una aplicación react requiere trabajo que alguién ya hizo por nosotros. Para comenzar un nuevo proyecto usaremos el software desarrollado por Facebook para facilitar la creación de aplicaciones, [create-react-app](https://github.com/facebook/create-react-app).

En el repositorio del proyecto están todas las instrucciones y [guías](https://github.com/facebook/create-react-app/blob/master/packages/react-scripts/template/README.md) para comenzar a desarrollar.

### Instalación

````bash
npm install -g create-react-app
````

### Nueva aplicación

```bash
create-react-app my-educalabs-app
cd my-educalabs-app
yarn start
```

Luego abre http://localhost:3000/ para ver la nueva applicación.

### Pasando a producción

Cuando esté lista para pasar a producción o staging, debes crear nuna versión modificada ejecutando:

```bash
yarn build
```

El package manager de preferencia por proyecto es [Yarn](https://yarnpkg.com).
