# 🔗 Portal de Enlaces Privados — Dashboard Personal

![Google AI Studio](https://img.shields.io/badge/Google%20AI%20Studio-Generación%20de%20código-4285F4?style=for-the-badge&logo=google&logoColor=white)
![Lovable](https://img.shields.io/badge/Lovable-React%20%2B%20Tailwind-FF4F64?style=for-the-badge)
![React](https://img.shields.io/badge/React-Frontend-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Estado](https://img.shields.io/badge/Estado-Publicado-4CAF50?style=for-the-badge)
![Tipo](https://img.shields.io/badge/Tipo-Herramienta%20Personal-FF6B6B?style=for-the-badge)

> **Proyecto Personal — Generación de Código Asistida por IA**  
> SPA como **hub centralizado de accesos directos** privados, con autenticación y modo oscuro

---

## 🔗 Acceso a la Aplicación

[![Ver App en Producción](https://img.shields.io/badge/🚀%20Ver%20App-mis--enlaces--privados.lovable.app-FF4F64?style=for-the-badge&logo=lovable&logoColor=white)](https://mis-enlaces-privados.lovable.app)

> 🔒 Acceso protegido por contraseña — herramienta de uso personal

---

## 📋 Descripción del Proyecto

**Portal de Enlaces Privados** es una Single Page Application (SPA) diseñada como dashboard personal de accesos directos. Centraliza enlaces de uso frecuente en una interfaz moderna, segura y optimizada, con capa de autenticación previa que garantiza que el contenido es accesible únicamente por el usuario autorizado.

El proyecto se desarrolló mediante un **enfoque híbrido de generación de código asistida por IA**: arquitectura inicial en Google AI Studio + migración a React con Lovable + capa de seguridad con contraseña.

---

## 🛠️ Flujo de Desarrollo

### Fase 1 — Conceptualización y Estructura (Google AI Studio)

Se utilizó **Google AI Studio** para definir la arquitectura técnica y el diseño visual inicial, generando una base sólida en **HTML5, Tailwind CSS y Vanilla JavaScript**.

#### Prompt de ingeniería utilizado:

```text
Role: Senior Front-End Developer & UI/UX Expert

Task: Generate the complete, production-ready code for a modern Single Page Application (SPA)
that serves as a Dashboard / Link Portal. It will act as a centralized shortcut hub for a
specific set of URLs.

Technical Specifications:
- Stack: HTML5, Tailwind CSS (via CDN) and Vanilla JavaScript
- Output Format: Single unified index.html with <style> and <script> tags

UI/UX Requirements:
- Clean, fully responsive design
- Functional Dark/Light mode toggle
- Grid layout with interactive Cards for each URL
- Card Design: hover elevation effect, display name, description, CTA button
- CRITICAL LINK BEHAVIOR: All links MUST use target="_blank" rel="noopener noreferrer"
- Functional real-time search bar to filter cards by name or description
```

#### Estructura de datos generada (fragmento):

```javascript
const links = [
    { name: "Servicio 1", url: "[URL_PRIVADA]", desc: "Servicio 1." },
    { name: "Servicio 2", url: "[URL_PRIVADA]", desc: "Servicio 2." },
    { name: "Servicio 3", url: "[URL_PRIVADA]", desc: "Servicio 3." }
];

function renderCards(filter = '') {
    const filtered = links.filter(l =>
        l.name.toLowerCase().includes(filter.toLowerCase()) ||
        l.desc.toLowerCase().includes(filter.toLowerCase())
    );
    // renderizado dinámico de tarjetas
}
```

---

### Fase 2 — Migración y Escalabilidad (Lovable)

La base técnica se migró a **Lovable** para transformar el código a arquitectura **React + Tailwind CSS**.

#### Prompt de migración:

```text
I have a fully functional SPA built with Vanilla HTML, Tailwind CSS and JavaScript.
Convert this code into your native React + Tailwind architecture.

Critical requirements:
1. Maintain exact layout, colors, and Dark/Light mode toggle (using React state)
2. Keep real-time search filtering for cards
3. Keep smooth hover elevation effect (translateY(-5px))
4. CRITICAL: Keep target="_blank" rel="noopener noreferrer" on all anchor tags
5. Pre-load the exact same 3 links and descriptions from the original JS array
```

---

### Fase 3 — Implementación de Seguridad

Se añadió una capa de autenticación mediante prompt a Lovable:

```text
¿Puedes añadir que pida contraseña antes de entrar en el portal de enlaces?
```

---

## ✨ Funcionalidades

| Funcionalidad | Descripción |
|---|---|
| **Acceso protegido** | Autenticación previa con contraseña antes de mostrar los enlaces |
| **Buscador en tiempo real** | Filtrado instantáneo de tarjetas mediante React State |
| **Modo oscuro/claro** | Persistencia de tema mediante localStorage |
| **Diseño responsivo** | Adaptabilidad total a móviles y escritorio |
| **Apertura segura** | Todos los links con `target="_blank"` y `rel="noopener noreferrer"` |

---

## 🧰 Tecnologías utilizadas

| Herramienta | Uso |
|---|---|
| **Google AI Studio** | Generación del código base (HTML5 + Tailwind + Vanilla JS) |
| **Lovable** | Migración a React, refinamiento y hosting |
| **React** | Framework frontend final |
| **Tailwind CSS** | Sistema de diseño |

---

## 📚 Contexto formativo

Este proyecto surge como herramienta de **productividad personal** desarrollada aplicando técnicas de prompt engineering y generación de código asistida por IA. Refleja competencias en diseño de prompts avanzados para ingeniería de software, comprensión de arquitecturas frontend y uso estratégico de herramientas no-code e IA generativa.

---

<p align="center">
  <sub>Desarrollado por <a href="https://github.com/migueljerico">@migueljerico</a> · 2026</sub>
</p>
