# Composer
Application-level package manager for the PHP programming language that provides a standard format for managing dependencies of PHP software and required libraries.

Create project
```
composer create-project laravel\laravel [project_name]
```

composer.json
- File chứa các composer dependencies của project.

Require
- Add package to project
```
$ composer require [name_package]
```
- Add Laravel UI
```
$ composer require laravel/ui --dev
$ php artisan ui vue
$ php artisan ui vue --auth     
```

# Artisan
    - The command-line interface của Laravel.
    - Assist with manage files in project
    list
        - List all commands of Artisan
        # Template
            $ php artisan list
    help    
        - Show information of another command
        # Template
            $ php artisan help [other command]
        # Code
            $ php artisan help view:cache
    serve
        - Serve the application on the PHP development server.
        # Template
            $ php artisan serve
    up
        - Bring the application out of maintenance mode
        - Như thế mới có thể run được application.
        # Template
            $ php artisan up
    down
        - Put the application into maintenance mode.
        # Template 
            $ php artisan down
    ui
        - Swap the front-end scaffolding for the application.
        - Chuyển ui của Laravel sang view
        # Code
            $ php artisan ui vue --auth
    tinker
        - Console environment to run directly php code
        # Template
            $ php artisan tinker
    migrate
        - Run migrations files.
        # Code
            $ php artisan migrate
        migrate:fresh
            - Reset and re-run all migrations.
            # Template
                $ php artisan migrate:fresh
    make
        make:controller
            - Tạo Controller
            # Template
                $ php artisan make:controller ['name controller']
        make:model
        # Template
            $ php artisan make:model ['name model']
            $ php artisan make:model ['name model'] -m //tạo luôn migrate luôn với model
            $ php artisan make:model ['name model'] -fmc //bonus factory + migration + controller
        make:policy
        - Policy là class định nghĩa quyền thực thi vào một đối tượng cụ thể nào đó.
            # Template
                $ php artisan make:policy [name_policy]
        - `-m [name_model]` : gán directly policy với model cụ thể
            # Code
                $ php artisan make:policy ProfilePolicy -m Profile
        make:channel
            - Create a new channel class
                $ php artisan make:channel [name_channel]
        storage:link
            - Create link từ public tới storage
            - Như thế thì mới có thể lấy directly resource  trong storage = url
                # Code
                    $ php artisan storage:link
                    //sau đó để get file trong storage
                    /storage/uploads/tên_sau_khi_upload

# Directory Structure
## app
Directory contains the core code of your application.

## bootstrap
Những file hỗ trợ cho framework chạy

## config
Directory contains all of your application's configuration files.
    
## database
Directory contains your database migrations, model factories, and seeds.

## public
This directory also houses assets such as images, JavaScript, and CSS.
- Những resources có thể lấy trực tiếp bởi view qua link.
            # File
                index.php

- The entry point for all requests entering your application and configures autoloading.
    
## resources
Un-compiled assets 
- such as LESS, SASS, or JavaScript.
- Directory contains your views as well as your raw.
    
views
```.blade.php```
- Rendering template.
- Chứa html

routes
Directory contains all of the route definitions for your application.
```web.php```
File contains routes that the `RouteServiceProvider` places in the `web` middleware group, which provides session state, CSRF protection, and cookie encryption. 
- Chứa các routes không phải stateless (RESTful API) => lưu trong đây
- `web.php` : register web routes for project.
- loaded by the RouteServiceProvider.
- Link url to Controller phù hợp
```
Route::get('/home', 'HomeController@index')->name('home');
//GET + /home -> HomeController @ index() 
//Route::get()->name('tên tắt') => <form method="GET" action="home"> 
//=> là call HomeController @ index() 
```
        - Truyền argument cho url
            Route::method('/url/{argument}', 'NameController');
            Route::get('/profile/{user}', 'ProfileController@index')->name('profile.show');

        api.php 
            - Contains routes that the `RouteServiceProvider` places in the `api` middleware group, which provides rate limiting. 
            - These routes are intended to be stateless, so requests entering the application through these routes are intended to be authenticated via tokens and will not have access to session state.
        console.php
            - Define console commands. 
            - Each Closure is bound to a command instance allowing a simple approach to interacting with each command's IO methods. 
            - Even though this file does not define HTTP routes, it defines console based entry points (routes) into your application.

        channels.php
            - Register all of the event broadcasting channels that application supports.

## storage
The `storage` directory contains your compiled Blade templates, file based sessions, file caches, and other files generated by the framework. 

## tests
Contains all test files

## ventor
    All dependencies.

