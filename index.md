Text can be **bold**, _italic_, or ~~strikethrough~~.

[Link to another page](./another-page.html).


# Programación funcional en Python
## ¿Que es?
La programación funcional (PF) es un paradigma de programación al igual que la programación orientada a objetos (POO). La PF se basa en cálculo lambda y concretamente en composición de funciones puras para modelar las soluciones de software.
La programación funcional es un paradigma declarativo. Nos enfocaremos en "qué" estamos haciendo y no en "cómo" se está haciendo que sería el enfoque imperativo. Esto quiere decir que nosotros expresaremos nuestra lógica sin describir controles de flujo; no usaremos ciclos o condicionales.

### Funciones de primera clase
Todo lo que se puede hacer con “datos” se puede hacer con las funciones mismas.
>Tratar funciones como objetos permite la composición y abstracción de código de manera eficaz.

```js
def cuadrado(x):
    return x ** 2
funcion = cuadrado
print(funcion(5))  
```
### Recursividad
Sirve para resolver problemas dividiéndolos en subproblemas más pequeños y manejables.
Una función puede realizar un llamado a sí misma durante su ejecución.
```python
def suma_naturales(n):
    if n == 0:
        return 0
    else:
        return n + suma_naturales(n - 1)
```
La idea básica es dividir el problema en partes más pequeñas y aplicar la misma operación de suma a esas partes más pequeñas hasta llegar al resultado.
### Funciones lambda

Las funciones lambda son funciones anónimas y simples, convenientes para operaciones rápidas sin necesidad de definición formal.
Son más breves y se pueden definir en una sola línea de código.
Útiles para operaciones simples y rápidas sin la necesidad de una definición formal. 
Se utilizan comúnmente como argumentos en funciones como map, filter, reduce.

### Funciones de alto orden
Son aquellas funciones que pueden recibir otras funciones como parámetro y/o devolver funciones como resultado.
Permite construir operaciones complejas a partir de funciones más simples.

* Map: Aplica una función a cada elemento de un iterable ej: una lista y devuelve un nuevo iterable con los resultado.
   
```python
def convertirAAnios(x):
    return {
        x["nombre"].lower(),
        x["Edad"]/12,
        x["Vegetariano"]
    }
listaEstudiantes = [ 
    {"nombre":"Diego","Edad":552,"Vegetariano":False},
    {"nombre":"Diana","Edad":480,"Vegetariano":False},
    {"nombre":"Camila","Edad":312,"Vegetariano":True}
]

listaEdadAnios = list(map(convertirAAnios,listaEstudiantes))
print(listaEdadAnios)
```
* Filter:Filtra los elementos de un iterable según una función que retorna valores booleanos.
  
```python
def filtrarVegetarianos(x):
    x["Vegetariano"] = True

listaEstudiantes = [ 
    {"nombre":"Diego","Edad":552,"Vegetariano":False},
    {"nombre":"Diana","Edad":480,"Vegetariano":False},
    {"nombre":"Camila","Edad":312,"Vegetariano":True}
]
listaVegetarianos = list(filter(lambda x:x["Vegetariano"]==True,listaEstudiantes))
listaEdadAnios = list(map(convertirAAnios,listaVegetarianos))
print(listaEdadAnios)
```
* Reduce: Aplica una función a una secuencia de dos elementos, luego al resultado y al siguiente elemento, devuelve un solo valor.
  
```python
from functools import reduce

# Generación de la lista de enteros de prueba desde 2 hasta 100, 
# con incrementos de 2
listaNumerosPares = list(range(2, 101, 2))
print(listaNumerosPares)

# Cálculo de una sumatoria usando un iterador:
suma_iterador = 0
for i in listaNumerosPares:
    suma_iterador += i

print(suma_iterador)

# Serie sumatoria, usando la función reduce con función predefinida
def MiSuma(x, y):
    return x + y

# Reduce usando la función suma predefinida
sumaTotalReduce1 = reduce(MiSuma, listaNumerosPares)

# Reduce usando una función lambda para la suma
sumaTotalReduce2 = reduce(lambda x, y: x + y, listaNumerosPares)

# Otra función lambda de reducción (división)
productoTotalReduce = reduce(lambda x, y: x / y, listaNumerosPares)


print(f"Suma con reduce (MiSuma): {sumaTotalReduce1}")
print(f"Suma con reduce (lambda): {sumaTotalReduce2}")
print(f"Producto con reduce (lambda): {productoTotalReduce}")
```

