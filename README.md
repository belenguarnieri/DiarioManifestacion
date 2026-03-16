# 🌿 Diario de Manifestación y Agradecimiento — 30 días

Un ritual diario de conexión personal, construido como una aplicación web estática que funciona directamente en el navegador, sin necesidad de instalar nada.

---

## ✨ ¿Qué es esto?

Una aplicación de journaling guiada para 30 días, diseñada para:

- 🌿 Bajar la ansiedad
- 💛 Reconectarte con vos misma
- ✨ Practicar gratitud y valoración personal
- ⏳ Crear un pequeño espacio diario para vos

Cada sesión lleva entre 10 y 20 minutos e incluye respiración guiada, seis secciones de escritura y reflexiones con inteligencia artificial.

---

## 🗂 Estructura del ritual diario

| Sección | Tiempo | Descripción |
|---|---|---|
| Check-in emocional | 2 min | Escribir sin filtro cómo estás hoy |
| Gratitud | 3–5 min | 3 cosas por las que agradecés |
| Valorarme | 2–3 min | Reconocer tu propio valor |
| Reconectar | 3–5 min | Pregunta de introspección del día |
| Manifestación | 2–3 min | Tu intención o afirmación |
| Cierre | 1 min | Un permiso para vos |

Más una **revisión semanal** cada 7 días y una **guía anti-loop mental** disponible en cualquier momento.

---

## 🚀 Cómo usar

### Opción 1 — Abrir directamente (sin instalar nada)

1. Descargá el archivo `diario-manifestacion-30dias.html`
2. Hacé doble clic para abrirlo en tu navegador
3. Listo

### Opción 2 — GitHub Pages

1. Hacé fork de este repositorio
2. Vas a `Settings → Pages`
3. En "Source" elegís `main` y `/ (root)`
4. GitHub te da una URL pública tipo `https://tu-usuario.github.io/nombre-repo`

> **Nota sobre la IA:** las reflexiones personalizadas con IA funcionan en local (cuando abrís el archivo con tu propia API key configurada) pero no desde GitHub Pages por razones de seguridad — ver sección de configuración.

---

## 💾 ¿Dónde se guardan tus entradas?

Todas las entradas se guardan con `localStorage` en tu navegador. Esto significa:

- ✅ No se envían a ningún servidor
- ✅ Funcionan sin internet
- ✅ Persisten entre sesiones en el mismo dispositivo y navegador
- ⚠️ Si usás otro navegador o dispositivo, las entradas no aparecerán allí

---

## 🧠 Guía Anti-Loop Mental

Disponible en cualquier momento desde el botón "Estoy en loop mental". Incluye 6 categorías de preguntas basadas en:

- Terapia cognitiva (CBT)
- Coaching somático
- Técnicas de regulación emocional
- Mindfulness

Las categorías son: preguntas de realidad, distancia emocional, romper el modo escasez, reconexión con el cuerpo, poder personal y cambio de estado rápido.

---

## 🤖 Configurar reflexiones con IA (opcional)

Las reflexiones con IA usan la API de Anthropic. Para habilitarlas de forma segura:

### En local

Abrí `diario-manifestacion-30dias.html` en un editor de texto, buscá la función `getAI` y reemplazá la URL del fetch por tu endpoint propio.

### Con Vercel (recomendado para uso propio)

1. Creá una cuenta gratuita en [vercel.com](https://vercel.com)
2. Creá un proyecto nuevo y agregá esta función en `/api/chat.js`:

```js
export default async function handler(req, res) {
  if (req.method !== 'POST') return res.status(405).end();

  const response = await fetch('https://api.anthropic.com/v1/messages', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'x-api-key': process.env.ANTHROPIC_API_KEY,
      'anthropic-version': '2023-06-01',
    },
    body: JSON.stringify(req.body),
  });

  const data = await response.json();
  res.status(200).json(data);
}
```

3. En Vercel, vas a `Settings → Environment Variables` y agregás `ANTHROPIC_API_KEY` con tu key
4. En el HTML, reemplazás `https://api.anthropic.com/v1/messages` por `https://tu-proyecto.vercel.app/api/chat`

### Con Netlify Functions

Mismo concepto, pero el archivo va en `/netlify/functions/chat.js`.

---

## 📁 Archivos

```
/
├── diario-manifestacion-30dias.html   # La aplicación completa (un solo archivo)
└── README.md                          # Este archivo
```

---

## 🛠 Tecnologías

- HTML, CSS y JavaScript vanilla — sin frameworks ni dependencias
- Google Fonts (Playfair Display + DM Sans)
- `localStorage` para persistencia de datos
- API de Anthropic para reflexiones con IA (opcional)

---

## 🌱 Filosofía del proyecto

> No busques hacerlo perfecto. Aunque escribas 5 minutos, ya cuenta.
> No releas inmediatamente lo que escribiste. No analices, solo escribí.

Este diario está pensado para crear un espacio pequeño pero consistente de conexión con una misma, no para ser otra tarea en la lista.

---

## 📄 Licencia

Libre para uso personal. Si lo compartís o modificás, se agradece la mención. 💛