## .env
Chứa configuration của project.
- Có chứa thông tin của database.

# App Directory
# Broadcasting
The `Broadcasting` directory contains all of the broadcast channel classes for your application.
# Console
Contains all of the custom Artisan commands for your application.
# Http
All of the logic to handle requests entering application.
# Controllers
Chứa các file controller cho View

Khi submit form thì sẽ redirect to controller sử lý rồi redirect lại view.

Argument từ url truyền vào function = function argument
```
Route::get('/profile/{user}', 'ProfileController@index')->name('profile.show');
class ProfileController extends Controller
{
    public function index($user) {
    ...
```

# Middleware
Middleware là những process chạy trước khi requrest được xử lý.

# Model
## Đính kèm
### trait Illuminate\Database\Eloquent\Factories\HasFactory;
Có thể tạo Factory cho model này

### trait Illuminate\Notifications\Notifiable;

### class Illuminate\Foundation\Auth\User
Hay được đặt tên thành Authenticatable

## HasRelationships
- belongsTo
    - Ứng với 1 đầu của quan hệ 1-1 or đầu many trong quan hệ 1-many.
```$this->belongsTo(User::class);```
- hasOne
    - Ứng với đầu còn lai trong quan hệ 1-1
```$this->hasOne(Profile::class);```
- hasMany
    - Ứng với đầu 1 của quan hệ 1-many
```$this->hasMany(Post::class);```
- belongToMany
    - Ứng với 1 đầu của quan hệ Many-Many

# Request Lifecycle
    
## Lifecycle Overview
First Things
- Khi init application => call `index.php`
- `index.php` call `bootstrap/app.php`

HTTP / Console Kernels
- The incoming request is sent to either the HTTP kernel or the console kernel.
- Depending on the type of request that is entering the application.
- These two kernels serve as the central location that all requests flow through.
- HTTP request sẽ phải flow qua `HTTP/Kernel.php`
- The HTTP kernel also defines a list of HTTP middleware that all requests must pass through before being handled by the application.

## HTTP Classes
Request
- Là argument cho mọi controller function.
- Chứa thông tin của request.

input()
- Lấy input trong form của request.
- Thường chỉ return string
```$input = $request->input('name');```

query()
- Lấy argument trên url
```$argument = $request->query('name');```
    
all()
- Get all input & querys
- Return array
```$array = $request->all();```
    
has()
- Kiểm tra input | argument có tồn tại trong request không.
```$check = $request->has('name'); //return boolean```
    
hasAny()
- Kiểm tra có tồn tại 1 trong những input | argument trong request không.
```$check = $request->has(['name1', 'name2']); //return boolean```

# Database Directory
    Migrations
        - Là những file php thay thế cho sql để làm việc với databse
    Factories
        - Là những file để fake data cho model trong database.
        - Từ đó có thể tạo data có sẵn để mockup, test, …

# .blade.php
## Laravel-mix
laravel-mix là 1 package webpack compile rồi cho output ra folder mà mình chỉ định
- Thường thì sẽ compile từ folder "resource" ra folder "public" 

`npm run dev`
- Build ra 1 bản js + css trong folder `public`

webpack.mix.js
- file để webpack có thể merge js + css của folder `public` + `resoureces`

## Directives
`@auth`
- tương đương với `@if (auth()->user())`

`@guest`
- tương đương với `@if (!auth()->user())`

# Authenticate
## cookie
laravel_session

XSRF-Token

remember_web_{id}

## auth()
### atempt()

# Question
Event và Listener là gì? Dùng khi nào? Tại sao dùng? Ví dụ?
- Event là 1 sự kiện
- Listener là phương thức xử lý khi event diễn ra
- VD: Event là bạn đang buồn vì chuyện của crush, còn Listener chính là việc bạn xử lý cái event đó như thế nào
- Lý do mình dùng Event thay vì không phải dùng trực tiếp trong Controller đó là khi bạn muốn cập nhật dữ liệu của bảng khác mà không phải gọi nó lặp lại trong Controller.
- Có thể tái sử dụng 1 Event trong nhiều Controllers

Queue là gì? Tại sao lại phải dùng Queue? Có mấy loại? Ví dụ về sử dụng Queue?
- Queue là hàng đợi cho các Tasks
- Queue giúp chúng ta phân phối các task, cân bằng không gây trì trệ cho các task sắp tới
- 2 loại Queue là Queue đồng bộ và Queue bất đồng bộ
- VD: bảng Comment cần create 100 records
    - Queue sẽ giúp đặt

Lifecycle của laravel