Y aqui otro ejemplo de reduce pero con concatenación

```python
# Una lista de cadenas, para usar otra función de "reducción" (concatenación)
listaCadenas = ["Muchos", "años", "después", ",", "frente", "al", "pelotón", "de", "fusilamiento"]
# Reducción con concatenación
inicioCienAniosSOledad = reduce(lambda x, y: x + " " + y, listaCadenas)
print(inicioCienAniosSOledad)
```

* * *

# Programación Orientada a objetos en Python
La programación orientada a objetos (POO) es un paradigma de programación que se basa en el concepto de "objetos", los cuales pueden contener datos en forma de campos (también conocidos como atributos) y código, en forma de procedimientos (también conocidos como métodos)

## Conceptos de OOP
1- Abstracción, es la capacidad de definir objetos que representan conceptos abstractos o entidades del mundo real y los comportamientos asociados con ellos.

2- Encapsulamiento, consiste en ocultar los detalles internos de un objeto y exponer solo lo que es necesario.
Modificadores de acceso
Private: solo son accesibles desde dentro de la propia clase. No pueden ser accedidos directamente desde fuera de la clase.
Public: son accesibles desde cualquier parte del programa. Pueden ser accedidos directamente desde fuera de la clase.

3- Herencia: La herencia permite que una clase herede atributos y métodos de otra clase. La clase que hereda se llama subclase, y la clase de la que hereda se llama superclase.

4-Polimorfismo: El polimorfismo permite que diferentes clases proporcionen una interfaz común para ser utilizada de manera similar. Esto se puede lograr a través de la herencia y la implementación de métodos con el mismo nombre en diferentes clases.

