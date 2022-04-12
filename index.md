## keys game

A simple game to learn the position of the keys.  
[Play it here](index_en.html)

Un juego sencillo para aprender las posiciones de las teclas.  
[Juega aquí](index_es.html)

### The game

The game has two levels:  
Level 1: single keys. It cares only about positions on the keyboard. Thus, it will only work for the Spanish QWERTY keyboard on PC. So:
- It will not work in android or iOS, check [What key was pressed? (You won't believe how keyboard events work)](https://www.youtube.com/watch?v=jLqTXkFtEH0&list=PLNYkxOF6rcIAKIQFsNbV0JDws_G_bnNo9)
- It will not work for many keys with the US keyboard. Two reasons for this:
  - some keys are in different positions (this could be easily fixed, since these keys are just character keys)
  - some keys require a combination in Spanish and no combinations in English. This is a problem, because level 1 is about single keys and level 2 is about combinations.
- It will work for in a laptop with linux, since I developed it in a linux laptop. The game doesn't ask about the windows key.

Level 2: keys combinations. It cares mainly about the typed characters and not about so much the positions, so it may work in any PC keyboard.

### El juego
Accede desde aquí:  
[En inglés](index_en.html)  
[En español](index_es.html)

El juego tiene dos niveles:  
Nivel 1: teclas individuales. Tiene en cuenta solamente las posiciones de las teclas. Por lo tanto, solo funcionará en un teclado español QWERTY. Así que:
- No funcionará en android ni en iOS, comprueba [What key was pressed? (You won't believe how keyboard events work)](https://www.youtube.com/watch?v=jLqTXkFtEH0&list=PLNYkxOF6rcIAKIQFsNbV0JDws_G_bnNo9)
- No funcionará con muchas teclas del teclado americano. Por dos razones:
  - algunas teclas están en posiciones diferentes (esto tiene fácil solución, puesto que esas teclas son teclas de caracteres)
  - algunas teclas requieren combinación de teclas en español pero no en inglés. Esto es un problema, porque el nivel 1 se ocupa de las teclas individuales y el 2 de las combinaciones.
- Funcionará en un portátil con linux, ya que lo he desarrollado en un portátil con linux. El juego no pregunta por la tecla de windows.

Nivel 2: combinaciones de teclas. Tiene en cuenta sobre todo los caracteres tecleados y no tanto las posiciones, por lo que debería funcionar en cualquier teclado para PC.

### How it was made
The game has been made with vanilla css and js. Everything is contained in a single html file (no external css or js), with no ofuscations. Exceptions:
- The icons for the keyboard and trophy come from [font awesome](https://fontawesome.com/).
- The fonts come from [Google Fonts](https://fonts.google.com/).

### Cómo está hecho
El juego está hecho con css y javascript vainilla. Todo está contenido en un solo fichero html (no hay ficheros css o js externos), sin ofuscaciones. Excepciones:
- Los iconos del teclado y el trofeo son de [font awesome](https://fontawesome.com/).
- Las fuentes son de [Google Fonts](https://fonts.google.com/).

### Coding challenges and pending refactor
Two things have been challenging:
- When the right key is guessed or one life is lost, there is a short animation. If the right key is pressed during the animation, it triggered another "newKey()" call, that produced a chaos. It was fixed by avoiding the checking of the keys during the animation, but I still saw it one time after the fix. Also, the fix is different for level 1 and 2, I would like to use the fix from level 2 better, and this is pending.
- The Spanish accent keys trigger a "KeyDown" event, but it doesn't always trigger a "KeyUp". Even worse, the combination of the shift and the accent doesn't trigger the "KeyUp" for the shift either. There is a "you typed" section on the screen, that gives you some help when you typed the wrong key, and because of this, sometimes in the level two it may say that you pressed the shift, even though you haven't. But the detection still works, because it checks other things. I should rebuild the "you typed" keys just by checking at the last KeyUp event, and not taking two keys into account, as it happens now.

I would like to refactor the code, not only because of those two things but mainly because the use of vanilla js causes a big mix of code:
- There is a big mixture of UI code and logic code
- You need to go through all the code to find the basic four logic conditions: guess right, guess wrong, level win, lose
I would like to have a much cleaner code, separating the UI and animation code from the logic, and having the logic condition clearly identified.

### Dificultades en el código y refactorización pendiente
Dos cosas han sido complicadas:
- Cuando se acierta la tecla o se pierde una vida, hay una animación. Si la tecla correcta se pulsa durante la animación, esto desencadenaba una llamada adicional a "newKey()" que producía un caos. Esto lo solucioné evitando la comprobación de teclas durante la animación, pero aún lo he visto suceder una vez tras corregirlo. Además, la corrección es distinta en el nivel 1 y el 2, me gustaría aplicar siempre la solución del nivel 2, pero esto está pendiente.
- El teclado español desencadena un evento "KeyDown" para las teclas de la tilde y la tilde invertida, pero sin embargo no siempre desencadena un "KeyUp". Y lo que es peor, si se ha pulsado la mayúscula antes del acento, es posible que tampoc llegue el "KeyUp" de la mayúscula. Hay una sección "has pulsado" en la pantalla, que te da ayuda cuando te equivocas de tecla, y por culpa de este problema, en el nivel 2 esta sección de la pantalla te puede decir que tienes pulsada la mayúscula cuando no es así. Pero la detección funciona de todos modos, porque comprueba otras cosas. Debería reconstruir este "has pulsado" a partir del código de la detección, que solo tiene en cuenta el último evento KeyUp. Esto está pendiente también.

Me gustaría refactorizar el código, no solo por las dos cosas anteriores, sino fundamentalmente porque el uso de js vainilla lleva a una gran mezcla de código:
- Hay una gran mezcla de código de UI y código de lógica
- Tienes que revisar todo el código para encontrar las cuatro condiciones de lógica básicas: acierto, error, pasas el nivel, pierdes
Me gustaría tener un código mucho más limpio, separando la parte de la UI y la animación de la lógica del juego, y teniendo las condiciones claramente identificadas
