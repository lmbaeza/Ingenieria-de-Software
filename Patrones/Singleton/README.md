# Singleton

Es un patron de diseño que permite limitar a uno el número de instancias posibles de una clase en nuestro programa, y proporciona un acceso global al mismo [1].

## Contenido

* [Singleton implementación en Python](#singleton-implementación-en-python)
* [Singleton implementación en Java](#singleton-implementación-en-java)

## Singleton implementación en Python

```python
class OnlyOne:
  class __OnlyOne:
    def __init__(self, arg):
      self.val = arg
    def __str__(self):
      return repr(self) + ' ' + self.val
  
  instance = None

  def __init__(self, arg):
    if not OnlyOne.instance:
      OnlyOne.instance = OnlyOne.__OnlyOne(arg)
    else:
      OnlyOne.instance.val = arg
  
  def __getattr__(self, name):
    return getattr(self.instance, name)
  
  def __str__(self):
    return str(self.instance)

x = OnlyOne('sausage')
print(x)
y = OnlyOne('eggs')
print(y)
z = OnlyOne('spam')
print(z)
print('\n')
print(x)
print(y)

# Out:
# <__main__.OnlyOne.__OnlyOne object at 0x7f72620a9ad0> sausage
# <__main__.OnlyOne.__OnlyOne object at 0x7f72620a9ad0> eggs
# <__main__.OnlyOne.__OnlyOne object at 0x7f72620a9ad0> spam


# <__main__.OnlyOne.__OnlyOne object at 0x7f72620a9ad0> spam
# <__main__.OnlyOne.__OnlyOne object at 0x7f72620a9ad0> spam
```

## Singleton implementación en Java

```java
public class SoyUnico {

    private String nombre;
    private static SoyUnico soyUnico;

    // El constructor es privado, no permite que se genere un constructor por defecto.
    private SoyUnico(String nombre) {
        this.nombre = nombre;
        System.out.println("Mi nombre es: " + this.nombre);
    }

    public static SoyUnico getSingletonInstance(String nombre) {
        if (soyUnico == null){
            soyUnico = new SoyUnico(nombre);
        } else{
            System.out.println("No se puede crear el objeto "+ nombre + " porque ya existe un objeto de la clase SoyUnico");
        }
        
        return soyUnico;
    }
    
    // metodos getter y setter

}

public class Main {

    public static void main(String[] args) {
        
        SoyUnico ricardo = SoyUnico.getSingletonInstance("Ricardo Moya");
        SoyUnico ramon = SoyUnico.getSingletonInstance("Ramón Invarato");
        
        // ricardo y ramon son referencias a un único objeto de la clase SoyUnico
        System.out.println(ramon.getNombre());
        System.out.println(ricardo.getNombre());   
    }
}
// Out:
// Mi nombre es: Ricardo Moya
// No se puede crear el objeto Ramón Invarato porque ya existe un objeto de la clase SoyUnico
// Ricardo Moya
// Ricardo Moya
```

# Bibliografia

* [[1]](https://devexperto.com/patrones-de-diseno-software/) A. Leiva, "Patrones de diseño de software - DevExperto", DevExperto, 2019. [Online]. Available: https://devexperto.com/patrones-de-diseno-software/

* [[2]](https://python-3-patterns-idioms-test.readthedocs.io/en/latest/Singleton.html) "The Singleton — Python 3 Patterns, Recipes and Idioms", Python-3-patterns-idioms-test.readthedocs.io, 2019. [Online]. Available: https://python-3-patterns-idioms-test.readthedocs.io/en/latest/Singleton.html.

* [[3]](https://jarroba.com/patron-singleton-en-java-con-ejemplos/) R. Maya, "Patrón Singleton en Java, con ejemplos", Jarroba, 2019. [Online]. Available: https://jarroba.com/patron-singleton-en-java-con-ejemplos .