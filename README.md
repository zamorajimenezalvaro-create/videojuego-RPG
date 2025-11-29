# Videojuego RPG: descripción General del Juego

Este código implementa un videojuego RPG por consola, ambientado en barrios marginales del sur de España, donde tres personajes principales (La Saray, El Patriarca y Su’ Primico) avanzan a través de distintos capítulos, enfrentando enemigos, usando objetos, comprando en tiendas y aplicando habilidades especiales únicas.

El juego está dividido en 3 capítulos, uno para cada personaje protagonista, con historia, ASCII art decorativo, combates por turnos y un inventario compartido entre todos.

---

# Estructura de la Historia

## CAPÍTULO 1 — La Saray
La esposa del Patriarca busca venganza tras su encarcelamiento. En este capítulo el jugador controla a La Saray, enfrentándose a varios sicarios de la mafia antes de poder avanzar.

Características del capítulo:
- Máximo de 3 peleas obligatorias.
- Acceso a:
  - Tienda (“Los Baratos”)
  - Inventario compartido
  - Estadísticas del personaje
- Habilidad especial: Maldición
- Tras cumplir las peleas, se avanza al Patriarca.

---

## CAPÍTULO 2 — El Patriarca
Al salir de prisión, el Patriarca vuelve al crimen para rehacer su vida. Se enfrenta a numerosos enemigos hasta que la policía interviene.

Características:
- Hasta 5 peleas, después de las cuales aparece la policía.
- Si intenta pelear tras el límite, muere automáticamente.
- Su muerte desbloquea el capítulo del Prímico.
- Habilidad especial: Ataque Cargado Devastador (One-Shot tras 2 turnos de carga).

---

## CAPÍTULO 3 — Su’ Primico (Boss Final)
El Prímico enfrenta al Capo de la Mafia en la batalla final del juego.

---

# Sistema de Combate

El combate es por turnos, siguiendo estas reglas:

### Turno del jugador
- Atacar  
- Usar objeto  
- Usar habilidad especial (si procede)  
- Ver estadísticas  
- Se aplican efectos como quemaduras al inicio del turno

### Turno del enemigo
- Ataca normalmente, excepto si:
  - Está maldito (puede hacerse daño)
  - Está quemado (recibe daño al inicio del turno)

### Daño
- Ataques del jugador y enemigo incluyen un bonus aleatorio (+0 a +2).

### Botín
- Los enemigos sueltan entre 1 y 5 lereles al morir.

---

# Habilidades Especiales

## La Saray — Maldición
- Coste: 8 de maná  
- El enemigo queda maldito toda la pelea  
- Efecto:
  - 50% de probabilidades de hacerse daño equivalente a su propio ataque
  - 50% atacar normalmente  

---

## El Patriarca — Ataque Cargado
- Consume todo el maná al activarse  
- Requiere 2 turnos de carga  
- Al finalizar: One-Shot, mata instantáneamente al enemigo  
- Durante la carga no puede usar otras habilidades  

---

# Efectos de Estado

### Quemadura
- 2 de daño por turno  
- Persistente toda la pelea  
- Aplicada por el objeto "Libro que quema"  

### Maldición
- Persistente toda la pelea  
- Ver efecto arriba  

---

# Inventario Compartido

Todos los personajes comparten un mismo inventario central.

Los objetos pueden:
- Comprarse
- Usarse en combate
- Consumirse (si son consumibles)
- Aplicar mejoras permanentes

Nota: En la versión actual del código, incluso los objetos permanentes se consumen al usarlos.

---

# Tienda — “Los Baratos”

El jugador puede comprar objetos con su dinero acumulado.

### Consumibles ofensivos
- Romero: daño extra aleatorio  
- Libro que quema: aplica quemadura  

### Consumibles de recuperación
- Té de hinojo: +10 vida  
- Potaje: +15 maná  
- Flamenco: +25 maná  

### Permanentes
- Pulsera: +1 ataque  
- Rosario: +5 vida máxima  
- Guitarra flamenca: +10 ataque  
- Bandera gitana: +5 vida máxima y +5 maná máximo  

---

# Sistema de Personajes

Cada personaje tiene:
- Vida (actual y máxima)
- Ataque
- Maná (actual y máximo)
- Estados (quemado, maldito, cargando)
- Dinero
- Métodos como:
  - `aplicarMaldicion()`
  - `aplicarQuemadura()`
  - `procesarEfectosAlInicioTurno()`
  - `startCharging()`
  - `decrementCharge()`

---

# Reglas Principales

1. El inventario es compartido por todos los personajes.  
2. La maldición y la quemadura duran toda la pelea.  
3. Los objetos consumibles desaparecen tras usarse.  
4. El Patriarca muere automáticamente si pelea tras 5 combates.  
5. El ataque cargado del Patriarca mata instantáneamente.  
6. Los enemigos malditos tienen 50% de hacerse daño.  
7. El boss final es el Capo de la Mafia.  

---

# Resumen Global

Este juego implementa un RPG narrativo con combate por turnos, dividido en capítulos, con sistema de tienda, inventario compartido, habilidades especiales persistentes y efectos de estado estratégicos.  
La historia progresa a través de La Saray, el Patriarca y Su’ Primico hasta la batalla final contra el Capo de la Mafia.
