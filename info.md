# 📋 INFORMACIÓN DEL PROYECTO - PORTFOLIO ACADÉMICO

## 🎯 ¿DE QUÉ SE TRATA ESTE PROYECTO?

Este es un **sitio web de portfolio académico** construido con **Hugo**, un generador de sitios estáticos. Específicamente, utiliza el tema **Hugo Academic CV** (ahora llamado Hugo Blox Builder) que está diseñado para:

- **Académicos e investigadores** que quieren mostrar su trabajo
- **Profesionales** que buscan un portfolio elegante y profesional
- **Desarrolladores** que quieren un sitio web personal moderno

### 🏗️ ESTRUCTURA DEL PROYECTO

```
portfolio/
├── config/_default/          # Configuración principal
│   ├── hugo.yaml            # Configuración de Hugo
│   ├── params.yaml          # Parámetros del sitio
│   ├── languages.yaml       # Configuración de idiomas
│   ├── menus.yaml           # Configuración de menús
│   └── module.yaml          # Configuración de módulos
├── content/                 # Contenido del sitio
│   ├── _index.md           # Página principal
│   ├── authors/admin/      # Información del autor
│   ├── post/              # Blog posts
│   ├── project/           # Proyectos
│   ├── publication/       # Publicaciones académicas
│   ├── teaching/          # Cursos/enseñanza
│   └── event/             # Eventos/conferencias
├── assets/                # Recursos estáticos
├── layouts/               # Plantillas personalizadas
├── static/                # Archivos estáticos
└── go.mod                 # Dependencias de Go
```

## 🛠️ TECNOLOGÍAS UTILIZADAS

### **Lenguaje Principal:**
- **Hugo** (Go-based static site generator)
- **Go** (para las dependencias y módulos)

### **Frontend:**
- **HTML/CSS/JavaScript**
- **Tailwind CSS** (framework de estilos)
- **Hugo Blox Builder** (sistema de bloques)

### **Características:**
- ✅ **Sitio estático** (no necesita servidor)
- ✅ **Responsive design**
- ✅ **SEO optimizado**
- ✅ **Sistema de bloques** (drag & drop)
- ✅ **Markdown** para contenido
- ✅ **Búsqueda integrada** (Pagefind)

## 📝 CÓMO MANIPULAR EL PROYECTO

### **1. Configuración Básica**

**Archivos principales a modificar:**

#### `config/_default/hugo.yaml`
```yaml
title: "Tu Nombre - Portfolio"  # Cambiar título
baseURL: 'https://tu-dominio.com/'  # Cambiar URL
```

#### `config/_default/params.yaml`
```yaml
# Información personal
header:
  navbar:
    logo:
      text: "Tu Nombre"  # Cambiar nombre

# SEO
marketing:
  seo:
    description: 'Tu descripción personal'
```

### **2. Contenido Personal**

#### `content/authors/admin/_index.md`
- **Información personal**: nombre, rol, organizaciones
- **Redes sociales**: GitHub, LinkedIn, Twitter, etc.
- **Educación**: títulos, instituciones, fechas
- **Experiencia laboral**: posiciones, empresas, responsabilidades
- **Habilidades**: técnicas y hobbies
- **Idiomas**: nivel de dominio
- **Premios**: certificaciones y reconocimientos

#### `content/_index.md`
- **Página principal**: biografía, publicaciones destacadas, proyectos
- **Secciones**: usar bloques predefinidos (resume-biography, collection, etc.)

### **3. Agregar Contenido**

#### **Nuevo Post (Blog)**
```bash
# Crear en content/post/mi-nuevo-post/
# Archivo: index.md
---
title: 'Mi Nuevo Post'
date: 2024-01-15
summary: 'Resumen del post'
tags: ['tag1', 'tag2']
---
```

#### **Nuevo Proyecto**
```bash
# Crear en content/project/mi-proyecto/
# Archivo: index.md
---
title: 'Mi Proyecto'
summary: 'Descripción del proyecto'
tags: ['python', 'machine-learning']
image:
  filename: featured.jpg
---
```

#### **Nueva Publicación**
```bash
# Crear en content/publication/mi-paper/
# Archivo: index.md
---
title: 'Título del Paper'
authors: ['Tu Nombre']
date: 2024-01-15
publication_types: ['1']  # 1=Journal, 2=Conference
---
```

## 🚀 DESPLIEGUE EN RENDER

### **Configuración Actual**
El proyecto ya tiene configuración para **Netlify**, pero Render es muy similar.

