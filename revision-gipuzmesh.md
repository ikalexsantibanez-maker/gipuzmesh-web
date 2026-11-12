# Revisión de gipuzmesh-web.html y gipuzmesh-web.css

> **Para usar en otro chat:** pega este archivo junto con tu HTML y tu CSS y escribe algo como
> *"Ayúdame a resolver los puntos de esta revisión, empezando por el punto X"*.
>
> **Importante sobre los números de línea:** corresponden a la versión que se revisó (HTML de 407 líneas, CSS de 746 líneas).
> Si has editado los archivos desde entonces, las líneas se habrán movido. Busca por el contenido que indica la tabla.

---

## 0. Ya resuelto

- [x] **Sección "Informazioa" sin cerrar.** Faltaban tres cierres justo después del `</article>` de la línea 250 (`</div>` del grid de la línea 103, `</div>` del container de la línea 91 y `</section>` de la línea 90). Con eso, todo lo posterior en el HTML sube 3 líneas.

---

## 1. Errores pendientes

### HTML

- [ ] **Líneas 4-5: `<link>` antes de `<meta charset>`.** Mueve la línea 5 (`<meta charset>`) encima de la 4.
- [ ] **Línea 15: logo sin tamaño.** El `<img>` no tiene clase y el CSS no tiene regla `.logo img`. Ver CSS más abajo.
- [ ] **Línea 106: `<div>` sin clase.** Debería ser `class="widget-header"`, igual que la línea 173.
- [ ] **Líneas 144, 154, 243: listas `<ul>` sin sangría.** Ver punto del reset en CSS.
- [ ] **Líneas 182-249: bloque de análisis sin CSS.** Clases sin ninguna regla en el CSS: `analisia-container` (182), `taula-box` (183), `table` (185-227), `posatiboa` (201, 208, 215, 224), `grafikoak-box` (231), `grafiko-wrapper` (233), imágenes (234-235), `ondorioak-box` (241-249).
- [ ] **Líneas 273-300 y 307-309: radios del calendario y turnos.** No se pueden usar con teclado por el `display: none` del CSS (ver CSS).
- [ ] **Líneas 387-389: `<div class="map-placeholder">`.** Este div intermedio sin estilos rompe el `max-height: 100%` de la imagen del mapa (la imagen está en la 388).
- [ ] **Líneas 19-23 y 46, 90, 253, 318, 348: anclas del menú.** Al hacer clic, el título de la sección queda tapado por la navbar fija.

### CSS

- [ ] **Línea 9: `padding: 0` del reset.** Quita la sangría a todos los `<ul>`, y las viñetas quedan pegadas al borde.
  Arreglo: `.widget-card ul { padding-left: 20px; }`
- [ ] **Líneas 12-14 y 29: `scroll-behavior` y `.section`.** Falta `scroll-margin-top`.
  Arreglo: `section[id] { scroll-margin-top: 90px; }`
- [ ] **Línea 72: `.logo`.** Falta `.logo img` con su tamaño.
  Arreglo: `.logo img { height: 40px; width: auto; display: block; }`
- [ ] **Líneas 86-90: `.nav-links`.** Sin `flex-wrap`, en móvil los 5 enlaces pueden salirse de la pantalla.
  Arreglo (dentro del `@media`): `.nav-links { flex-wrap: wrap; justify-content: center; }`
- [ ] **Líneas 596-598: `input[type="radio"] { display: none; }`.** Impide usar el calendario con teclado.
  Arreglo: borra esa regla y usa `.day-radio, .slot-radio { position: absolute; opacity: 0; pointer-events: none; }`
- [ ] **Líneas 664-676 y 678-688: `.map-box` y su imagen.** El parche está en la **línea 687** (`top: 25px`) y empuja la imagen fuera del borde.
  Arreglo: quita el `top: 25px`, y quita el div `.map-placeholder` del HTML o dale `height: 100%; display: flex; align-items: center; justify-content: center;`.
- [ ] **Falta un `img` global.** Sin él, las imágenes de gráficos pueden desbordar la tarjeta.
  Arreglo: `img { max-width: 100%; height: auto; }`
- [ ] **Falta todo el CSS de la tabla y los gráficos.** Se puede añadir antes del `@media` (hacia la línea 708-710). Punto de partida:

