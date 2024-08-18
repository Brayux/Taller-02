# Taller-02

| Nombre                       | Identificación |      Grupo      |      Carrera        |
|------------------------------|----------------|-----------------|---------------------|
| Brayan Andres Guerrero Cortés| 1011201494     |                 |                     |
| Daniel Santiago Barrera Rojas| 1031647812     |   ProGreening   | Ingeniería Agrícola |
| Pablo Mendoza Malagón        | 1072645448     |                 |                     |

[![Imagen-de-Whats-App-2024-04-18-a-las-13-37-14-41369a78.jpg](https://i.postimg.cc/MKtYzt5J/Imagen-de-Whats-App-2024-04-18-a-las-13-37-14-41369a78.jpg)](https://postimg.cc/CzB8NG9c)
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
````python
#Se crea una función para ingresar un número flotante n y separe su parte entera de la parte decimal
def separador_de_digitos(nFloat):
    #Divido por parte entera de 1 para que me de el numero entero
    separador_parte_entera = nFloat // 1
    #Le resto la arte entera al numero racional para obtener el número decimla
    separador_parte_decimal = float(nFloat - int(separador_parte_entera))
    #Se muestra en pantalla la parte entera y ladecimal
    return print(f"La parte entera es: { separador_parte_entera} y la parte decimal es: {separador_parte_decimal}")
if __name__ == "__main__":
    #Usuario digita un numero
    nFloat = float(input("Digite un numero racional: "))
    separador_de_digitos(nFloat)
````
3. Desarrollar un programa que permita ingresar dos números enteros y determinar si se tratan de números espejos, definiendo números espejos como dos números a y b tales que a se lee de izquierda a derecha igual que se lee b de derecha a izquierda, y viceversa.
````python
#Code para saber si 2 numeros son espejos (Mismo numeros al derecho y al revez)
def verificador(a:str,b:str):
    if (a.isdigit() and b.isdigit()):
        return True
    else:
        return False
def operador_a(a:int):
    lista_a=[]
    entrada=a
    longitud=0
    entrada_1=entrada
    while entrada_1>0:
        entrada_1//=10
        longitud+=1
    while longitud>0:
        cifra=entrada//10**(longitud-1)
        cifra=cifra%10
        longitud-=1
        lista_a.append(cifra)
    return lista_a
def operador_b(b:int):
    lista_b=[]
    entrada=b
    longitud=0
    entrada_1=entrada
    while entrada_1>0:
        entrada_1//=10
        longitud+=1
    longitud_1=0
    while longitud_1<longitud:
        cifra_2=entrada//10**(longitud_1)
        cifra_2=cifra_2%10
        longitud_1+=1
        lista_b.append(cifra_2)
    return lista_b
#Se comparan los dos numeros y se arroja un resultado boleano
def identificador(lista_a:list,lista_b:list):
    if lista_a==lista_b:
        return True
    else:
        return False
if __name__=="__main__":
    #El usuario digita los numeros
    a=input("Digite un numero: ")
    b=input("Digite otro numero: ")
    #Se verifica los numeros digitados por el usuario; Si son válidos, se ejecuta el codigo
    verificar=verificador(a,b)
    if verificar==True:
        a=int(a)
        b=int(b)
        print(a+b)
        lista_a=operador_a(a)
        lista_b=operador_b(b)
        juicio=identificador(lista_a,lista_b)
        if juicio==True:
            print("Los numeros ",a," y ",b,"son numeros espejos")
        else:
            print("Los numeros digitados",a," y ",b," no son numeros espejos")
    else:
        print("No se han digitado datos validos")
````
4. Diseñar una función que permita calcular una aproximación de la función coseno alrededor de 0 para cualquier valor x (real), utilizando los primeros n términos de la serie de Taylor. nota: use math para traer la función coseno y mostrar la diferencia entre el valor real y la aproximación. Calcule con cuántos términos de la serie (i.e: cuáles valores de n), se tienen errores del 10%, 1%, 0.1% y 0.001%.
````python
import math


# Función para calcular la aproximación del coseno usando la serie de Taylor
def cos_taylor(x, n):
    aproximacion = sum(((-1)**k * x**(2*k)) / math.factorial(2*k) for k in range(n))
    return aproximacion

# Función para calcular el error porcentual entre el valor real y la aproximación
def error_porcentaje(real, aproximado):
    return abs((real - aproximado) / real) * 100

# Valores a calcular
x = float(input("Ingresa el valor de x (en grados): "))
x_radianes = math.radians(x)
real_value = math.cos(x_radianes)  # Usar x_radianes aquí

# Determinar el número de términos para errores específicos
errors = [10, 1, 0.1, 0.001]
results = {}

for error in errors:
    n = 1
    while True:
        approximation = cos_taylor(x_radianes, n)
        current_error = error_porcentaje(real_value, approximation)
        if current_error <= error:
            results[error] = n
            break
        n += 1

# Devolver resultados en una estructura de datos
results_list = [(error, terminos) for error, terminos in results.items()]

#Iteracion para mostrar los resultados
for error, terminos in results_list:
    print(f"Para un error de {error}%, se necesitan {terminos} términos.")
````
 
5.Desarrollar un programa que permita determinar el Minimo Comun Multiplo de dos numeros enteros. Abordar el problema desde una perpectiva tanto iterativa como recursiva. Pista: Puede ser de utilidad chequear el Algoritmo de Euclides para el cálculo del Máximo Común Divisor, y revisar cómo se relaciona este último con el Mínimo Común Múltiplo.
````python
# Solicitar al usuario que ingrese dos números enteros
primer_entero = int(input("Elija el primer número entero: "))
segundo_entero = int(input("Elija el segundo número entero: "))
# Inicializar listas para almacenar divisores, residuos y cocientes
divisor = []
residuos = []
cocientes = []

# Determinar cuál número es mayor para iniciar el cálculo
if primer_entero > segundo_entero:
    # Calcular el primer cociente y residuo usando el mayor y menor de los dos números
    cociente = primer_entero // segundo_entero
    cocientes.append(cociente)  # Guardar el cociente en la lista
    residuo = primer_entero % segundo_entero
    residuos.append(residuo)  # Guardar el residuo en la lista
    divisor.append(segundo_entero)  # Guardar el divisor (el número menor)
else:
    # Similar al bloque anterior, pero para el caso donde el segundo número es mayor
    cociente = segundo_entero // primer_entero
    cocientes.append(cociente)
    residuo = segundo_entero % primer_entero
    residuos.append(residuo)
    divisor.append(primer_entero)

# Bucle para continuar el proceso de división hasta que el residuo sea 0
while residuo != 0:
    divisor_actual = divisor[-1]  # Obtener el último divisor de la lista
    residuo_anterior = residuos[-1]  # Obtener el último residuo de la lista

    # Si el residuo es 0, se rompe el ciclo para evitar división por 0
    if residuo_anterior == 0:
        break

    # Calcular el nuevo residuo y cociente
    residuo = divisor_actual % residuo_anterior
    cociente = divisor_actual // residuo_anterior
   
    # Guardar el nuevo residuo y cociente en sus respectivas listas
    residuos.append(residuo)
    cocientes.append(cociente)
   
    # Actualizar la lista de divisores con el residuo anterior
    divisor.append(residuo_anterior)


# Calcular el Máximo Común Divisor (MCD)
m_c_d = sum(cocientes)  

# Calcular el Mínimo Común Múltiplo (MCM)
m_c_m = (primer_entero * segundo_entero) / m_c_d

# Imprimir los resultados finales
print("El M.C.M y M.C.D de los números entregados son " + str(m_c_m) + " y " + str(m_c_d) + " respectivamente.")
````
6. Desarrollar un programa que determine si en una lista existen o no elementos repetidos. Pista: Maneje valores booleanos y utilice el operador in.
````python
#programa que determine si en una lista existen o no elementos repetidos
#Se crean dos variables
def listarepeticion(l:list,k:bool):
    i=1
    while i==1:
        e= input("Digite un dato: ")
        l.append(e)
        #Se le pide al usuario mas numeros para comparar esos dos datos
        i=int(input("Quiere digitar otro dato? (1, cualquier otro numero para no)"))
        #Si los datos son iguales es falso
        #Se utilizan boleanos
    if k==True: print("La priemra lista es: "+ str(l)+ ", la siguiente lista no debe tener mas de "+ str(len(l))+" datos")
    else: print("La lista es: "+ str(l)+ ", la cual tiene "+ str(len(l))+" datos")
if __name__=="__main__":
    p:bool=False
    lista1=[]
    lista2=[]
    listarepeticion(lista1,False)
    for i in lista1:
        if lista1.count(i)!=1 and i in lista2!=True:
            print("El numero "+str(i)+" se repite "+str(lista1.count(i))+" veces")
            lista2.append(i)
            p=True
    #Se le muestra al usuario si hay valores repetidos o no
    if p==True:
        print("En la lista hay valores repetidos")
    else:
        print("No hay valores repetidos")
````
7. Desarrollar un programa que determine si en una lista se encuentra una cadena de caracteres con dos o más vocales. Si la cadena existe debe imprimirla y si no existe debe imprimir 'No existe'.
````python
#se llama la funcion del punto 6
from Punto_6 import listarepeticion
if __name__ == "__main__":
#Se crean 2 listas
    o:list=[]
    q:list=["a","e","i","o","u","A","E","I","O","U"]
    listarepeticion(o,False)
#se crea un for con las listas
    for i in o:
        l:int=0
        for j in i:
            if j in q:
                l=l+1
#Mostrar el resultado en pantalla
        if l==1: print("La palabra "+i+" tiene "+str(l)+" vocales")
        elif l>1: print("La palabra "+i+" tiene "+str(l)+" vocales")
        else: print("La palabra "+i+" no es una cadena o no tiene vocales")
````
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
````python
#Halle el promedio de una serie de numeros con la cantidad de elemntos que desee
#Creamos un vector con n elementos y n digitos
A=[]
sum=0
N=int(input("Digite tamaño vector mayor a 3: \n"))
for f in range(0,N,1):
    x=int(input("Digite un elemento: "))
    A.append(x)

for f in range(0,N,1):
    sum=sum + A[f]
#Creamos funcion de promedio
pro=sum/len(A)
print("El promedio es: ",pro)
#Crear funcion raiz cubica del primer índice
raiz= A[0]**(1/3)
print("La raiz cúbica del primer elemento es: ",raiz)
#Crear operacion de prom multiplicativo de los primeros 3 indices
promediomultiplicativo = A[0]*A[1]*A[2]**(1/5)
print("El promedio multiplicativo de los 3 primeros indices es ", promediomultiplicativo)
````
10. Suponga que se tiene una lista A con ciertos números enteros. Desarrolle una función que, independientemente de los números que se encuentran en la lista A, tome aquellos números que son múltiplos de 3 y los guarde en una lista nueva, la cual debe ser retornada por la función. Implemente la perspectiva de un patrón de acumulación y también de comprensión de listas. 
````python
A = [12, 22, 45, 33, 19, 81, 100, 30]
# Función haciendo uso de %
def obtener_multiplos_de_3_con_modulo(A):
    multiplos = []  # Lista para acumular los múltiplos de 3
    for num in A:  # Recorre cada número en la lista A
        if num % 3 == 0:  # Verifica si el número es múltiplo de 3 usando %
            multiplos.append(num)  # Si es múltiplo de 3, se añade a la lista
    return multiplos  # Retorna la lista de múltiplos de 3

resultados = obtener_multiplos_de_3_con_modulo(A)
print(resultados)  # Imprime la lista de múltiplos de 3 encontrados

# Función para verificar si un número es múltiplo de 3 sin hacer uso de %
def multiplo_de_3(num):
    suma = 0  # Inicializa la suma de los dígitos
    for digit in str(num):  # Recorre cada dígito del número
        suma += int(digit)  # Convierte el dígito a entero y lo suma
   
    # Resta 3 de la suma repetidamente hasta que sea menor que 3
    while suma >= 3:
        suma -= 3
   
    return suma == 0  # Si el resultado final es 0, el número es múltiplo de 3

# Función que utiliza la función anterior para obtener los múltiplos de 3 en la lista A
def obtener_multiplos_de_3(A):
    multiplos = []  # Lista para acumular los múltiplos de 3
    for num in A:  # Recorre cada número en la lista A
        if multiplo_de_3(num):  # Verifica si el número es múltiplo de 3
            multiplos.append(num)  # Si es múltiplo de 3, se añade a la lista
    return multiplos  # Retorna la lista de múltiplos de 3

print(obtener_multiplos_de_3(A))  # Imprime la lista de múltiplos de 3 encontrados
````

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
