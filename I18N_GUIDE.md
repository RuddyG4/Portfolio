# Internacionalización (i18n) - Portfolio

## Estructura creada

He configurado el sistema de i18n para soportar español (ES) e inglés (EN).

### Archivos creados:

1. **`src/i18n/ui.ts`** - Contiene todas las traducciones y funciones helper
2. **`src/components/LanguagePicker.astro`** - Selector de idioma
3. **`src/pages/en/`** - Carpeta para las páginas en inglés

## Cómo usar las traducciones

### 1. En un componente Astro:

```astro
---
import { getLangFromUrl, useTranslations } from "../i18n/ui";

const lang = getLangFromUrl(Astro.url);
const t = useTranslations(lang);
---

<h1>{t('hero.title')}</h1>
<p>{t('hero.description')}</p>
```

### 2. Estructura de URLs:

- Español (default): `https://tu-dominio.com/` 
- Inglés: `https://tu-dominio.com/en/`

### 3. Agregar el selector de idioma al Header:

```astro
---
import LanguagePicker from "./LanguagePicker.astro";
import { getLangFromUrl } from "../i18n/ui";

const lang = getLangFromUrl(Astro.url);
---

<header>
  <!-- Tu contenido actual -->
  <LanguagePicker currentLang={lang} />
</header>
```

## Próximos pasos para completar la implementación:

### Opción A: Actualizar componentes existentes (Recomendado)

1. Mover `/src/pages/index.astro` a `/src/pages/[lang]/index.astro`
2. Actualizar cada componente para usar `t()` en lugar de texto hardcodeado
3. Los datos (servicios, proyectos) pueden mantener su estructura actual

### Opción B: Crear versión en inglés separada

1. Duplicar `/src/pages/index.astro` a `/src/pages/en/index.astro`
2. Traducir manualmente los textos en la versión inglesa
3. Más fácil pero menos mantenible

## Ejemplo de cómo actualizar un componente:

### Antes (Hero.astro):
```astro
<h1>Smart Web <span>Business solutions</span></h1>
```

### Después (Hero.astro):
```astro
---
import { getLangFromUrl, useTranslations } from "../i18n/ui";
const lang = getLangFromUrl(Astro.url);
const t = useTranslations(lang);
---

<h1>{t('hero.title')} <span>{t('hero.titleHighlight')}</span></h1>
```

## Agregar nuevas traducciones:

En `src/i18n/ui.ts`, agrega las claves en ambos idiomas:

```typescript
export const ui = {
  es: {
    "nueva.clave": "Texto en español",
  },
  en: {
    "nueva.clave": "Text in English",
  },
};
```

## ¿Quieres que implemente todo esto en los componentes existentes?

Puedo actualizar automáticamente todos los componentes para usar las traducciones. Solo confirma y procedo con la implementación completa.
