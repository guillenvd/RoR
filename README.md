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
> Se debe de instalar la versión 2.0

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
>	Para esta parte crearemos un archivo en nuestro escritorio, con el nombre `yield` y la extensión `.rb`
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
		$my_global_bar = "Estoy accesible en cualquier lugar :'("
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

> Ahora crearemos otro archivo en nuestro escritorio, con el nombre `words` y la extensión `.rb`
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
>	Para  decir un `HOLA MUNDO` en rails, lo primero que haremos es generar una vista, la cual estableceremos como la vista principal de nuestro proyecto, lo cual lo realizaremos con los comandos de consola que Rails trae predefinidos.
>	Para crear un nuevo controlador, necestiamos correr el generador de controladores y decirle que queremos un controlador llamado "principal" con una acción llamada "index", lo cual se hace escribiendo la siguiente línea en nuestra terminal (estando en la carpeta de nuestro proyecto):

>	 `rails generate controller principal index`

>	Si todo salio como debería, en consola nos debe de desplegar lo siguiente:
>	 ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/generatePrincipal.PNG)

>	Para comprobar que todo funciona correctamente iremos a la siguiente dirección:

>	http://localhost:3000/principal/index

>   Donde podremos ver lo siguiente:
>	 ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/principalWeb.PNG)
> Ahora, para poder establecer nuestra ruta, principal/index como pantalla principal, tenemos que ir al archivo donde se declaran las rutas de acceso, el cual se encuentra en la siguiente dirección, `proyecto/config/routes.rb` , procedemos a abrirlo para poder editarlo.
> Al abrirlo podremos ver que unicamente tenemos una routa declarada: ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/routes.PNG)
> Ahora procederemos a cambiar la línea 2, por lo siguiente:

> ```ruby
    get 'principal' => 'principal#index', as: :principal
> ```

> y por ultimo agregaremos una línea más.

> ```ruby
    root 'principal#index'
> ```

> nuestro archivo `routes.rb` debe de quedar de la siguiente manera: ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/routesPrincipal.PNG)

> Ahora al abrir nuestra aplicación, desde la routa `http://localhost:3000/` nos debe de desplegar la vista principal, como se ve a continuación: ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/principalPrincipal.PNG)

> Ahora iremos a trabajar con el controlador y la vista un poco, los cuales se encuentran en la siguiente dirección:
> Las vistas estan en: `proyecto/app/views/principal`
> Los controladores estan en: `proyecto/app/views/controllers`

> ### *Generando un CRUD*
> Ya que sabemos como crear una vista, controlador y una accion, ahora vamos a generar un crud, con el cual podamos crear, leer, actualizar y eliminar objetos de una BD.

> #### *Creando Una Migracion*
> Nuestra primera tabla tendra los campos `id`, `titulo` & `descripcion`, esto lo realizaremos automaticamente con el comando `Scaffold` el cual nos generará nuestro esquema de la tabla, el modelo, vista y controlador del mismo, en este caso de tema, en la ventana de terminal escribiremos lo siguiente (dentro del directorio de nuestro proyecto):

> `rails generate scaffold tema titulo:string descripcion:text`

> Seguido de:

> `rake db:migrate`

> ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/rakeTemas.PNG)

> Ahora si corremos el siguiente comando: 

> `rake routes` 
> Con el cual veremos lo siguiente:

> ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/rakeRoutes.PNG)

> Ahora prueba con lo siguiente:
> ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/urlConsole.PNG)

> Despues de haber realizado lo anterior si nos dirigimos en nuestro navegador a la siguiente liga `http://localhost:3000/temas` , nos debera de aparecer una ventana como la siguiente: ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/temasIndex.PNG)

> Para poder dirigirnos con un link desde nuestra vista principal a los temas pondremos lo siguiente al final del index de principal:

> ```ruby
   <%= link_to 'Ira a temas', temas_path %>
> ```

> Como realizaremos votaciones sobre temas, tenemos que generar una tabla que registre cada voto.
> Esta tabla contendra el campo `id` y `tema_id`, proseguimos a escribir lo siguiente en la terminal:

> `rails generate model voto tema_id:integer`

> `rake db:migrate`
> `Ahora no realizaremos scaffold, ya que no se necesita`

> Si todo salio bien en nuestra terminal dede de salir algo parecido a esto:
> ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/votosRake.PNG)

> Como ya se mencionó, podemos votar sobre los temas, entonces podemos deducir que tenemos que marcar las relaciones entre estas tablas, lo cual se hace directo en el modelo de cada una, los modelos se encuentran en la siguiente ruta.

> `votos/app/models/`

> Procedemoa abrir los modelos de temas y de votos y los editamos de tal manera que nos queden de la siguiente forma:
> Temas

> ```ruby
   has_many :votos, dependent: :destroy
> ```

> ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/temaHas.PNG)

> Votos

> ```ruby
   belongs_to :tema
> ```

> ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/votoBelongs.PNG)

> Estando en nuestro proyecto en la terminal introducimos `rails c` y probamos lo siguiente:

| Clase de Modelo / métodos de asociación | Métodos de Instancia de Modelo |
| ------------- | ------------- |
| Tema.first  | mi_tema.titulo  |
| Tema.last  | mi_tema.titulo = 'New titulo'  |
| Tema.all | mi_tema.update_attributes(titulo: 'New titulo')  |
| Tema.count  | mi_tema.update_attributes(titulo: 'New titulo') |
| Tema.find_by_id(5)   | mi_tema.save! |
| Tema.destroy_all  | mi_tema.destroy |
| mi_tema.votos.count | mi_tema.votos.first.destroy |
| mi_tema.votos.create |  |
| mi_tema.votos.destroy_all |  |

> Ya que hemos jugado un poco es momento de que podamos votar atravez de la aplicación web, para lo cual tenemos que ir al controlador de los temas para agregar un nuevo metodo


> ```ruby
  #Nuevo metodo para votar temas_controller.rb
  def upvote
    @tema = Tema.find(params[:id])
    @tema.votos.create
    redirect_to(temas_path)
  end
> ```

> Ahora abrimos nuestro archivo routes.rb y anexamos nuestro metodo `upvote` a nuestro CRUD TEMAS, editamos el controlador para que quede de la siguiente forma:

> ```ruby
  resources :temas do
    member do
      post 'upvote'
    end
  end
> ```


> ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/upVote.PNG)

> Ahora a nuestra vista `index` de temas le anexamos un boton de botar, el cual tendra una accion sobre el metodo upvote
 
 > ```ruby
    <td><%= pluralize(tema.votos.count, "voto") %></td>
    <td><%= button_to '+1', upvote_tema_path(tema), method: :post %></td>
> ```   
