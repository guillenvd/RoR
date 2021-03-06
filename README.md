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

> Probar

> `gem --version`

> `ruby --version`

> `rails --version`

> `sqlite3 --version`

> `gem install json`

> Sí en la línea de `gem install json` no se descargo la gema seguir los siguentes pasos:
> * Bajar: AddTrustExternalCARoot-2048.pem del siguiente link:
> * https://mega.nz/#F!Q5cwEAoQ!bZ1RFmCcN2tXRzMID9SpSQ
> * Encontrar la carpeta de `RailsInstaller`, seguro esta en la raíz de C.
> * Ir a la ruta `RailsInstaller\Ruby2.0.0\lib\ruby\2.0.0\rubygems\ssl_certs`
> * Y colocar el archivo en la carpeta ssl_certs.
> * Al probar `gem install json` debe de funcionar correctamente.

> * Por ultimo colocamos
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
> 	Después nos dirigiremos al sitio donde creamos el archivo desde la terminal y lo invocamos de la siguiente manera:
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
> 	Después nos dirigiremos al sitio donde creamos el archivo desde la terminal y lo invocamos de la siguiente manera:
>	`ruby words.rb`

>	En la teminal podremos observar que se muestra lo siguiente: ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/words.PNG)

# Generando el primer proyecto en Rails.
>	En una nueva ventana abrimos la terminal y tecleamos lo siguiente: `Cd: /Sites`
>	Después de haber hecho lo anterior tecleamos lo siguiente `rails new votos`
>	Ahora entramos a nuestro nuevo proyecto `Cd: votos`
>	Una vez dentro de nuestro nuevo proyecto comprovaremos que se generó con exito, por lo cual proseguiremos a iniciar el servidor de ruby con le siguiente comando, `rails server` o `rails s`, si todo va bien en consola debe de aparecer lo siguiente: ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/server.PNG)
>	Después de esto, abrimos nuestro navegador y escribimos la siguiente dirección: 

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
> Al abrirlo podremos ver que unicamente tenemos una ruta declarada: ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/routes.PNG)
> Ahora procederemos a cambiar la línea 2, por lo siguiente:

> ```ruby
  ...  
    get 'principal' => 'principal#index', as: :principal
  ...
> ```

> y por ultimo agregaremos una línea más.

> ```ruby
    ...
      root 'principal#index'
    ...
> ```

> nuestro archivo `routes.rb` debe de quedar de la siguiente manera: ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/routesPrincipal.PNG)

> Ahora al abrir nuestra aplicación, desde la routa `http://localhost:3000/` nos debe de desplegar la vista principal, como se ve a continuación: ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/principalPrincipal.PNG)

> Ahora iremos a trabajar con el controlador y la vista un poco, los cuales se encuentran en la siguiente dirección:
> Las vistas estan en: `proyecto/app/views/principal`
> Los controladores estan en: `proyecto/app/views/controllers`

> ### *Generando un CRUD*
> Ya que sabemos como crear una vista, controlador y una acción, ahora vamos a generar un crud, con el cual podamos crear, leer, actualizar y eliminar objetos de una BD.

> #### *Creando Una Migracion*
> Nuestra primera tabla tendra los campos `id`, `titulo` & `descripcion`, esto lo realizaremos automáticamente con el comando `Scaffold` el cual nos generará nuestro esquema de la tabla, el modelo, vista y controlador del mismo, en este caso de tema, en la ventana de terminal escribiremos lo siguiente (dentro del directorio de nuestro proyecto):

> `rails generate scaffold tema titulo:string descripcion:text --skip-stylesheets --skip-javascripts `

> Seguido de:

> `rake db:migrate`

> ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/rakeTemas.PNG)

> Ahora si corremos el siguiente comando: 

> `rake routes` 
> Con el cual veremos lo siguiente:

> ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/rakeRoutes.PNG)

> Ahora prueba con lo siguiente:
> ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/urlConsole.PNG)

> Después de haber realizado lo anterior si nos dirigimos en nuestro navegador a la siguiente liga `http://localhost:3000/temas` , nos debera de aparecer una ventana como la siguiente: ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/temasIndex.PNG)

> Como podermos ver nuestra base de datos se encuentra vacía, para no tardar en crear registros vamos a generar una semilla, vamos a editar el archivo en la ruta `votos/db/seeds.rb` y abriremos el archivo y colocaremos lo siguiente en el:

> ```ruby
  Tema.create(titulo: 'Titulo 1', descripcion: 'Contenido 1')
  Tema.create(titulo: 'Titulo 2', descripcion: 'Contenido 2')
  Tema.create(titulo: 'Titulo 3', descripcion: 'Contenido 3')
  Tema.create(titulo: 'Titulo 4', descripcion: 'Contenido 4')
  Tema.create(titulo: 'Titulo 5', descripcion: 'Contenido 5')
  Tema.create(titulo: 'Titulo 6', descripcion: 'Contenido 6')
  Tema.create(titulo: 'Titulo 7', descripcion: 'Contenido 7')
  Tema.create(titulo: 'Titulo 8', descripcion: 'Contenido 8')
  Tema.create(titulo: 'Titulo 9', descripcion: 'Contenido 9')
  Tema.create(titulo: 'Titulo 10', descripcion: 'Contenido 10')
>```

> Despues en la terminal introducimos lo siguiente:

> `rake db:seed`

> Ahora para poder dirigirnos con un link desde nuestra vista principal a los temas pondremos lo siguiente al final del index de principal:

> ```ruby
  ...
   <%= link_to 'Ir a temas', temas_path %>
  ...
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
  ...
   has_many :votos, dependent: :destroy
  ...
> ```

> ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/temaHas.PNG)

> Votos