```python
class ProductoInvestigacion:

    def __init__(self, pTitulo, pAutores):
        # Abstracción: La clase abstracta ProductoInvestigacion encapsula los atributos comunes
        self.titulo = pTitulo
        self.__autores = pAutores  # Encapsulación: __autores es un atributo privado

    def eliminarAutor(self, pAutor):
        # Abstracción: Eliminar un autor es una operación pública
        self.__eliminarAutor(pAutor)  # Encapsulación: Invocamos el método privado

    def __eliminarAutor(self, pAutor):
        # Encapsulación: Este método es privado y no debería ser accesible desde fuera
        # Lógica para eliminar un autor (implementación privada)
        pass


class ArticuloRevista(ProductoInvestigacion):

    def __init__(self, pTitulo, pAutores, pIssn, pVol, pNum, pAnio):
        super().__init__(pTitulo, pAutores)
        # Herencia: ArticuloRevista hereda de ProductoInvestigacion
        # Abstracción: La clase ArticuloRevista hereda y especializa atributos
        self.issn = pIssn
        self.vol = pVol
        self.num = pNum


class Libro(ProductoInvestigacion):

    def __init__(self, pTitulo, pAutores):
        super().__init__(pTitulo, pAutores)
        # Herencia: Libro hereda de ProductoInvestigacion
        # Abstracción: La clase Libro hereda y no añade atributos adicionales


class RegistroSoftware(ProductoInvestigacion):

    def __init__(self, pTitulo, pAutores):
        super().__init__(pTitulo, pAutores)
        # Herencia: RegistroSoftware hereda de ProductoInvestigacion
        # Abstracción: La clase RegistroSoftware hereda y no añade atributos adicionales


# Polimorfismo (potencial):
def procesar_producto(producto):
    # Aquí, producto puede ser un objeto de cualquier clase derivada de ProductoInvestigacion
    print(f"Título: {producto.titulo}")

# Crear instancias de las clases derivadas
articulo = ArticuloRevista("Artículo de Revista", ["Autor1", "Autor2"], "1234-5678", 10, 2, 2023)
libro = Libro("Libro de Investigación", ["Autor3", "Autor4"])
software = RegistroSoftware("Software de Investigación", ["Autor5", "Autor6"])

# Llamar a la función con objetos de diferentes clases
procesar_producto(articulo)
procesar_producto(libro)
procesar_producto(software)
```
## Patrones de Diseño
Los patrones de diseño son soluciones generales y reutilizables para problemas comunes que surgen al diseñar software. Estos patrones ofrecen un enfoque probado y estructurado para resolver ciertos tipos de problemas
### Patrones Creacionales
Estos patrones se centran en cómo se crean las instancias de las clases, proporcionando flexibilidad en la creación de objetos.
#### Singleton
Garantiza que una clase tenga solo una instancia y proporciona un punto global de acceso a ella.
Beneficios del Singleton
1- evitar acceso concurrente a recurso compartido
2- tener un punto de acceso global a un recurso
Siglenton Clasico
```python
class ClassicSingleton:

    _instance_ = None

    def __init__(this):
        raise RuntimeError("invocar la función create_instance para crear objeto")
    
    #métodos de instancia
    def enqueueDocument(this, fileName, format):
        pass

    def dispatchDocument(this, fileName):
        pass

    def deleteDocument(this, fileName):
        pass
    
    #un "classmethod es un método estático"
    @classmethod
    def createInstance(this):
        if this._instance_ is None:
            #lo hace solo una vez, cuando no se ha instanciado ningún objeto
            this._instance_ = this.__new__(this) 
            #__new__ lo usa internamente __init__ para crear una nueva instancia de clase
        
        return this._instance_
    
######### fin de implementación del singleton

#tratamos de crear con el método init:
#printerPool1 = ClassicSingleton()
#printerPool2 = ClassicSingleton()

#Ejemplo de uso del singleton clásico:

printerPool1 = ClassicSingleton.createInstance() #lo llamo como método estático, no
                                                 #método de objeto
printerPool2 = ClassicSingleton.createInstance()

print(printerPool1)
print(printerPool2)

print(printerPool1 == printerPool2)
```
Naive Siglenton
```python
#esta implementación "naive" reemplaza el método constructor por defecto por un
#método propio de instanciación
class naive_singleton():
    _instance_ = None
    #se va a lanzar error cuando se llame, para obligar a llamar al método create_instance
    def __init__(self):
        raise RuntimeError("use create_instance method instead")
    #Se usa este método en vez del inicializador para garantizar que se cree una sola instancia
    #classmethod garantiza que el método sea estático
    #cls se usa aquí como el self
    @classmethod 
    def create_instance(cls):
        #si no existe la instancia, la crea
        if cls._instance_  is None:
            cls._instance_ = cls.__new__(cls)
        #retorna la instancia
        return cls._instance_

#ambos objetos SON la misma instancia de la clase
printer_pool1 = naive_singleton.create_instance()
printer_pool2 = naive_singleton.create_instance()

print(printer_pool1)
print(printer_pool2)

#Debe mostrar si printer_pool1 y printer_pool2 corresponden a la misma instancia de clase (en este caso, es VERDADERO):
print(f"Son la misma instancia?: {printer_pool1 is printer_pool2}")
```
#### Factory Method
Define una interfaz para crear un objeto, pero deja que las subclases alteren el tipo de objetos que se crearán.
```python

class TranslateEnglish():
    def __init__(self):
        self.translations  = {"mamá":"mom", "papá":"dad"}
    def translate(self, msg):
        return self.translations.get(msg)

class TranslateFrench():
     def __init__(self):
        self.translations  = {"mamá":"mére", "papá":"pére"}
     def translate(self, msg):
        return self.translations.get(msg)

class TranslateGerman():
    def __init__(self):
        self.translations  = {"mamá":"mama", "papá":"papa"}
    def translate(self, msg):
        return self.translations.get(msg)

class TranslationFactory():
    def __init__(self):
        self.translators = { "English":TranslateEnglish, "French": TranslateFrench, "German":TranslateGerman  }
    def return_translator(self, language):
        return self.translators[language]

if __name__ == "__main__":

    my_factory = TranslationFactory()
    my_en_translator = my_factory.return_translator("English")
    my_fr_translator = my_factory.return_translator("French")
    my_gr_translator = my_factory.return_translator("German")
```
### Patrones Estructurales
Estos patrones se centran en cómo se componen las clases y objetos para formar estructuras más grandes.
#### Adapter
El Adapter permite que interfaces incompatibles trabajen juntas.
> Ejemplo Adapter

