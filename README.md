# 100 Programadores Dijeron 🎯

Juego interactivo estilo **100 Mexicanos Dijeron / Family Feud** desarrollado para el AWS User Group Mariachi Builders. Diseño fiel al tablero físico original: arco azul royal, fondo amarillo, bombillas animadas y ranuras tipo persiana.

---

## 🗂️ Estructura del proyecto

```
📁 /
├── index.html          → 📺 Tablero TV principal  (proyectar en pantalla grande)
├── admin.html          → 🎛️  Panel del Conductor / Admin
├── buzzer.html         → ⚡ Cara a Cara — botones de buzzer para los equipos
├── fastmoney.html      → 💰 Dinero Rápido — Gran Final
├── amplify.yml         → Configuración de despliegue en AWS Amplify
├── logo ug mb nuevo.png
└── AWS_logo_RGB_WHT.png
```

---

## 📺 Páginas

### `index.html` — Tablero TV
- Se proyecta en pantalla grande durante el juego
- Muestra marcadores, pregunta activa, respuestas con flip 3D, strikes y banners
- Solo lectura — se controla desde `admin.html`

### `admin.html` — Panel Conductor
- **Tab Juego Principal**: control de rondas, revelar respuestas una a una, strikes, robo de puntos, multiplicadores (x1/x2/x3), entregar bote
- **Tab Dinero Rápido**: selector de equipo que juega, nombres editables de jugadores, revelar respuesta y puntos por separado, timers de 25s, declarar ganador
- **Tab Configuración**: banco de preguntas editable en JSON, ajuste de equipos

### `buzzer.html` — Cara a Cara
- Dos botones gigantes para los capitanes de cada equipo
- Detecta quién presionó primero con precisión en milisegundos
- Teclado: `A` = Equipo A, `L` = Equipo B

### `fastmoney.html` — Dinero Rápido
- Tablero de 5 preguntas × 2 jugadores con el mismo estilo visual
- Respuesta y puntos se revelan en pasos separados
- Overlay de celebración con confetti al declarar ganador

---

## 🔊 Sonidos

Los sonidos oficiales del programa se cargan desde MyInstants:

| Acción | Sonido |
|---|---|
| Strike (X) | MP3 personalizado |
| Correcto / Revelar | MyInstants oficial |
| Nadie acertó | MyInstants incorrecto |
| Buzzer Cara a Cara | MP3 personalizado |
| Triunfo / Bote entregado | MyInstants oficial |
| Respuesta Repetida (Dinero Rápido) | Buzzer eléctrico sintetizado |

---

## 🔄 Sincronización

Todas las páginas se sincronizan en tiempo real mediante:
- `BroadcastChannel('100_prog_dijeron')` — para pestañas en el mismo navegador
- `localStorage('100_prog_state')` — para persistencia y respaldo

---

## 🎮 Flujo de juego

1. Abrir `admin.html` en la laptop del conductor
2. Proyectar `index.html` en pantalla grande
3. Abrir `buzzer.html` en tablets/móviles de los capitanes (opcional)
4. Al terminar las 4 rondas → abrir `fastmoney.html` en el proyector
5. Seleccionar equipo ganador en admin → Tab Dinero Rápido

---

## ☁️ Despliegue en AWS Amplify

1. Subir este repositorio a GitHub
2. En [AWS Amplify Console](https://console.aws.amazon.com/amplify/) → **New app → Host web app**
3. Conectar el repo → rama `main`
4. Amplify detecta el `amplify.yml` automáticamente
5. Deploy listo — sitio estático sin backend

> El `amplify.yml` ya está configurado para servir todos los archivos desde la raíz.

---

## 🛠️ Tecnologías

- HTML5 + CSS3 + JavaScript vanilla (sin frameworks)
- [Tailwind CSS](https://tailwindcss.com/) via CDN (admin y buzzer)
- [Google Fonts](https://fonts.google.com/): Anton, Orbitron, Inter
- [Lucide Icons](https://lucide.dev/) via CDN
- Web Audio API para sonidos sintetizados
- BroadcastChannel API para sincronización entre pestañas

---

## 🏗️ AWS UG Mariachi Builders

Desarrollado para los eventos del [AWS User Group Mariachi Builders](https://www.meetup.com/aws-user-group-mariachi-builders/).
