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

* Para GNU/Linux.
> Linux se debe de instalar RVM 

```ruby
 get 'principal' => 'principal#index', as: :principal
  get 'temas' => 'temas#index', as: :temas
  
  resources :temas do
    member do
      post 'upvote'
      post 'downvote'
    end
  end
```
  # match '/signup',  to: 'users#new'
  root 'principal#index'