> ```ruby
  ... 
   belongs_to :tema
  ...
> ```

> ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/votoBelongs.PNG)

> Estando en nuestro proyecto en la terminal introducimos `rails c` y probamos lo siguiente:

| Clase de Modelo / métodos de asociación | Métodos de Instancia de Modelo |
| ------------- | ------------- |
| Tema.first  | VarTema.titulo  |
| Tema.last  | VarTema.titulo = 'New titulo'  |
| Tema.all | VarTema.update_attributes(titulo: 'New titulo')  |
| Tema.count  | VarTema.update_attributes(titulo: 'New titulo') |
| Tema.find_by_id(5)   | VarTema.save! |
| Tema.destroy_all  | VarTema.destroy |
| VarTema.votos.count | VarTema.votos.first.destroy |
| VarTema.votos.create |  |
| VarTema.votos.destroy_all |  |

> Ya que hemos jugado un poco es momento de que podamos votar a través de la aplicación web, para lo cual tenemos que ir al controlador de los temas para agregar un nuevo metodo


> ```ruby
...
  #Nuevo metodo para votar temas_controller.rb
  def upvote
    @tema = Tema.find(params[:id])
    @tema.votos.create
    redirect_to(temas_path)
  end
...
> ```

> Ahora abrimos nuestro archivo routes.rb y anexamos nuestro metodo `upvote` a nuestro CRUD TEMAS, editamos el controlador para que quede de la siguiente forma:

> ```ruby
...
  resources :temas do
    member do
      post 'upvote'
    end
  end
...
> ```

> ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/upVote.PNG)

> Ahora a nuestra vista `index` de temas le anexamos un botón de botar, el cual tendra una acción sobre el metodo upvote
 
 > ```ruby
 ...
    <td><%= pluralize(tema.votos.count, "voto") %></td>
    <td><%= button_to '+1', upvote_tema_path(tema), method: :post %></td>
 ...
> ```   

> Si realizamos todo bien, al ingresar a la ruta `http://localhost:3000/temas` nos debe de aparecer el index de la siguiente manera:

> ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/temasLike.PNG)


> Donde si damos click en el botón `+1` de algun tema, debe de incrementar los votos sobre dicho tema.

> # Integrando Bootstrap
> En este caso para integrar bootstrap a nuestro proyecto lo haremos en forma de depencencia, para lo cual iremos a nuestro archivo
> `Gemfile` de nuestro proyecto (este se encuentra en la raíz), y anexaremos la siguiente línea:

> ``` ruby
...
  gem 'bootstrap-sass'
...
> ```

> Nuestro archivo `Gemfile` debe de quedar de la siguiente manera:

> ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/bootstrapSass.PNG)

> Ahora para instalar las dependecias corremos el siguiente comando (desde el directorio de la aplicación):

> `bundle install`

> Una vez instalado las dependecias modificaremos el siguiente archivo `votos/app/assets/javascript/application.js` y agregaremos la siguiente línea

> `//= require bootstrap`  de tal manera que nuestro archivo quede de la siguiente forma:

> ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/bootstrapJs.PNG)

> Como ahora utilizamos archivos  Sass de Bootstrap, tenemos que renombrar el siguiente fichero: `votos/app/stylesheet/application.css` por `votos/stylesheet/application.scss`
> Y le anexamos una línea, la cual dice que utilizaremos bootstrap.

> `@import "bootstrap";`

> Ya tenemos todo listo para comenzar a utilizar `Bootstrap` en nuestro proyecto.
> Si no sabes sobre las clases disponibles de bootstrap o componentes puedes acceder a la siguiente página donde se encuentra toda la documentación de este framework.

> http://getbootstrap.com/
> ### Agregando nuestra propia hoja de estilo
> Para agregar nuestra propia hoja de estilo, la podemos agregar directo en `votos/app/assets/stylesheet/custom.css`
> Después tenemos que incializar la hoja de estilo en el siguiente archivo en  en `votos/app/config/initializers/assets.rb class="rb"></assets>`

> Nos debe de quedar algo así:
> ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/customAssetse.PNG)

> Ahora proseguimos a agregar la siguiente línea a la vista de la aplicación, nuestro archivo base, el cual se encuentra
> en la siguiente ruta `votos/app/views/layouts/application.html.erb`

> ```ruby 
  ...
    <%= stylesheet_link_tag    'custom', media: 'all', 'data-turbolinks-track' => true %>
  ...
>```

> Ahora ya depende de la imaginación de cada quien para editar las vistas y darle formato.
> ![Image of irb](https://github.com/guillenvd/RoR/blob/master/img/bootstrapImp.PNG)

> # Validaciones de campos.

> Como se puede apreciar, si intentamos generar un nuevo tema con los campos vacios o con una sola letra, este se genera
> sin ningun problema, para poder impedir que esto suceda debemos de agregar validaciones o restricciones en el modelo de
> temas `votos/app/models/tema.rb`, donde anexaremos lo siguiente.

> ```ruby
....
  validates :titulo, :descripcion, presence: true
   validates :titulo, length: {
      minimum: 2,
      maximum: 10,
      too_short: "Debe de tener al menos %{count} letras",
      too_long: "Debe de tener como maximo %{count} letras"
      }
....
>  ```

> Donde básicamente le decimos que valide que tanto titulo y descripción no estén vacios y a demas que titulo tenga como maximo 10 letras y como Mínimo 2.

> En esta página pueden encontrar más información sobre validaciones y otros temas.
> http://guides.rubyonrails.org/active_record_validations.html

#Contacto

> * Facebook: https://www.facebook.com/llenllen
> * Twitter: https://twitter.com/guillenvd
> * +Gmail: https://plus.google.com/u/1/+DavidGuillenVazquez1