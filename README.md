

--> Crear un proyecto llamado first_app (1 Punto)

        rails new first_app

--> Inicializar Git (1 Punto)

        claudio@Arrakis:git init
        Reinicializado el repositorio Git existente en /home/claudio/Biblioteca/EQ_Curso_Ruby_On_Rails/08_Desarrollo_Aplicaciones_Ruby_on_Rails/03_Aplicaciones_en_Rails/Dia_02/Desafio_Proyecto01/first_app/.git/

--> Añadir los cambios y hacer el primer committ (1 Punto)
claudio@Arrakis:git add .

        claudio@Arrakis:git commit -m "2022.04.19_00"
        [main (commit-raíz) bedfc98] 2022.04.19_00
        78 files changed, 1372 insertions(+)
        create mode 100644 .gitattributes
        create mode 100644 .gitignore
        create mode 100644 .ruby-version
        create mode 100644 Gemfile
        ......

--> Crear el controlador pages con las páginas one y two (2 Puntos)
        
        claudio@Arrakis:rails generate controller pages one two
      
        create  app/controllers/pages_controller.rb
        route  get 'pages/one'
              get 'pages/two'
        invoke  erb
        create    app/views/pages
        create    app/views/pages/one.html.erb
        create    app/views/pages/two.html.erb
        invoke  test_unit
        create    test/controllers/pages_controller_test.rb
        invoke  helper
        create    app/helpers/pages_helper.rb
        invoke    test_unit
      
--> Setear la página one como página de inicio (1 Punto)

        # Defines the root path route ("/")
        root "pages#one"

--> Agregar un título h1 con tu nombre completo en la página de inicio (0.5 Punto)

        <h1>Claudio Andres Zeiss Martinez</h1>


--> Ejecutar el comando rake routes en la terminal y obtener una captura de pantalla del resultado (0.5 Punto)

        imagen -> fisrtApp_Routes.png

--> Insertar la imagen de la captura de pantalla obtenida a la página two (1 Punto)

        <h1>Imagen de rails routes</h1>
        <%= image_tag "fisrtApp_Routes.png" %>

--> Añadir los cambios y hacer el segundo commit (0.5 Punto)

        claudio@Arrakis:git add .
        claudio@Arrakis:git commit -m "2022.04.19_01"
        [main e543da0] 2022.04.19_01
        7 files changed, 31 insertions(+), 1 deletion(-)
        create mode 100644 app/assets/images/fisrtApp_Routes.png
        create mode 100644 app/controllers/pages_controller.rb
        create mode 100644 app/helpers/pages_helper.rb
        create mode 100644 app/views/pages/one.html.erb
        create mode 100644 app/views/pages/two.html.erb
        create mode 100644 test/controllers/pages_controller_test.rb

--> Agregar el método three al controlador Pages (1 Punto)
        
        app->controllers->applicacion_controller.rb
        
          def three
          end

--> Agregar un archivo llamado three.html.erb a la carpeta views del controlador pages (0.5 Punto)

        app->views->pages->three.html.erb

--> En el archivo routes.rb agregar la ruta que apunta al controlador pages con el método three (1 Punto)

        get 'pages/one'
        get 'pages/two'
        get 'pages/three'
  
--> Agregar un título h2 y un párrafo Lorem ipsum en la página three (1 Punto)

        <h1>Pagina 3</h1>
        <h2>Parrafo</h2>
        <p>Esto es un gran parrafo donde es necesario hablar y hablar,, bla, bla, bla...
        </p>
        
--> Añadir los cambios y hacer el tercer commit (0.5 Punto)

        claudio@Arrakis:git add .
        claudio@Arrakis:git commit -m "2022.04.19_02"
        [main e80e188] 2022.04.19_02
         3 files changed, 9 insertions(+)
         create mode 100644 app/views/pages/three.html.erb

--> Agregar un navbar al layout (2 Puntos)

--> El navbar debe contener la clase navbar-inverse y su estructura sólo debe contener 3 links donde cada uno llevará a la página correspondiente (2 Puntos)

        app->views->layouts->application.html.erb

        <body>
        <!-- Barra de navegacion -->
        <nav class="navbar-inverse"> 
                <!-- Links --> 
                <ul class="navbar-nav"> 
                        <li class="nav-item"><%= link_to "one", pages_one_path %></li> 
                        <li class="nav-item"><%= link_to "two", pages_two_path %></li> 
                        <li class="nav-item"><%= link_to "three", pages_three_path %></li> 
                </ul> 
        </nav> 
        <%= yield %>
        </body>


--> Añadir los cambios y hacer el cuarto commit (1 Punto)

        claudio@Arrakis:git add .
        claudio@Arrakis:git commit -m "2022.04.19_03"
        [main 574fc62] 2022.04.19_03
         1 file changed, 10 insertions(+)

--> Crear un repositorio en GitHub (1 Punto)

        echo "# first_app" >> README.md
        git init
        git add README.md
        git commit -m "first commit"
        git branch -M main
        git remote add origin git@github.com:ClaudioZeiss/first_app.git
        git push -u origin main

--> Inicializar proyecto en Heroku y hacer push (2 Puntos)
        
   -- Cambiar base de datos sqlite3 por postgres (Heroku no soporta sqlite3) :
   
   Reemplazar el codigo en archivo database.yml (path : config/database.yml) por
      
        development:
                adapter: postgresql
                usarname: claudio
                password: desafio
                port: 5432
                host: localhost
                database: my_database_development
                pool: 5
                timeout: 5000

        test:
                adapter: postgresql
                usarname: claudio
                password: desafio
                port: 5432
                host: localhost  
                database: my_database_test
                pool: 5
                timeout: 5000

        production:
                adapter: postgresql
                database: my_database_production
                pool: 5
                timeout: 5000
        
   En el archivo Gemfile, reemplazar la linea
   
                gem "sqlite3", "~> 1.4"
   por
   
                gem "pg"
        
   Cargar la gema para trabajar con postgres en rails
   
        bundle install
        
   Creacion de las bases de datos en postgres
   
        rails db:create  
        
   Link Pagina Heroku
   
        https://non-startup.herokuapp.com/
      
