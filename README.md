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

> Ahora crearemos otro archivo en nuestro escritorio, con el nombre `words` y la extension `.rb`
>	en el cual colocaremos le siguiente codigo:
>	```ruby
class Ejemplo
  @@total_chars = 0
  def initialize(word)
    @word_chars  = word.length
    puts "La palabra #{word}, tiene #{@word_chars} caracteres"
    @@total_chars += @word_chars
    get_total_chars
  end 
  def get_total_chars
    puts "el total de caracteres son #{@@total_chars}"
  end
end
dejemplo1 = Ejemplo.new('Hello Word')
dejemplo1.get_total_chars
dejemplo2 = Ejemplo.new("I Love Ruby")
dejemplo2.get_total_chars
dejemplo3 = Ejemplo.new("I <3 Ruby")
dejemplo3.get_total_chars
```
> 	Despues nos dirigiremos al sitio donde creamos el archivo desde la terminal y lo invocamos de la siguiente manera:
>	`ruby words.rb`

>	En la teminal podremos observar que se muestra lo siguiente: ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/words.PNG)

# Generando el primer proyecto en Rails.
>	Abrimos una nueva ventana la terminal y tecleamos lo siguiente: `Cd: /Sites`
>	Después de haber hecho lo anterior tecleamos lo siguiente `rails new votos`
>	Ahora entramos a nuestro nuevo proyecto `Cd: votos`
>	Una vez dentro de nuestro nuevo proyecto comprovaremos que se genero con exito, por lo cual proseguiremos a iniciar el servidor de ruby con le siguiente comando, `rails server` o `rails s`, si todo va bien en consola debe de aparecer lo siguiente: ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/server.PNG)
>	Despues de esto, abrimos nuestro navegador y escribimos la siguiente dirección: 

>	http://localhost:3000/

>	En nuestro navegador se debe de desplegar lo siguiente:  ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/railsRun.PNG)
> # Generando vistas & Controladores
>	Para  decir un HOLA MUNDO en rails, lo primero que haremos es generar una vista, la cula estableceremos como la vista principal de nuestro proyecto, lo cual lo realizaremos con los comandos de consola que Rails trae predefinidos.
>	Para crear un nuevo controlador, necestiamos correr el generador de controladores y decirle que quieres un controlador llamado "welcome" con una acción llamada "index", lo cual se hace escribiendo la siguiente linea en nuestra terminal (estando en la carpeta de nuestro proyecto):
>	 `rails generate controller principal index`
>	Si todo salio como debería, en consola nos debe de desplegar lo siguiente:
>	 ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/generatePrincipal.PNG)
>	Para comprobar que todo funciona correctamente iremos a la siguiente dirección.

>	http://localhost:3000/principal/index

>	Donde podremos ver lo siguiente:
>	 ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/principalWeb.PNG)