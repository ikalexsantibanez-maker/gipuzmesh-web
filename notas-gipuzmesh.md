Tenemos el siguiente problema: Tenemos q aberiguar preguntando a un profesor q boton hay q usar en el archivo html de gipuzmesh
Tambien queda por ver como hacer q la web este tambien en ingles
Tambien queda revisar a fondo ciertos otros detalles, como q lo de Jasangarritasuna y salmenen analisia se parezca mas
Opcion 1:
<div class="calendar-grid">
    <span class="day-name">Al</span><span class="day-name">Ar</span><span class="day-name">Az</span><span class="day-name">Og</span><span class="day-name">Or</span><span class="day-name">La</span><span class="day-name">Ig</span>
    <button type="button" class="day">1</button><button type="button" class="day">2</button><button type="button" class="day">3</button><button type="button" class="day">4</button><button type="button" class="day">5</button><button type="button" class="day">6</button><button type="button" class="day">7</button>
    <button type="button" class="day">8</button><button type="button" class="day">9</button><button type="button" class="day">10</button><button type="button" class="day">11</button><button type="button" class="day">12</button><button type="button" class="day">13</button><button type="button" class="day">14</button>
    <button type="button" class="day">15</button><button type="button" class="day">16</button><button type="button" class="day">17</button><button type="button" class="day">18</button><button type="button" class="day">19</button><button type="button" class="day">20</button><button type="button" class="day">21</button>
    <button type="button" class="day">22</button><button type="button" class="day">23</button><button type="button" class="day">24</button><button type="button" class="day">25</button><button type="button" class="day">26</button><button type="button" class="day">27</button><button type="button" class="day">28</button>
</div>
<!-- CSS A METER SI SE SLIGE ESTA OPCION -->
añadir esto debajo de la regla .day del CSS:
button.day {
    border: none;
    font-family: inherit;
}
<!--javaScrip a poner en un archivo en la misma carpeta del html-->
js
function seleccionarUno(botones) {
    botones.forEach(function (boton) {
        boton.addEventListener("click", function () {
            botones.forEach(function (b) {
                b.classList.remove("active");
            });
            boton.classList.add("active");
        });
    });
}

seleccionarUno(document.querySelectorAll(".calendar-grid .day"));
seleccionarUno(document.querySelectorAll(".time-slot"));
Lo siguiente meterlo en el body del html:
<script src="gipuzmesh-web.js"></script>

Opcion 2:
Sustituye los 28 botones de día por pares input + label. El input tiene que ir justo antes de su label:
<input type="radio" name="dia" id="dia1" class="day-radio"><label for="dia1" class="day">1</label>
<input type="radio" name="dia" id="dia2" class="day-radio"><label for="dia2" class="day">2</label>
<input type="radio" name="dia" id="dia3" class="day-radio"><label for="dia3" class="day">3</label>
<!-- ... y así hasta el 28, cambiando el número en id, for y el texto -->
<input type="radio" name="dia" id="dia28" class="day-radio"><label for="dia28" class="day">28</label>

<div class="time-slots">
    <input type="radio" name="txanda" id="txanda1" class="slot-radio" checked><label for="txanda1" class="time-slot">09:00 - Goizeko Txanda</label>
    <input type="radio" name="txanda" id="txanda2" class="slot-radio"><label for="txanda2" class="time-slot">14:30 - Arratsaldeko Txanda</label>
    <input type="radio" name="txanda" id="txanda3" class="slot-radio"><label for="txanda3" class="time-slot">Egun Osoa (24h)</label>
</div>

<!-- CSS A METER SI SE SLIGE ESTA OPCION -->
Si se a añadido antes el button.day {...} borrarlo
.day-radio,
.slot-radio {
    position: absolute;
    opacity: 0;
    pointer-events: none;
}

.time-slot {
    text-align: center;
}

.day-radio:checked + .day {
    background-color: #10b981;
    color: #0f172a;
    font-weight: bold;
}

.slot-radio:checked + .time-slot {
    border-color: #38bdf8;
    color: #38bdf8;
}

.day-radio:focus-visible + .day,
.slot-radio:focus-visible + .time-slot {
    outline: 2px solid #38bdf8;
}

Ninguna de estas opciones estrictamente correcta con la realidad, y ninguna activa las flechas laterales superiores.