```python
# Definición de la interfaz XML
class XMLInterface:
    def get_data(self):
        pass

    def set_data(self, data):
        pass

# Clase concreta que implementa la interfaz XML
class Source(XMLInterface):
    def get_data(self):
        return "<XML>data</XML>"

    def set_data(self, data):
        # Implementación del método set_data para la fuente XML
        print(f"Estableciendo datos XML: {data}")

# Interfaz destino para texto
class TxtInterface:
    def get_data(self):
        pass

    def set_data(self, data):
        pass

# Adaptador que convierte la interfaz XML a la interfaz de texto
class Adapter(TxtInterface):
    _source = None

    def __init__(self, source):
        self._source = source

    def get_data(self):
        return "datos de texto plano"

    def set_data(self, data):
        # Aquí puedes implementar la lógica de conversión si es necesario
        self._source.set_data(data)

# Cliente que utiliza la interfaz de texto
class ClienteTxt:
    _source_type = None

    def __init__(self, source_type):
        self._source_type = source_type

    def obtener_datos_cliente(self):
        if self._source_type.get_data() == "datos de texto plano":
            print("Datos correctos")
        else:
            print("Datos incorrectos")

# Uso del código
fuente_xml = Source()
adaptador = Adapter(fuente_xml)
mi_cliente = ClienteTxt(adaptador)

mi_cliente.obtener_datos_cliente()
```
### Patrones de Comportamiento
Estos patrones se centran en cómo se comunican y colaboran las clases y objetos.
#### Observer
Define una dependencia uno a muchos entre objetos, de modo que cuando un objeto cambia su estado, todos sus dependientes son notificados y actualizados automáticamente
```python
#Clase Publisher que se encarga de actualizar o notificar a los 
#subscriptores
class Publisher:
    #Inicializar lista de observadores
    def __init__(this):
        this._observers = []

    def addSubscriber(this, newSubscriber):
        this._observers.append(newSubscriber)

    def removeSubscriber(this, subscriber):
        this._observers.remove(subscriber)

    def notifySubscribers(this,message):
        #enviar message a todos los subscribers en la lista:
        for subscriber in this._observers :
            subscriber.update(message)

class Subscriber:

    def Update(this, message):
        pass

class SubscriberType1(Subscriber):

    def Update(this, message):
        #return super().Update(message)
        print(f"Subscriber 1 recibió mensaje {message}")

class SubscriberType2(Subscriber):

    def Update(this, message):
        print(f"")

#Método principal:
if __name__ == "__main__":

    #crear publisher:
    publisher1 = Publisher()

    #crear subscriptores u "observers"
    observer1 = SubscriberType1()
    observer2 = SubscriberType2()

    #agregar subscriptores:
    publisher1.addSubscriber(observer1)
    publisher1.addSubscriber(observer2)

    #notificar subscriptores:
    publisher1.notifySubscribers("checking my subscribers...")
```
#### Strategy
Strategy es un patrón de diseño de comportamiento que te permite definir una familia de algoritmos, colocar cada uno de ellos en una clase separada y hacer sus objetos intercambiables.
```python
#clase que define una estrategia en general
class Strategy:
    def execute():
        pass

#estrategias concretas:
class ConcreteStrategyA(Strategy):
    def execute(self):
        print ("Ejecutando estrategia concreta A")

class ConcreteStrategyB(Strategy):
    def execute(self):
        print("Ejecutando estrategia concreta B")

#la clase Context es la que le permite al cliente ejecutar la estrategia correspondiente:
class Context:
    def __init__(self,strategy:Strategy):
        self.strategy = strategy

    def execute_strategy(self):
        self.strategy.execute()

#ejemplo de uso del patrón strategy (general):
#usando la estrategia A
strategyA = ConcreteStrategyA()
contexto_str1 = Context(strategyA)
result_str1 = contexto_str1.execute_strategy()

#usando la estrategia B
strategyB = ConcreteStrategyB()
contexto_str2 = Context(strategyB)
result_str2 = contexto_str2.execute_strategy()
```
# Programación Multihilo en Java

