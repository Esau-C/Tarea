# Tarea algoritmos
La tarea consiste en realizar 2 programas los cuales son:

1. Realizar un programa que: Un triángulo recto puede tener lados cuyas longitudes sean valores enteros. Un conjunto de tres valores enteros para los lados de un triángulo recto se conoce como triple de Pitágoras. Estos tres lados deben satisfacer la relación que establece que la suma de los cuadrados de dos lados es igual al cuadrado de la hipotenusa. Encuentre todos los triples de Pitágoras para lado1, lado2, y la hipotenusa, que no sean mayores de 500. Use un ciclo for triplemente anidado para probar todas las posibilidades. 

2. El segundo programa consiste en realizar un juego de ahorcado, el usuario debera adivinar la palabra oculta.

>Los ejercicio deben ser creados de 3 formas diferentes las cuales son:
* C++
* Python
* Pseint

### Acontinuacion el codigo 

# Ejercicio de las pitagoras
## Codigo en C++
```c++
#include <iostream>

int main() {
    // Define el límite superior para los lados
    const int limite_superior = 500;
    // Bucle for para lado 1
    for (int lado1 = 1; lado1 <= limite_superior; lado1++) {
       // Bucle for para lado 2
        for (int lado2 = lado1; lado2 <= limite_superior; lado2++) {
            //Blucle for para la hipotenusa
            for (int hipotenusa = lado2; hipotenusa <= limite_superior; hipotenusa++) {
                // Se comprueba si se cumple el teorema
                if (lado1 * lado1 + lado2 * lado2 == hipotenusa * hipotenusa) {
                    std::cout << "Triple de Pitágoras encontrado: " << lado1 << ", " << lado2 << ", " << hipotenusa << std::endl;
                }
            }
        }
    }

    return 0;
}
```
## Codigo en Python
```py
# Define el límite superior para los lados
limite_superior = 500

# Bucle for para lado 1
for lado1 in range(1, limite_superior + 1):
    # Bucle for para lado 2
    for lado2 in range(lado1, limite_superior + 1):
        # Bucle for para la hipotenusa
        for hipotenusa in range(lado2, limite_superior + 1):
            # Comprobar si se cumple el teorema de Pitágoras
            if lado1 ** 2 + lado2 ** 2 == hipotenusa ** 2:
                print(f"Triple de Pitágoras encontrado: {lado1}, {lado2}, {hipotenusa}")

```
## Codigo en Pseint
```
Algoritmo TriplesPitagoras
    Definir limite_superior Como Entero
    limite_superior <- 500
    
    Escribir "Triples de Pitágoras encontrados:"
    
    Para lado1 <- 1 Hasta limite_superior Con Paso  1 Hacer
        Para lado2 <- lado1 Hasta limite_superior Con Paso 1 Hacer
            Para hipotenusa <- lado2 Hasta limite_superior Con Paso 1 Hacer
                Si lado1^2 + lado2^2 = hipotenusa^2 Entonces
                    Escribir lado1, ", ", lado2, ", ", hipotenusa
                Fin Si
            Fin Para
        Fin Para
    Fin Para
Fin Algoritmo

```
---
---
---
---
# Ejercicio del juego del ahorcado
## Ejercicio en C++
```c++
//Definimos las librerias
#include <iostream>
#include <string>

using namespace std;

int main() {
    //definimos la palabra secreta
    string palabraSecreta = "Computadora";
    //para ocultar la palabra y se muestre con guiones
    string palabraAdivinada(palabraSecreta.length(), '_');
    int intentosRestantes = 6;

    cout << "Bienvenido al juego del ahorcado!" << endl;

    while (intentosRestantes > 0 && palabraAdivinada != palabraSecreta) {
        cout << "Palabra actual: " << palabraAdivinada << endl;
        cout << "Intentos restantes: " << intentosRestantes << endl;
        cout << "Ingresa una letra: ";
        char letraIngresada;
        cin >> letraIngresada;

        bool letraAdivinada = false;

        //Se realiza la comparacion si es verdadero o no
        for (int i = 0; i < palabraSecreta.length(); ++i)
         {
            
            if (palabraSecreta[i] == letraIngresada) {
                palabraAdivinada[i] = letraIngresada;
                letraAdivinada = true;
            }
        }
        
        if (!letraAdivinada) {
            cout << "Incorrecto, la letra no está en la palabra." << endl;
            intentosRestantes--;
        }
    }
    //Comparacion si aun quedan vidas o no
    if (intentosRestantes == 0) {
        cout << "Te has quedado sin intentos, la palabra era: " << palabraSecreta << endl;
    } else {
        cout << "Felicidades, has adivinado la palabra: " << palabraSecreta << endl;
    }

    return 0;
}

```
---
## Ejercicio en Python
```py
palabra_secreta = "Computadora"
palabra_adivinada = ["_"] * len(palabra_secreta)
intentos_restantes = 6

print("Bienvenido al juego del ahorcado!")

while intentos_restantes > 0 and "".join(palabra_adivinada) != palabra_secreta:
    print("Palabra actual:", " ".join(palabra_adivinada))
    print("Intentos restantes:", intentos_restantes)
    letra_ingresada = input("Ingresa una letra: ")

    letra_adivinada = False

    for i in range(len(palabra_secreta)):
        if palabra_secreta[i] == letra_ingresada:
            palabra_adivinada[i] = letra_ingresada
            letra_adivinada = True

    if not letra_adivinada:
        print("Incorrecto. La letra no está en la palabra.")
        intentos_restantes -= 1

if intentos_restantes == 0:
    print("¡Te has quedado sin intentos! La palabra era:", palabra_secreta)
else:
    print("¡Felicidades! Has adivinado la palabra:", palabra_secreta)

```
---
## Ejercicio en Pseint
```
Algoritmo JuegoAhorcado
    Definir palabraSecreta Como Caracteres
    Definir palabraAdivinada Como Caracteres
    Definir intentosRestantes Como Entero
    Definir letraIngresada Como Caracter
    Definir letraAdivinada Como Logico
	
    palabraSecreta = "Computadora"
    palabraAdivinada = ""
    intentosRestantes = 6
	
    Para i = 1 Hasta Longitud(palabraSecreta)
        palabraAdivinada = palabraAdivinada + "_"
    FinPara
	
    Escribir "Bienvenido al juego del ahorcado!"
	
    Mientras intentosRestantes > 0 Y palabraAdivinada <> palabraSecreta
        Escribir "Palabra actual: ", palabraAdivinada
        Escribir "Intentos restantes: ", intentosRestantes
        Escribir "Ingresa una letra: "
        Leer letraIngresada
		
        letraAdivinada = Falso
		
        Para i = 1 Hasta Longitud(palabraSecreta)
            Si Subcadena(palabraSecreta, i, 1) = letraIngresada Entonces
                palabraAdivinada = Subcadena(palabraAdivinada, 1, i - 1) + letraIngresada + Subcadena(palabraAdivinada, i + 1, Longitud(palabraAdivinada) - i)
                letraAdivinada = Verdadero
            FinSi
        FinPara
		
        Si No letraAdivinada Entonces
            Escribir "Incorrecto, la letra no está en la palabra."
            intentosRestantes = intentosRestantes - 1
        FinSi
    FinMientras
	
    Si intentosRestantes = 0 Entonces
        Escribir "Te has quedado sin intentos, la palabra era: ", palabraSecreta
    Sino
        Escribir "Felicidades, has adivinado la palabra: ", palabraSecreta
    FinSi
	
FinAlgoritmo

```
---
---
---
[Click aca para ver el video explicando el codigo ](https://youtu.be/rKGdzoeIjJQ)