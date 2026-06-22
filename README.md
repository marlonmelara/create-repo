# 🚀 create-repo

Script Bash para generar **automáticamente** la estructura base de proyectos web pequeños con HTML, CSS y JavaScript. Ideal para ejercicios de bootcamp, ejemplos educativos y proyectos de estudio.

Crea carpetas, archivos, configuraciones de linters, y repositorio Git listos para comenzar a desarrollar.

---

## ✨ Características

- ✅ **Estructura BEM** desde el inicio
- ✅ **CSS Split**: `base.css` (reset global) + `style.css` (componentes)
- ✅ **Herramientas modernas**: oxlint, stylelint, servor (Rust-fast)
- ✅ **Ordenamiento CSS profesional**: propiedades categorizadas automáticamente
- ✅ **GitHub Pages ready**: copia a `/docs` con `.gitkeep`
- ✅ **VS Code integrado**: auto-formateo al guardar
- ✅ **Git inicializado**: primer commit automático
- ✅ **Zero-config**: todo listo para `pnpm dev`

---

## 📋 Requisitos Previos

Asegúrate de tener instalado:

- **Bash** (incluido en Linux/WSL por defecto)
- **Git**
- **pnpm** (o npm/yarn, pero pnpm se recomienda)

Verifica:

```bash
bash --version
git --version
pnpm --version
```

---

## 📥 Instalación

### **En WSL/Debian**

```bash
# 1. Descarga el script
mkdir -p ~/code-tools
cd ~/code-tools
# (Coloca aquí el archivo create-repo)

# 2. Dale permisos de ejecución
chmod +x create-repo

# 3. Colócalo en el PATH
mkdir -p ~/.local/bin
cp create-repo ~/.local/bin/create-repo

# 4. Agrega ~/.local/bin al PATH de Fish
nano ~/.config/fish/config.fish
```

En el editor, agrega al final:

```fish
set -gx PATH ~/.local/bin $PATH
```

Guarda: `Ctrl+X`, `Y`, `Enter`.

```bash
# 5. Recarga Fish
source ~/.config/fish/config.fish
```

---

### **En Linux Mint (con Fish)**

Idéntico a WSL/Debian:

```bash
mkdir -p ~/.local/bin
cp create-repo ~/.local/bin/create-repo
chmod +x ~/.local/bin/create-repo

nano ~/.config/fish/config.fish
# Agrega: set -gx PATH ~/.local/bin $PATH
source ~/.config/fish/config.fish
```

---

### **En macOS (con Fish)**

```bash
mkdir -p ~/.local/bin
cp create-repo ~/.local/bin/create-repo
chmod +x ~/.local/bin/create-repo

nano ~/.config/fish/config.fish
# Agrega: set -gx PATH ~/.local/bin $PATH
source ~/.config/fish/config.fish
```

---

## 🚀 Cómo Usar

Desde **cualquier directorio**:

```bash
create-repo nombre-del-proyecto
```

Ejemplo:

```bash
create-repo my-grid-exercise
cd my-grid-exercise
pnpm dev
```

---

## 📁 Estructura Generada

```
my-grid-exercise/
├── src/
│   ├── index.html
│   ├── index.js
│   └── css/
│       ├── base.css      (reset, tipografía global, estilos base)
│       └── style.css     (componentes específicos, BEM)
├── docs/
│   └── .gitkeep         (para GitHub Pages)
├── .vscode/
│   └── settings.json    (auto-formateo en VS Code)
├── .gitignore
├── .oxlintrc.json
├── .stylelintrc.json
├── package.json
├── README.md
└── .git/
```

---

## 📦 Dependencias Instaladas

El script instala automáticamente:

