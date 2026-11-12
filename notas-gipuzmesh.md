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
<!-- A mter si se elige la opcion 1-->
Lo siguiente meterlo en el body del html:
<script src="gipuzmesh-web.js"></script>

Opcion 2:
Sustituir los 28 botones de día por pares input + label. El input tiene que ir justo antes de su label:
<input type="radio" name="dia" id="dia1" class="day-radio"><label for="dia1" class="day">1</label>
<input type="radio" name="dia" id="dia2" class="day-radio"><label for="dia2" class="day">2</label>
<input type="radio" name="dia" id="dia3" class="day-radio"><label for="dia3" class="day">3</label>
<input type="radio" name="dia" id="dia4" class="day-radio"><label for="dia4" class="day">4</label>
<!-- ... y así hasta el 28, cambiando el número en id, for y el texto -->
<input type="radio" name="dia" id="dia28" class="day-radio"><label for="dia28" class="day">28</label>
<!--version extendida de lo de arriba-->
<input type="radio" name="dia" id="dia1" class="day-radio"><label for="dia1" class="day">1</label>
<input type="radio" name="dia" id="dia2" class="day-radio"><label for="dia2" class="day">2</label>
<input type="radio" name="dia" id="dia3" class="day-radio"><label for="dia3" class="day">3</label>
<input type="radio" name="dia" id="dia4" class="day-radio"><label for="dia4" class="day">4</label>
<input type="radio" name="dia" id="dia5" class="day-radio"><label for="dia5" class="day">5</label>
<input type="radio" name="dia" id="dia6" class="day-radio"><label for="dia6" class="day">6</label>
<input type="radio" name="dia" id="dia7" class="day-radio"><label for="dia7" class="day">7</label>
<input type="radio" name="dia" id="dia8" class="day-radio"><label for="dia8" class="day">8</label>
<input type="radio" name="dia" id="dia9" class="day-radio"><label for="dia9" class="day">9</label>
<input type="radio" name="dia" id="dia10" class="day-radio"><label for="dia10" class="day">10</label>
<input type="radio" name="dia" id="dia11" class="day-radio"><label for="dia11" class="day">11</label>
<input type="radio" name="dia" id="dia12" class="day-radio"><label for="dia12" class="day">12</label>
<input type="radio" name="dia" id="dia13" class="day-radio"><label for="dia13" class="day">13</label>
<input type="radio" name="dia" id="dia14" class="day-radio"><label for="dia14" class="day">14</label>
<input type="radio" name="dia" id="dia15" class="day-radio"><label for="dia15" class="day">15</label>
<input type="radio" name="dia" id="dia16" class="day-radio"><label for="dia16" class="day">16</label>
<input type="radio" name="dia" id="dia17" class="day-radio"><label for="dia17" class="day">17</label>
<input type="radio" name="dia" id="dia18" class="day-radio"><label for="dia18" class="day">18</label>
<input type="radio" name="dia" id="dia19" class="day-radio"><label for="dia19" class="day">19</label>
<input type="radio" name="dia" id="dia20" class="day-radio"><label for="dia20" class="day">20</label>
<input type="radio" name="dia" id="dia21" class="day-radio"><label for="dia21" class="day">21</label>
<input type="radio" name="dia" id="dia22" class="day-radio"><label for="dia22" class="day">22</label>
<input type="radio" name="dia" id="dia23" class="day-radio"><label for="dia23" class="day">23</label>
<input type="radio" name="dia" id="dia24" class="day-radio"><label for="dia24" class="day">24</label>
<input type="radio" name="dia" id="dia25" class="day-radio"><label for="dia25" class="day">25</label>
<input type="radio" name="dia" id="dia26" class="day-radio"><label for="dia26" class="day">26</label>
<input type="radio" name="dia" id="dia27" class="day-radio"><label for="dia27" class="day">27</label>
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

Para solucionar el problema q dava poner <imput type "radio"> (ponia n circulo blanco al lado de cada boton) se a colocado el proximo codigo dentro del archivo CSS en el apartado de */ERRESERBA...

input[type="radio"] {
    display: none;
}

Ninguna de estas opciones estrictamente correcta con la realidad, y ninguna activa las flechas laterales superiores.
