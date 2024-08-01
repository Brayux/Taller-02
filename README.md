# Taller-02

| Nombre                       | Identificación |      Grupo      |      Carrera        |
|------------------------------|----------------|-----------------|---------------------|
| Brayan Andres Guerrero Cortés| 1011201494     |                 |                     |
| Daniel Santiago Barrera Rojas| 1031647812     |   ProGreening   | Ingeniería Agrícola |
| Pablo Mendoza Malagón        | 1072645448     |                 |                     |

<table cellspacing="1" bgcolor="" align="center">
  <tr bgcolor="#252582">
    <th><b>- ProGreening - </b></th>
  </tr>
  

    
1. Desarrollar un programa que ingrese un número entero n y separe todos los digitos que componen el número. Pista: Utilice los operadores módulo (%) y división entera (//).
````python
    
#Separar todos los digitos que componen un número.
#Creamos variable
digitosNumero=[]
#Creamos una funcion donde nos de el residuo de x al dividirlo entre 10 para hallar su ultimo numero
def digitos(x):
    while x > 0:
        digitosNumero.append(x % 10)
        #dividimos nuestro numero por parte entera entre 10
        x = x//10
    #mostrar los digitos en el mismo orden q el usuario los ingreso[::-1]
    print ("Los digitos de su número son :",digitosNumero[::-1])
    
if __name__=="__main__":
 usuario = int(input("Ingrese su número favorito :) = "))
 digitos(usuario)
 
````
2. Desarrollar un programa que ingrese un número flotante n y separe su parte entera de la parte decimal, y luego entregue los dígitos tanto de la parte entera como de la decimal.

3. Desarrollar un programa que permita ingresar dos números enteros y determinar si se tratan de números espejos, definiendo números espejos como dos números a y b tales que a se lee de izquierda a derecha igual que se lee b de derecha a izquierda, y viceversa.

4. Diseñar una función que permita calcular una aproximación de la función coseno alrededor de 0 para cualquier valor x (real), utilizando los primeros n términos de la serie de Taylor. nota: use math para traer la función coseno y mostrar la diferencia entre el valor real y la aproximación. Calcule con cuántos términos de la serie (i.e: cuáles valores de n), se tienen errores del 10%, 1%, 0.1% y 0.001%. 
 
5.Desarrollar un programa que permita determinar el Minimo Comun Multiplo de dos numeros enteros. Abordar el problema desde una perpectiva tanto iterativa como recursiva. Pista: Puede ser de utilidad chequear el Algoritmo de Euclides para el cálculo del Máximo Común Divisor, y revisar cómo se relaciona este último con el Mínimo Común Múltiplo.

6. Desarrollar un programa que determine si en una lista existen o no elementos repetidos. Pista: Maneje valores booleanos y utilice el operador in.

7. Desarrollar un programa que determine si en una lista se encuentra una cadena de caracteres con dos o más vocales. Si la cadena existe debe imprimirla y si no existe debe imprimir 'No existe'.

8. Desarrollar un programa que dadas dos listas determine que elementos tiene la primer lista que no tenga la segunda lista.
````python

'''que elementos tiene la primer lista que no tenga la segunda lista.'''
#Crear 2 variables, cada una con una lista independiente
lista1=[1,2,3,4,5,6,7,8,9,0,"hola mundo","python","Real madrid","felipe Roldan"]
lista2=["Barcelona","Felipe roldan",8,9,7,3,1,4,6,"hola Mundo", "python"]
#Para saber que datos no se repiten en la lista 1 se resta el contenido de la lista 2 al cont de la lista 1
salida=set(lista1)-set(lista2)
print("Los elementos que no se repiten en la primera lista son:\n ",salida)

````
9. Resolver el punto 7 del taller 1 usando operaciones con vectores.

10. Suponga que se tiene una lista A con ciertos números enteros. Desarrolle una función que, independientemente de los números que se encuentran en la lista A, tome aquellos números que son múltiplos de 3 y los guarde en una lista nueva, la cual debe ser retornada por la función. Implemente la perspectiva de un patrón de acumulación y también de comprensión de listas. 

-----Bono-----
Desarrollar un algoritmo que determine si una matriz es mágica. Se dice que una matriz cuadrada es mágica si la suma de cada una de sus filas, de cada una de sus columnas y de cada diagonal es igual.
````python
square= []
square.append([29*29, 1, 47*47])
square.append([41**2, 37**2, 1])
square.append([529, 1681, 841])


for row in square:
    rowsum = 0
    for element in row:
        rowsum += element
    print(rowsum)


for i in range(3):
    colsum = 0
    rowsum = 0
    for j in range(3):
        colsum += square[i][j]
        rowsum += square[j][i]
    print("Colsum: ",colsum)
    print("Rowsum: ",rowsum)


diag1sum = 0
diag2sum = 0
for i in range(3):
    diag1sum += square[i][i]
    diag2sum += square[2-i][i]


print("diag1sum",diag1sum)
print("diag2sum",diag2sum)
````