```css
.analisia-container { display: grid; gap: 25px; margin-top: 20px; }
.taula-box { overflow-x: auto; }
table { width: 100%; border-collapse: collapse; font-size: 0.9rem; }
th, td { padding: 10px 12px; text-align: left; border-bottom: 1px solid #334155; }
thead th { color: #38bdf8; }
tfoot th { border-top: 2px solid #334155; }
.posatiboa { color: #10b981; font-weight: 600; }
.grafiko-wrapper { display: grid; gap: 15px; }
.ondorioak-box ul { padding-left: 20px; }
```

---

## 2. Textos y datos (HTML)

- [ ] **Línea 56:** "Kaldatuz gabeko", probablemente "Kableatu gabeko".
- [ ] **Línea 137:** "kargarregarriak", probablemente "birkargagarriak".
- [ ] **Línea 157:** "Repetidore", que es castellano (en la línea 78 usas "errepikagailu").
- [ ] **Líneas 208 y 246:** 4.950 / 33.100 = 14,95 %, que redondeado a un decimal es **15,0 %**, no 14,9 %.
- [ ] **Líneas 234-235:** `gráfico de ventas.png` y `pastel de ventas.png` tienen espacios y tilde. Mejor `grafico-ventas.png` y `pastel-ventas.png` (renombra el archivo y el `src`).
- [ ] **Línea 269:** "Apirila / Maiatza 2026" está desfasado respecto a la fecha actual.
- [ ] **Líneas 113, 115, 178:** comprueba que los documentos de Google estén compartidos como "cualquiera con el enlace".
- [ ] **Líneas 143-149 y 152-167:** dos listas con el mismo contenido (decide cuál conservar).

---

## 3. Cosas que no hacen nada

### HTML

- [ ] **268 y 270:** botones `<` y `>` del calendario, sin JavaScript.
- [ ] **273-300, 307-309 y 311:** los radios no están en un `<form>`, así que lo elegido no va a ninguna parte. El botón de la 311 solo salta a `#kontaktua`.
- [ ] **359:** el formulario tiene `action="#"`, así que no envía nada. Necesita un servicio o un backend.
- [ ] **105:** `id="jasangarritasuna"`, nadie lo enlaza.
- [ ] **106, 112, 152:** `<div>` sin clase y sin función.
- [ ] **114:** `<br>` entre los dos botones.
- [ ] **118, 142, 357, 377, 387, 400:** clases sin regla CSS (`gjh-section`, `contact-form-card`, `contact-info-card`, `map-placeholder`, `footer-content`). Son inofensivas, y puedes dejarlas como "ganchos" o quitarlas.

### CSS: se puede borrar

- [ ] **Líneas 4 y 742-744:** comentarios de depuración `outline: 5px solid red`.
- [ ] **Líneas 82-84:** `.logo span`.
- [ ] **Líneas 279-317:** bloque ODS antiguo (`.sdg-list`, `.sdg-item`, `.sdg-badge`, `.sdg-9/12/13`, `.sdg-item h4/p`).
- [ ] **Líneas 319-388:** bloque del gráfico antiguo (`.chart-*`, `.bar*`, `.legend-*`), con su comentario de la 319.
- [ ] **Línea 515:** `.day-name`.
- [ ] **Línea 531:** `.day.muted`.
- [ ] **Línea 536:** `.day.active`.
- [ ] **Línea 565:** la parte `.time-slot.active` (el `:hover` de esa línea sí funciona).
- [ ] **Líneas 734-739:** `.header-eta-menua` dentro del `@media`.

### CSS: redundante (opcional)

- [ ] **Línea 427:** `margin: 0` en `.gjh-card h4` (queda útil solo el `8px` de abajo).
- [ ] **Líneas 570-574:** `.slot-radio`, que anula el `display: none` de la 596.
- [ ] **Líneas 576-578:** `.time-slot` repetida (únela con la de la 554).
- [ ] **Líneas 591-594:** `:focus-visible` que ahora nunca se activa.
- [ ] **Línea 675:** `box-sizing` en `.map-box` (ya lo hace el `*`).

> Antes de borrar `.slot-radio` y `:focus-visible`, decide si arreglas la accesibilidad de los radios (CSS 596-598). Si la arreglas, esas reglas pasan a ser útiles.

---

## 4. Orden recomendado

1. Arreglar el punto de estructura (ya hecho).
2. Errores de la sección 1 (sobre todo CSS de tabla/gráficos, logo y mapa).
3. Textos y datos de la sección 2.
4. Limpieza de la sección 3.
5. Decidir qué hacer con lo que no funciona (calendario y formulario).
