# Manual Técnico — Portal de Enlaces Privados

**Versión del documento:** 1.0  
**Fecha:** 07/08/2026 

**Repositorio:** [migueljerico/portal-enlaces-privados-documentation](https://github.com/migueljerico/portal-enlaces-privados-documentation)  
**Aplicación en producción:** [mis-enlaces-privados.lovable.app](https://mis-enlaces-privados.lovable.app)

---

## 1. Arquitectura General

La aplicación sigue una arquitectura de **Single Page Application (SPA)** con tres capas conceptuales, todas ejecutándose en el lado del cliente:

```
┌─────────────────────────────────────────────────────┐
│                    CAPA DE PRESENTACIÓN              │
│  ┌─────────────────────────────────────────────────┐ │
│  │  Componentes React (JSX) + Tailwind CSS        │ │
│  │  ┌──────────┐ ┌──────────┐ ┌────────────────┐  │ │
│  │  │ AuthGate │ │ Dashboard│ │ ThemeToggle   │  │ │
│  │  └──────────┘ └──────────┘ └────────────────┘  │ │
│  │  ┌──────────┐ ┌──────────┐ ┌────────────────┐  │ │
│  │  │  Search  │ │  Card    │ │  Footer       │  │ │
│  │  └──────────┘ └──────────┘ └────────────────┘  │ │
│  └─────────────────────────────────────────────────┘ │
├─────────────────────────────────────────────────────┤
│                CAPA DE LÓGICA (React)               │
│  ┌─────────────────────────────────────────────────┐ │
│  │  Estado global (useState / useReducer)         │ │
│  │  - Autenticación (token en memoria)            │ │
│  │  - Tema claro/oscuro (localStorage)            │ │
│  │  - Filtro de búsqueda (texto)                  │ │
│  │  - Lista de enlaces (array estático)           │ │
│  └─────────────────────────────────────────────────┘ │
├─────────────────────────────────────────────────────┤
│             CAPA DE DATOS / ALMACENAMIENTO          │
│  ┌─────────────────────────────────────────────────┐ │
│  │ ● Datos de enlaces: objeto JSON inline         │ │
│  │ ● Persistencia de tema: localStorage            │ │
│  │ ● No hay backend ni API externa                │ │
│  └─────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────┘
```

**Flujo de interacción típico:**

1. El usuario accede a la URL de la aplicación.
2. Se muestra el componente `AuthGate` (pantalla de inicio de sesión).
3. Tras autenticarse correctamente, se renderiza el `Dashboard`.
4. El usuario puede buscar enlaces mediante el `SearchBar`, alternar el tema (`ThemeToggle`) y hacer clic en tarjetas (`Card`) para abrir enlaces en nuevas pestañas.
5. El estado de tema persiste en `localStorage`.

---

## 2. Módulos y Componentes Principales

A continuación se describen los componentes React que conforman la aplicación. Dado que el repositorio actual solo contiene el README y la licencia, los nombres y responsabilidades se han inferido del flujo de desarrollo descrito.

| Archivo / Componente       | Responsabilidad                                                                 | Funciones exportadas clave (props/eventos)                |
|----------------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
| `AuthGate`                 | Presenta un formulario de inicio de sesión protegido por contraseña.            | `onLogin(password: string): boolean`                      |
| `Dashboard`                | Contenedor principal que muestra la cuadrícula de tarjetas y la barra de búsqueda. | Renderiza `SearchBar`, `CardGrid`, `ThemeToggle`          |
| `SearchBar`                | Input de búsqueda que filtra enlaces por nombre o descripción.                  | `onSearch(query: string)`                                 |
| `Card`                     | Tarjeta individual con nombre, descripción y botón de acceso.                   | `link: { name, url, desc }`, `onClick` (abre URL)       |
| `ThemeToggle`              | Botón para alternar entre modo claro y oscuro.                                  | `onToggle(theme: 'light' | 'dark')`                      |
| `Footer` (opcional)       | Pie de página con información de versión y atribuciones.                        | —                                                         |

**Estructura de datos de enlaces (fragmento representativo):**

```javascript
const links = [
  {
    name: "Servicio 1",
    url: "https://ejemplo.com/servicio1",
    desc: "Descripción del servicio 1."
  },
  {
    name: "Servicio 2",
    url: "https://ejemplo.com/servicio2",
    desc: "Descripción del servicio 2."
  }
  // ... más enlaces privados
];
```

**Nota:** Los enlaces reales son privados y no se incluyen en el repositorio público.

---

## 3. APIs y Endpoints

**La aplicación no expone ni consume APIs externas.** Toda la funcionalidad es completamente del lado del cliente:

- La autenticación se realiza mediante una verificación de contraseña fija en el código, sin llamada a servidor.
- La lista de enlaces es un array estático embebido en el código fuente.
- El cambio de tema se almacena en `localStorage` del navegador.

**No existen endpoints REST ni servicios back-end.** Si en el futuro se añadiera una capa de servidor, se documentarían aquí.

---

## 4. Variables de Entorno

La aplicación no requiere variables de entorno para su funcionamiento básico, ya que todos los datos (contraseña, enlaces) están hardcodeados dentro del código. No obstante, si se desea externalizar la configuración, se recomienda el siguiente esquema (no implementado actualmente):

| Variable              | Valor de ejemplo                    | Obligatoria | Descripción                                      |
|-----------------------|-------------------------------------|-------------|--------------------------------------------------|
| `REACT_APP_PASSWORD`  | `miClaveSegura123`                  | No          | Contraseña de acceso al dashboard.               |
| `REACT_APP_LINKS_JSON`| `[{"name":"...","url":"...","desc":"..."}]` | No    | Lista de enlaces en formato JSON.                |
| `REACT_APP_TITLE`     | `Mis Enlaces Privados`              | No          | Título personalizado de la aplicación.           |

**Estado actual:** ninguna variable de entorno está configurada. La contraseña y los enlaces están definidos en el código fuente de la aplicación React.

---

## 5. Guía de Despliegue

La aplicación está construida con **React** y **Tailwind CSS**, y puede desplegarse en cualquier servicio de hosting estático (Lovable, Vercel, Netlify, GitHub Pages, etc.). A continuación, se detallan los pasos para un despliegue típico.

### Prerrequisitos

- Node.js >= 18.x
- npm >= 9.x
- Cuenta en un servicio de hosting estático (opcional para despliegue local)

### Paso 1: Clonar el repositorio

```bash
git clone https://github.com/migueljerico/portal-enlaces-privados-documentation.git
cd portal-enlaces-privados-documentation
```

> **Nota:** El repositorio actual solo contiene documentación. Para obtener el código fuente de la aplicación, es necesario acceder al proyecto original en Lovable o descargar el código generado. Si se dispone del código, se debe clonar en su lugar.

### Paso 2: Instalar dependencias

```bash
npm install
```

### Paso 3: Configure la contraseña y los enlaces (opcional)

Edite el archivo de configuración (por ejemplo, `src/config.js`) para modificar la contraseña y la lista de enlaces. **Asegúrese de no subir contraseñas reales a repositorios públicos.**

### Paso 4: Compilar la aplicación para producción

```bash
npm run build
```

El comando genera una carpeta `build/` con los archivos estáticos optimizados.

### Paso 5: Desplegar en un servicio de hosting

#### Opción A: Lovable (plataforma original)

- Conecte el repositorio de GitHub a Lovable.
- Lovable detecta automáticamente el proyecto React y lo despliega.
- La URL generada es similar a `https://mis-enlaces-privados.lovable.app`.

#### Opción B: Vercel

```bash
npx vercel --prod
```

- Siga las instrucciones en pantalla.
- Vercel detectará el framework React y configurará el build automáticamente.

#### Opción C: Netlify

- Arrastre la carpeta `build/` a Netlify Drop o conecte el repositorio.
- Configure el comando de build: `npm run build` y el directorio de publicación: `build`.

#### Opción D: GitHub Pages

1. Agregue al `package.json`: `"homepage": "https://<tu-usuario>.github.io/<repo>"`
2. Instale `gh-pages`: `npm install --save-dev gh-pages`
3. Agregue script: `"deploy": "gh-pages -d build"`
4. Ejecute: `npm run deploy`

### Paso 6: Verificar el despliegue

Acceda a la URL proporcionada por el servicio. Debería ver la pantalla de autenticación. Ingrese la contraseña configurada para acceder al dashboard.

---

## 6. Limitaciones Conocidas y Mejoras Futuras

### Limitaciones actuales

1. **Contraseña fija en el código.**  
   No hay un sistema de autenticación robusto (sin hashing, sin sesiones, sin JWT). Cualquier persona con acceso al código fuente puede obtener la contraseña.

2. **Enlaces estáticos.**  
   La lista de enlaces está hardcodeada. Para agregar, modificar o eliminar un enlace es necesario modificar el código y recompilar la aplicación.

3. **Sin persistencia de estado de autenticación.**  
   Al recargar la página, se vuelve a solicitar la contraseña (no hay sesión persistente).

4. **Sin backend.**  
   No se puede sincronizar la lista de enlaces entre dispositivos ni tener un historial de accesos.

5. **Sin protección contra fuerza bruta.**  
   No hay límite de intentos ni bloqueo de IP.

### Mejoras futuras propuestas

- **Backend ligero (Node.js + Express o Firebase Functions):**  
  - Mover la autenticación a un servidor con JWT y bcrypt.  
  - Almacenar enlaces en una base de datos (Firestore, MongoDB, SQLite).  
  - Permitir que el usuario administre sus enlaces desde la misma interfaz (CRUD).

- **Sistema de autenticación con OAuth (Google, GitHub):**  
  - Eliminar la contraseña fija y permitir inicio de sesión con cuentas externas.

- **Persistencia de sesión:**  
  - Usar `localStorage` con un token de sesión (duración limitada).

- **Modo sin conexión (PWA):**  
  - Convertir la aplicación en una Progressive Web App para que funcione offline.

- **Internacionalización (i18n):**  
  - Soporte para múltiples idiomas.

- **Tema personalizable:**  
  - Permitir que el usuario guarde su propio tema (colores, fondos) en lugar de solo claro/oscuro.

---

## 7. Licencia

Este proyecto se distribuye bajo la licencia MIT. Consulte el archivo [LICENSE](LICENSE) para más detalles.

---

**Fin del Manual Técnico**

<p align="center">Creado por <a href="https://github.com/migueljerico">@migueljerico</a> y documentado por BazaarLink (DeepSeek V4 Flash (free)) desde la App Asistente de IA · 2026</p>