| Herramienta                                          | Función                                    |
| ---------------------------------------------------- | ------------------------------------------ |
| **[servor](https://github.com/lukejacksonn/servor)** | Servidor local sin dependencias externas   |
| **[oxlint](https://oxc.rs/)**                        | Linter ultra-rápido para JavaScript (Rust) |
| **oxfmt**                                            | Formateador de código rápido               |
| **[stylelint](https://stylelint.io/)**               | Linter para CSS con validación BEM         |
| **stylelint-config-standard**                        | Reglas CSS estándar                        |
| **stylelint-order**                                  | Ordena propiedades CSS por categoría       |

---

## 🎯 Comandos Disponibles

Una vez dentro del proyecto:

```bash
pnpm dev              # 🚀 Inicia servidor en puerto 1234 + reload automático
pnpm build            # 📦 Copia /src → /docs para GitHub Pages
pnpm lint             # 🔍 Valida JS y CSS (sin cambios)
pnpm lint:all         # ✨ Autoformatea JS, CSS y ordena propiedades
pnpm lint:js          # Valida solo JavaScript
pnpm lint:js:fix      # Autoformatea JavaScript
pnpm lint:css         # Valida solo CSS
pnpm lint:css:fix     # Autoformatea CSS
pnpm format           # Formatea código con oxfmt
```

---

## ⚙️ Configuración

### **CSS: Ordenamiento de Propiedades**

Las propiedades se ordenan automáticamente por categoría:

```
1. Posicionamiento (position, top, right, bottom, left, z-index)
2. Display & Flexbox (display, flex-direction, justify-content, align-items, gap)
3. Grid (grid-template-columns, grid-template-rows, grid-auto-flow)
4. Dimensiones (width, height, min-width, max-width, etc.)
5. Espaciado (margin, padding)
6. Tipografía (font, font-size, line-height, color)
7. Bordes (border, border-radius, outline)
8. Fondo (background, background-color, background-image)
9. Transformaciones (transform, transition, animation)
10. Efectos visuales (box-shadow, filter, opacity)
11. Interactividad (cursor, pointer-events, overflow)
```

### **BEM: Nomenclatura de Clases**

El linter valida automáticamente la nomenclatura BEM:

```css
/* ✅ Válido */
.main {
}
.main__h1 {
}
.btn--primary {
}
.card__image-wrapper {
}

/* ❌ Inválido */
.Main {
} /* mayúscula */
.main-h1 {
} /* debe ser __h1 */
.btn_primary {
} /* debe ser --primary */
```

### **VS Code: Auto-formateo**

El archivo `.vscode/settings.json` configura auto-formateo al guardar:

```json
{
  "[css]": {
    "editor.defaultFormatter": "stylelint.vscode-stylelint"
  },
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.stylelint": "explicit"
  }
}
```

Instala la extensión de **Stylelint** en VS Code para que funcione.

---

## 🔄 GitHub Pages

El script genera `/docs` listo para GitHub Pages:

1. **Crea el proyecto:**

   ```bash
   create-repo mi-sitio
   cd mi-sitio
   ```

2. **Desarrolla tu código** en `/src`

3. **Prepara para publicar:**

   ```bash
   pnpm build
   ```

4. **Sube a GitHub:**

   ```bash
   git remote add origin https://github.com/tuusuario/mi-sitio.git
   git push -u origin main
   ```

5. **Activa GitHub Pages:**
   - Ve a Settings → Pages
   - Selecciona `main` branch, carpeta `/docs`
   - Guarda

Tu sitio estará en: `https://tuusuario.github.io/mi-sitio/`

---

## 📝 Personalización

### **Cambiar el puerto de desarrollo**

Edita `package.json`:

```json
"dev": "servor src index.html 5000 --reload"   // Puerto 5000
```

### **Agregar más linters**

Edita `package.json` en `devDependencies` e instala:

```bash
pnpm add -D nombre-del-paquete
```

### **Configurar ESLint adicional**

El script usa oxlint (más rápido). Si prefieres ESLint:

```bash
pnpm add -D eslint eslint-config-standard
```

Crea `.eslintrc.json` y configura según necesites.

---

## 🐛 Solución de Problemas

### **Error: "create-repo: command not found"**

```bash
# Verifica que está en el PATH
which create-repo

# Si no aparece nada, recarga Fish
source ~/.config/fish/config.fish

# O verifica que ~/.local/bin existe
ls -la ~/.local/bin/create-repo
```

### **Error: "pnpm: command not found"**

Instala pnpm:

```bash
npm install -g pnpm
```

### **Stylelint no formatea en VS Code**

Instala la extensión:

- Abre VS Code
- Ctrl+Shift+X
- Busca "Stylelint"
- Instala `stylelint.vscode-stylelint`

### **El servidor no inicia en el puerto 1234**

Puede estar en uso. Cambia en `package.json`:

```json
"dev": "servor src index.html 3000 --reload"
```

---

## 📚 Recursos

- **[Servor - Zero-dep local server](https://github.com/lukejacksonn/servor)**
- **[Stylelint - CSS Linter](https://stylelint.io/)**
- **[BEM - Block Element Modifier](https://bem.info/)**
- **[Oxc - Rust Linter](https://oxc.rs/)**

---

## 📄 Licencia

Libre para usar, modificar y distribuir.

---

## 💬 Uso Educativo

Este script está diseñado para:

- 📚 Estudiantes de bootcamp
- 👨‍🏫 Profesores de desarrollo web
- 🎓 Ejercicios de práctica
- 📖 Ejemplos educativos

Perfecto para enseñar **estructura BEM**, **GitHub Pages**, y **herramientas profesionales modernas** desde el inicio.

---
