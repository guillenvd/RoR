# Ruby on Rails: La primera frontera.

> `Lecciones`
>  * Inicio con ruby.
>  * Generando el primer proyecto en Rails.
>  * Generando vistas y controladores.
>  * Integrando Bootstrap.

## Instalando Ruby on Rails.
* Windows & Mac

> Para Windows y Mac existe un instalador el cual se encuentra en el siguiente link. 
> http://rubyinstaller.org/
> Se debe de instala la versión 2.0

* Para GNU/Linux.
> Linux se debe de instalar RVM 

# Iniciando con Ruby.

> Escribe `irb` en la terminal para inicializar el intérprete Interactivo de Ruby.
> Así se debería de ver nuestra terminal.
![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/cmd-irb.PNG)
> En esta ventana de la terminal teclearemos lo siguiente (espere a las instrucciones):
>	*  puts "Hola Mundo"
>	*  1+5
>	*  2*3
>	*  3**3
>	*  variable = 5
>	*  variable * 2
>	*	hash = {"foo" => "bar", "bar" => "foo"}
>	*	hash['foo']
>	*	hash.fetch('foo')
> 	*	frutas = ["kiwi", "fresa", "ciruela"]
> 	*	frutas = frutas + ["naranja"]
> 	*	frutas = frutas - ["kiwi"]
> 	*	array = [1,2,3,4,6,7,8,9,10]
>	*	(1...10).to_a
>	*	(1..10).to_a
>	*	('a'..'z').to_a
>	*	array.each {|elemento| puts elemento*2 }
>	*	array.map {|elemento| elemento*2 }
>	*	array.each { |j| puts "el elemento es: #{j}" }
>	*	frutas.class
>	*	frutas.methods 
>	*	frutas.methods.sort
>	*	frutas.length
>	* 	array.first
>	* 	array.last
>	* 	array.first(2)
>	* 	array.min
>	* 	array.max
>
>	###  *Clases, Objetos y Variables*
>	Para esta parte crearemos un archivo en nuestro escritorio, con el nombre `yield` y la extension `.rb`
>	en el cual colocaremos le siguiente codigo:
>	```ruby
def test
  puts "ejecutando código dentro del método test"
  yield
  puts "ejecutando nuevamente el código dentro del método test"
end
test { puts "ejecutando el código dentro del bloque que hemos pasado como argumento" }
```
> 	Despues nos dirigiremos al sitio donde creamos el archivo desde la terminal y lo invocamos de la siguiente manera:
>	`ruby yield.rb`

>	En la teminal podremos observar que se muestra lo siguiente: ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/yield.PNG)
>	###  *Tipos de Variables*
> 	En ruby existen 5 tipos de variables, las cuales son:
>	* Variables locales:

>	```ruby
		my_var = "Hola Mundo"
>	```

>	* Variables globales:

>	```ruby
		$my_global_bar = "Estoy accesible en cualquier lugar :("
>	```

>	* Variables constantes:

>	```ruby
		# alternativa 1
		PI = 3.141592653589793
		# alternativa 2
		Pi = 3.141592653589793
>	```

>	* Variables de Clase:

>	```ruby
	class Persona
	  @@class_variable = 10
	end
>	```

>	* Variables de Instancia:

>	```ruby
class Example
 def some_method
    @instance_var = "Hola soy una variable de instancia y vivo dentro de un objeto"
  end
end
>	```