### **Pasos para Render:**

1. **Crear cuenta en Render.com**

2. **Conectar repositorio GitHub**
   - Subir el proyecto a GitHub
   - Conectar desde Render

3. **Configurar build en Render:**
   ```bash
   Build Command: hugo --gc --minify
   Publish Directory: public
   ```

4. **Variables de entorno (opcional):**
   ```
   HUGO_VERSION: 0.136.5
   HUGO_ENV: production
   ```

5. **Configuración adicional para Render:**
   Crear archivo `render.yaml`:
   ```yaml
   services:
     - type: web
       name: portfolio
       env: static
       buildCommand: hugo --gc --minify
       staticPublishPath: ./public
       routes:
         - type: rewrite
           source: /*
           destination: /index.html
   ```

### **Cambios necesarios para Render:**

1. **Modificar `netlify.toml` → `render.yaml`**
2. **Actualizar `baseURL` en `hugo.yaml`**
3. **Configurar dominio personalizado en Render**

## 🔧 DESARROLLO LOCAL

### **Requisitos:**
- **Hugo Extended** (versión 0.136.5 o superior)
- **Go** (para módulos)

### **Comandos principales:**
```bash
# Instalar dependencias
hugo mod get

# Servidor de desarrollo
hugo server -D

# Construir para producción
hugo --gc --minify

# Limpiar cache
hugo --gc
```

### **Estructura de desarrollo:**
- **`hugo server`**: Servidor local en `http://localhost:1313`
- **Hot reload**: Cambios automáticos al editar archivos
- **Draft posts**: Usar `draft: true` en frontmatter

## 📊 SISTEMA DE BLOQUES

El tema usa un sistema de bloques configurables:

### **Bloques disponibles:**
- `resume-biography`: Biografía personal
- `collection`: Lista de posts/proyectos/publicaciones
- `markdown`: Contenido personalizado
- `cta-card`: Llamadas a la acción
- `resume-experience`: Experiencia laboral
- `resume-skills`: Habilidades
- `resume-awards`: Premios

### **Ejemplo de bloque:**
```yaml
- block: collection
  content:
    title: "Mis Proyectos"
    filters:
      folders:
        - project
  design:
    view: article-grid
    columns: 3
```

## 🎨 PERSONALIZACIÓN

### **Colores y temas:**
```yaml
# En params.yaml
appearance:
  mode: system  # light, dark, system
  color: emerald  # emerald, blue, red, etc.
```

### **CSS personalizado:**
- Crear `assets/css/custom.css`
- Importar en `layouts/partials/custom_head.html`

### **Plantillas personalizadas:**
- Modificar archivos en `layouts/partials/`
- Crear nuevos layouts en `layouts/`

## 🔍 BÚSQUEDA Y SEO

### **Búsqueda integrada:**
- **Pagefind**: Búsqueda estática incluida
- **Configuración**: Automática en build

### **SEO optimizado:**
- Meta tags automáticos
- Open Graph tags
- Twitter Cards
- Sitemap automático

## 📱 CARACTERÍSTICAS RESPONSIVE

- **Mobile-first design**
- **Navegación adaptativa**
- **Imágenes optimizadas**
- **Tipografía responsive**

## 🚨 CONSIDERACIONES IMPORTANTES

### **No necesita API porque:**
- ✅ Es un sitio **estático**
- ✅ Todo el contenido se genera en build time
- ✅ No hay base de datos
- ✅ No hay servidor backend

### **Limitaciones:**
- ❌ No hay formularios dinámicos (sin backend)
- ❌ No hay comentarios (sin base de datos)
- ❌ No hay autenticación de usuarios

### **Soluciones para funcionalidad dinámica:**
- **Formularios**: Netlify Forms, Formspree
- **Comentarios**: Disqus, Utterances
- **Analytics**: Google Analytics, Plausible
- **Búsqueda**: Pagefind (ya incluido)

## 🎯 PRÓXIMOS PASOS RECOMENDADOS

1. **Personalizar información personal** en `content/authors/admin/_index.md`
2. **Cambiar configuración** en `config/_default/params.yaml`
3. **Agregar contenido** (posts, proyectos, publicaciones)
4. **Personalizar diseño** (colores, layout)
5. **Configurar dominio** en Render
6. **Optimizar SEO** (meta tags, descripciones)

---

**¡Tu portfolio académico está listo para ser personalizado y desplegado! 🚀** 