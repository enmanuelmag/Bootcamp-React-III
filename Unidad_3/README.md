# Modulo 3 - Routing en ReactJS

## ¿Qué es Routing?

Es la forma en la que el usuario puede desplazarse o visitar diferentes secciones de una aplicación web. Básicamente es una asociación de un URL, con algún componente de ReactJS. Estas URLs pueden ser:

- Estáticas
- Dinámicas

## ¿Por qué Routing usarlo?

- Mejora la experiencia del usuario.
- Facilita la navegación.
- Permite compartir enlaces.
- Facilita la indexación de motores de búsqueda.

## Tanstack Router

Es una librería de ReactJS que permite manejar el enrutamiento de una aplicación web. Es la más popular y utilizada en la actualidad.


## Configurando rutas

Como se menciono previamente, en este curso usaremos el File-based routing, que consiste en crear una estructura de carpetas y archivos que representen las rutas de la aplicación. Esto permite una mejor organización del código y facilita la navegación entre las diferentes secciones de la aplicación. Actualmente ya el proyecto tiene configurado el enrutamiento, pero puedes revisar la documentación oficial de [Tanstack Router](https://tanstack.com/router/latest/docs/framework/react/quick-start) para más información de como hacerlo manualmente.

### Estructura de carpetas

```
src/
  components/
    <componentes de la app>
  routes/
    <rutas de la app>
  types/       
    <tipos de la app>
  api/         
    <definición de funciones para cargar datos>
  App.tsx
```

Puntos a repasar:
- `src/main.tsx`: Aquí se inicializa la aplicación y se configura el enrutamiento. No solo esta la config del router, sino también de React-Query, que se revisará más adelante.
- `routerTree.gen.ts`: Aquí se genera el árbol de rutas de la aplicación. Este archivo es generado automáticamente por la librería y no es necesario modificarlo.
- `src/routes/`: Aquí se encuentran las rutas de la aplicación. Cada archivo representa una ruta y su estructura de carpetas representa la jerarquía de las rutas

[Documentación sobre las rutas](https://tanstack.com/router/latest/docs/framework/react/routing/route-trees)

## Práctica Routing

Consiste en realizar lo siguiente:
- Crear la ruta `/candidates` que muestre una lista de candidatos. Asi como se visualiza actualmente en la aplicación.
- Agregar el hook de search params, para buscar candidatos según el estado.

Pasos:
- Actualizar el esquema `CandidateSchema` para agregar el `id`.
- Crear el archivo `src/api/candidates.ts`, el cual debe contener la función `getCandidates` que retorna una lista de candidatos. Puede recibir un parámetro `status` que filtra la lista de candidatos según el estado.
- Crear el archivo `src/routes/candidates.tsx`, el cual debe mostrar la lista de candidatos.
- Actualizar el `src/components/Header.tsx` para agregar un enlace a la ruta `/candidates`.

Filtrar candidatos por estado:
- Para esto podemos definir enviar el filtro por search params. Para esto se puede usar el hook `useSearchParams` de React Router. Este hook permite acceder a los parámetros de búsqueda de la URL y actualizarlos. Se puede usar para filtrar la lista de candidatos según el estado. La ruta debe ser `/candidates?status=Pending` o `/candidates?status=Approved`, etc.

Link para probar:
```
http://localhost:3000/candidates?status=Pending
```

## Se puede mejora rla carga de datos?

Actualmente estamos usando directamente una función sincrona que no produce un retraso en la carga de los datos. Sin embargo, gracias a que estamos usando el pack de Tanstack tenemos 2 opciones de poner mejorar y manejar peticiones asíncronas:

- Parámetro `loader` en la función `createFileRoute`. Este parámetro permite definir una función que se ejecutará antes de cargar la ruta. Esta función puede ser asíncrona y puede devolver un objeto que contenga los datos que se cargarán en la ruta. Esto permite manejar la carga de datos de forma más eficiente y evitar el uso de funciones sincrónicas.
- Usar React-Query. Esta librería permite manejar la carga de datos de forma más eficiente y evita el uso de funciones sincrónicas. Además, permite manejar el estado de la carga de datos, los errores y la caché de los datos. Esto permite mejorar la experiencia del usuario y evitar problemas de rendimiento en la aplicación.

### Cuando usar una u otra opción?

El uso del parámetro es un enfoque más sencillo y ligado a la ruta. Por lo que es recomendable usarlo cuando la carga de datos es sencilla y no requiere de un manejo más complejo. Por otro lado, el uso de React-Query es más adecuado para cargas de datos más complejas, donde se requiere un manejo más eficiente del estado de la carga de datos, los errores y la caché de los datos. Además, permite en un solo componente realizar múltiples peticiones a diferentes APIs y manejar el estado de cada una de ellas de forma independiente.

Pasos a seguir para usar `loader`
- Definir el loader en la ruta `/candidates` y usar la función `getCandidates` para cargar los datos.
- Actualizar el componente `Candidates` para usar los datos cargados por el loader.
