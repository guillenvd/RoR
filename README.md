# Ruby on Rails: La primera frontera.

> Lecciones
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

''' Ruby
 get 'principal' => 'principal#index', as: :principal
  get 'temas' => 'temas#index', as: :temas
  
  resources :temas do
    member do
      post 'upvote'
      post 'downvote'
    end
  end
'''
  # match '/signup',  to: 'users#new'
  root 'principal#index'


## Usage

TODO: Write usage instructions

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## History

TODO: Write history

## Credits

TODO: Write credits

## License

TODO: Write license