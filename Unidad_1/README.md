# Modulo 1 - ReactJS

##  ¿Que es ReactJS?
Es una de las librerías, creada por Facebook, mas populares de JavaScript para el desarrollo de aplicaciones web y móviles. Se fundamenta en la creación de fragmentos o bloques reutilizables llamados Componentes, para crear interfaces.

## ¿Por qué ReactJS?

- Gran comunidad de desarrolladores.
- Fácil curva de aprendizaje.
- Desarrollo web y móvil (nativo).

## Creación de un proyecto en ReactJS

```bash
npm create vite@latest

# 1. Escriba el nombre del proyecto
# 2. Seleccione la opción React
# 3. Seleccione la opción Tanstack-Router
# 4. Seleccione la opción File Router - File-based routing structure
# 5. Do you like to use Tailwind CSS? (Y/n) Y
# 6. Select toolchain: eslint+prettier
# 7. (Optional) Select add-ons: Form, Shadcn, Tanstack Query (use Space bar to select)
# 8. Would you like any examples? No, Just press Enter

# Ingresar al directorio del proyecto
cd <nombre_proyecto>

# Instalar dep para poder usar alias en tsconfig.json y vite.config.ts
npm i --save-dev vite-tsconfig-paths

# Add import tsconfigPaths from 'vite-tsconfig-paths'
# Update tsconfig.json with data below and remove alias from vite.config.ts

# Iniciar el servidor de desarrollo
npm run dev
```

## Configuración de TypeScript
```json
  "baseUrl": ".",
  "paths": {
    "@/*": ["src/*"],
    "@api/*": ["src/api/*"],
    "@components/*": ["src/components/*"],
    "@constants/*": ["src/constants/*"],
    "@hooks/*": ["src/hooks/*"],
    "@shared/*": ["src/shared/*"],
    "@styles/*": ["src/styles/*"],
    "@utils/*": ["src/utils/*"],
    "@pages/*": ["src/pages/*"],
    "@assets/*": ["src/assets/*"],
    "@customTypes/*": ["src/types/*"],
    "@store/*": ["src/store/*"],
    "@services/*": ["src/services/*"]
  }
```

# Componentes en ReactJS
En la actualidad toda aplicación, ya sea web o móvil, se empieza a diseñar por secciones, páginas y bloques. Es aquí donde se empiezan a definir las bases de cada componente, sus funcionalidades, estilos e interacción con la UI o los datos de nuestra aplicación.

En ReactJS los bloques de nuestra aplicación son los Componentes, en ellos desarrollaremos, de manera declarativa, como se renderizará el componente, si hace uso o no de “props” y sus diferentes interacciones.

## Creación de mi primer componente

Se debe crear un componente que renderice el nombre, edad, años de experiencia laboral y estado actual de contratación (pendiente, revisión, rechazado, contratado) y skills de un usuario. El componente debe recibir los siguientes props:

- `name`: Nombre del usuario
- `age`: Edad del usuario
- `experience`: Años de experiencia laboral (número)
- `status`: Estado actual de contratación (string)
- `skills`: Habilidades del usuario (array de strings)


El componente `Candidate` creado debe estar dentro de la carpeta `src/components/` se debe usar en el archivo de entrada de ViteJs (__root.tsx)

> En las siguientes clases se profundizará en el sistema de routing y como administrarlo.
> Por ahora, trabajaremos solo en el archivo `main.tsx` y `__root.tsx`

Requisitos:
- El componente debe recibir los props `url` y `name`
- En el archivo `App.tsx` usar una lista (Array) de objetos que contengan la url y el nombre del usuario para renderizar varios componentes `Candidate`

### Estructura de carpetas
```
src/
  components/
    candidate.tsx
```

## Props en ReactJS

Los props es un análogo de los parámetros que hemos visto en las funciones. Para enviar un valor en un prop a un componente se lo realiza como los atributos HTML antes revisado, con la diferencia de que ahora no solo pueden recibir String, si no también todos los demás valores primitivos y complejos como JSONs, Clases o incluso, otro Componente de ReactJS.

Como tal React no es difícil, pero si hay que tener en el mapa ciertas bases o conocimientos para construir buenas aplicaciones. Tales como el ciclo de vida y como utilizarlo, sobre todo el tema de memorization. Patrones de diseño eficientes. El uso de librerías adecuadas etc

## Compilación 

Con ReactJS, el programador escribe la aplicación web en JSX, TSX (Typescript), junto con CSS (o SCSS) para al final ver una aplicación web que es solo HTML, CSS y JavaScript. Pero...

- ¿Cómo o quién realiza este proceso?
- ¿Cómo ReactJS actualiza la UI una vez compilado?

# Preparación del entorno de desarrollo

Navegador:
- Redux DevTools
- React DevTools

Visual Studio Code:
- TypeScript
- Tailwind

## Extra

- Añadir un prop “working” para indicar cuando un usuario está actualmente trabajando. En caso de serlo mostrar una imagen de “Check” o un texto que indique está o no trabajando.
- Investigar sobre renderizado condicional y dinámico. Para poder desde una lista de objecto de type `CandidateType`, rederizar el componente `Candidate`.

Hint:
```tsx
const candidates: CandidateType = [
{ name: 'Emanuel', age: 26, ...el resto de propiedades definidas en el type }
]
```

[Documentación](https://react.dev/learn/conditional-rendering)