La programación multihilo, es una técnica en la que un programa se descompone en unidades más pequeñas de ejecución llamadas hilos. Un hilo es la unidad básica de procesamiento de la CPU y representa una secuencia de instrucciones que pueden ejecutarse de forma independiente, aunque comparten el mismo espacio de memoria y recursos del sistema.

### Conceptos
#### Hilo
Un hilo es una unidad más pequeña dentro de un proceso que ejecuta una secuencia de instrucciones de manera independiente. Los hilos comparten el mismo espacio de memoria y recursos del proceso padre.

#### Multitarea
La multitarea se refiere a la ejecución simultánea de múltiples tareas. En el contexto de la programación con hilos, la multitarea se logra mediante la ejecución simultánea de varios hilos dentro de un proceso.

#### Concurrencia 
La concurrencia es la ejecución aparentemente simultánea de múltiples tareas, pero no necesariamente al mismo tiempo exacto.
```js
ublic class HilosSimples {	
	
	static void hiloMensaje(String mensaje)
	{
		String nombreHilo = Thread.currentThread().getName();
		System.out.println("Hilo:"+nombreHilo+",Mensaje:"+mensaje);
	}		
	
	//clase estática para el segundo hilo del programa:
	private static class CicloMensajes implements Runnable
	{
		@Override
		public void run() {
			//cola de mensajes:
			String messages[] = {
					"Este",
					"es",
					"el",
					"curso",
					"de",
					"lenguajes",
					"de",
					"programación"
			};
			
			for(String mensaje: messages)
			{
				try {
					Thread.sleep(2000);
					hiloMensaje(mensaje);
				} catch (InterruptedException e) {
					// TODO Auto-generated catch block
					hiloMensaje("No he terminado!");
				}					
			}			
		}		
	}	
	//hilo principal: método main:
	public static void main(String args[])
	{
		
	}
}
}
```
>Otro ejemplo de hilos

```python
public class MainClass {

    public static void main(String[] args) {
        Account myAccount = new Account(250000);

        // 1. Crear 8 hilos para realizar retiros concurrentes sobre la cuenta:
        Thread[] hilosRetiro = new Thread[8];

        for (int i = 0; i < hilosRetiro.length; i++) {
            hilosRetiro[i] = new Thread(() -> myAccount.withdraw(100000));
            hilosRetiro[i].start();
        }

        // 2. Unir los hilos a este hilo principal (main)
        // e imprimir el id de cada hilo:
        try {
            for (Thread t : hilosRetiro) {
                t.join();
                System.out.println("Hilo con id: " + t.getId());
            }

        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        // De aquí en adelante, se espera que todos los hilos de retiro terminen
        System.out.println("Balance final: " + myAccount.getBalance());
    }
}

class Account {
    private int balance;

    public Account(int initialBalance) {
        this.balance = initialBalance;
    }

    public synchronized void withdraw(int amount) {
        if (amount > balance) {
            System.out.println("No hay fondos suficientes para el retiro.");
        } else {
            balance -= amount;
            System.out.println("Retiro exitoso. Saldo restante: " + balance);
        }
    }

    public synchronized void deposit(int amount) {
        balance += amount;
        System.out.println("Depósito exitoso. Saldo actual: " + balance);
    }

    public int getBalance() {
        return balance;
    }
}

```


