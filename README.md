# 🔗 Portal de Enlaces Privados — Dashboard Personal

![HTML5](https://img.shields.io/badge/HTML5-%23E34F26?style=for-the-badge&logo=html5&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-%2338B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-%23F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![React](https://img.shields.io/badge/React-%2361DAFB?style=for-the-badge&logo=react&logoColor=black)
![Estado](https://img.shields.io/badge/Estado-Publicado-%234CAF50?style=for-the-badge)
![Licencia](https://img.shields.io/badge/Licencia-MIT-%23FF6B6B?style=for-the-badge)

> **Hub centralizado de accesos directos privados**, con autenticación y modo oscuro, generado con asistencia de IA.

---

## 🔗 Acceso / Demo

[![Ver App en Producción](https://img.shields.io/badge/🚀%20Ver%20App-mis--enlaces--privados.lovable.app-FF4F64?style=for-the-badge&logo=lovable&logoColor=white)](https://mis-enlaces-privados.lovable.app)

> 🔒 Acceso protegido por contraseña — herramienta de uso personal

## 📋 Descripción

**Portal de Enlaces Privados** es una Single Page Application (SPA) que funciona como un dashboard personal de accesos directos. Centraliza enlaces de uso frecuente (servicios, herramientas, plataformas) en una interfaz moderna, segura y optimizada. Incluye una capa de autenticación previa que garantiza que el contenido solo es accesible por el usuario autorizado.

El proyecto se desarrolló mediante un **enfoque híbrido de generación de código asistida por IA**: la arquitectura inicial se concibió en Google AI Studio generando HTML5 + Tailwind CSS + Vanilla JavaScript, y posteriormente se migró a React con Lovable para escalabilidad y despliegue. La seguridad (pantalla de contraseña) se añadió mediante un prompt específico.

Este portal está dirigido a cualquier persona que necesite un punto único de acceso a sus recursos web más importantes, de forma rápida, con búsqueda en tiempo real y en un entorno visual agradable (modo oscuro/claro).

## ✨ Funcionalidades

| Funcionalidad | Descripción |
|---|---|
| **Acceso protegido** | Autenticación previa con contraseña antes de mostrar los enlaces |
| **Buscador en tiempo real** | Filtrado instantáneo de tarjetas mediante React State |
| **Modo oscuro/claro** | Cambio de tema con persistencia en localStorage |
| **Diseño responsivo** | Adaptabilidad total a móviles y escritorio |
| **Apertura segura** | Todos los enlaces se abren con `target="_blank"` y `rel="noopener noreferrer"` |
| **Tarjetas interactivas** | Efecto hover de elevación, nombre, descripción y botón de acción |

## ⚙️ Instalación

Dado que la aplicación está desplegada directamente en Lovable y no requiere instalación local para su uso, los siguientes pasos describen cómo ejecutarla de forma local si se desea modificar o personalizar:

1. **Clonar el repositorio** (si estuviera disponible el código fuente React):
   ```bash
   git clone https://github.com/migueljerico/portal-enlaces-privados-documentation.git
   cd portal-enlaces-privados-documentation
   ```

2. **Instalar dependencias** (asumiendo `npm` y `package.json`):
   ```bash
   npm install
   ```

3. **Iniciar el servidor de desarrollo**:
   ```bash
   npm run dev
   ```

4. **Abrir en el navegador** la URL que indique la terminal (normalmente `http://localhost:5173`).

> **Nota:** Este repositorio contiene solo la documentación del proyecto. El código fuente original de la aplicación se encuentra en Lovable y no está incluido aquí.

## 🚀 Uso

El siguiente fragmento de código muestra la lógica de filtrado de tarjetas que se utiliza en la aplicación (basado en el prototipo inicial de Vanilla JavaScript):

```javascript
const links = [
    { name: "Servicio 1", url: "https://ejemplo1.com", desc: "Descripción del servicio 1." },
    { name: "Servicio 2", url: "https://ejemplo2.com", desc: "Descripción del servicio 2." },
    { name: "Servicio 3", url: "https://ejemplo3.com", desc: "Descripción del servicio 3." }
];

function renderCards(filter = '') {
    const filtered = links.filter(l =>
        l.name.toLowerCase().includes(filter.toLowerCase()) ||
        l.desc.toLowerCase().includes(filter.toLowerCase())
    );
    // Renderizado dinámico de tarjetas en el DOM
    const container = document.getElementById('card-container');
    container.innerHTML = filtered.map(l =>
        `<div class="card">
            <h3>${l.name}</h3>
            <p>${l.desc}</p>
            <a href="${l.url}" target="_blank" rel="noopener noreferrer">Ir al servicio</a>
         </div>`
    ).join('');
}
```

Este fragmento se integra con un campo de búsqueda que actualiza el estado de filtro en tiempo real, tanto en la versión Vanilla como en la versión React (donde se usa `useState` y `useEffect`).

## 📁 Estructura del proyecto

```
portal-enlaces-privados-documentation/
├── README.md
└── LICENSE
```

> La estructura completa de la aplicación React desplegada en Lovable incluye componentes como `App.jsx`, `Card.jsx`, `SearchBar.jsx`, `ThemeToggle.jsx`, `Login.jsx`, etc., pero no están incluidos en este repositorio de documentación.

## 🛠️ Tecnologías

| Herramienta | Versión/Detalle | Uso en el proyecto |
|---|---|---|
| **Google AI Studio** | — | Generación del código base (HTML5 + Tailwind + Vanilla JS) |
| **Lovable** | — | Migración a React, refinamiento y hosting |
| **React** | 18.x | Framework frontend principal (SPA) |
| **Tailwind CSS** | 3.x | Sistema de diseño utilitario responsivo |
| **HTML5** | — | Estructura base inicial |
| **JavaScript (Vanilla)** | ES6 | Lógica de filtrado y renderizado en el prototipo |
| **npm** | 9.x (estimado) | Gestor de dependencias (si se ejecuta localmente) |

## 📚 Contexto formativo

Este proyecto surge como herramienta de **productividad personal** desarrollada aplicando técnicas de prompt engineering y generación de código asistida por IA. Refleja competencias en:

- Diseño de prompts avanzados para ingeniería de software.
- Comprensión de arquitecturas frontend (SPA, componentes React, estado).
- Uso estratégico de herramientas no-code e IA generativa (Google AI Studio + Lovable).
- Migración de prototipos a frameworks modernos.
- Implementación de funcionalidades de seguridad y UX (autenticación, modo oscuro, búsqueda en tiempo real).

El proceso documentado en las fases del README demuestra un flujo de trabajo realista entre la generación de código por IA y el refinamiento humano para obtener un producto funcional y desplegado en producción.

---

<p align="center">Creado por <a href="https://github.com/migueljerico">@migueljerico</a> y documentado por BazaarLink (DeepSeek V4 Flash (free)) desde la App Asistente de IA · 2026</p>
