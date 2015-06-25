## Notice
I envision a system with just this components, [waifung0207](https://github.com/waifung0207/) seems to have had this idea some time ago, and is now porting it to CodeIgniter 3 and the lastest version of the other components.

This is a copy of his work, where I can make experiments and maybe help along or follow my own path.

So, please use the project [ci_bootstrap_3](https://github.com/waifung0207/ci_bootstrap_3/) from wayfung0207.

--- 

For my version of this project, read more at http://dreamerworks.github.io/rockstart/.

---
 

## CodeIgniter 3 Bootstrap  (from here down is the Original copy)

**Work in progress**

A starter template that supports multi-tenant (Frontend / Admin Panel / API) website in a single application.

This repository is developed upon the following tools: 
* [CodeIgniter](http://www.codeigniter.com/) (v3.0.0) - PHP framework
* [CodeIgniter HMVC Extensions](https://bitbucket.org/wiredesignz/codeigniter-modular-extensions-hmvc) - modular structure by [wiredesignz](http://wiredesignz.co.nz/)
* [Bootstrap](http://getbootstrap.com/) (v3.3.5) - popular frontend framework
* [Grocery CRUD](http://www.grocerycrud.com/) (v1.5.1) - feature-rich library to build CRUD tables
* [Image CRUD](http://www.grocerycrud.com/image-crud) (v0.6) - CRUD library for image management
* [AdminLTE](https://github.com/almasaeed2010/AdminLTE) (v2.1.2) - bootstrap theme for Admin Panel


### Features

This repository contains setup for rapid development:
* Multi-tenant (e.g. Frontend Website, Admin Panel, API) website in single application
* Modular design by CodeIgniter HMVC extension
* Custom config files (sites.php, locale.php) for easy configuration of website behavior
* Admin Panel with AdminLTE v2 theme, and Grocery CRUD integration
* Admin Panel includes usage of [Sortable](http://rubaxa.github.io/Sortable/) library
* API Site to handle RESTful endpoints, with shortcut functions to grab parameters and display results
* User authentication for Frontend Website (Sign Up, Login, Forgot Password, etc.)
* User authentication for Admin Panel (Login, Change Password, etc.)
* Preset layouts and templates
* Preset asset pipeline (e.g. minify scripts, image optimization) via Gulp (reference from [gulp-starter 2.0 branch](https://github.com/greypants/gulp-starter/tree/2.0))
* Form Builder library to help with form rendering with Bootstrap theme, form validation, etc.
* Breadcrumb handling
* Multilingual support
* Email config setup
* Functions to be called from CLI (e.g. daily cron job, database backup)
* ... more coming!


### Folder Structure

Explanation on the folder structure which supports HMVC (only showing the highlighted folders and files).

```
application/                    --- Main CodeIgniter source files
    config/
        production/             --- Configuration when ENVIRONMENT is set as "production"
        autoload.php            --- By default, some files are loaded for this repo
        database.php            --- Need to verify to ensure connection with MySQL database
        email.php               --- Created to centralize email configuration (preset: using Mandrill service)
        form_validation.php     --- Created to centralize validation forms for all forms, include ReCAPTCHA settings
        routes.php              --- Changed default controller from Welcome to Home
        site.php                --- Core configuration file for Frontend Website; same format also applied to Admin module
    controllers/                --- Controllers for Frontend Website; extends from MY_Controller (except Cli)
        Cli.php                 --- Utility function that can only be called from command line
        Home.php                --- Default controller for Frontend Website        
        Language.php            --- Controller to handle language switching
    core/                       --- Extending CodeIgniter core classes; can also be used within modules
        MY_Controller.php       --- Important class which contains shared logic of all controllers
        MY_Form_validation.php  --- Contains additional rule for validation
        MY_Loader.php           --- Required for HMVC extension
        MY_Model.php            --- Contains shared function for model classes (can consider to replace by https://github.com/jamierumbelow/codeigniter-base-model)
        MY_Router.php           --- Required for HMVC extension
    helpers/                    --- Contains custom helper functions being used throughout this repo
    language/                   --- Preset language files
    libraries/                  --- Custom libraries (e.g. Data Importer, Form Builder)
    models/                     --- Sample model extending from MY_Model
    modules/                    --- Each module can be accessed by http://{base_url}/{module_name}/{module_controller}/, etc.
        admin/                  --- Module for Admin Panel
            config/             --- Configuration for Admin Panel (overriding application/config/)
            controllers/        --- Controllers for Admin Panel; also extends from MY_Controller
            libraries/          --- Libraries from Grocery CRUD and Image CRUB
            models/             --- Models only being used in Admin panel
            views/              --- Views for Admin Panel; can reuse Frontend views, or override by using same path/filename
        api/                    --- Another module specific for API endpoints
    third_party/
        MX/                     --- Required for HMVC extension
    views/                      --- Views for Frontend Website, can also be used by modules unless overrided
assets/
    css/                        --- Custom CSS files append to each site
    dist/                       --- Minified scripts, stylesheets and optimized images via Gulp tasks
    fonts/                      --- Font files copied via Gulp tasks
    grocery_crud/               --- Asset files from Grocery CRUD library
    image_crud/                 --- Asset files from Image CRUD library
    images/                     --- Source image files before optimization
    js/                         --- Custom CSS files append to each site
    uploads/                    --- Default directory of upload files, where permission should set as writable
gulpfile.js/                    --- Task runner following gulp-starter 2.0 practice
screenshots/                    --- Screenshot images for preview
sql/                            --- MySQL data which contains preset user data
system/                         --- CodeIgniter core files (unchanged as clean CI3 installation)
.htaccess                       --- URL rewrite for Apache web server (require mod enabled)
```


### Screenshots

Frontend - Home: 

![](screenshots/frontend_home.png "Frontend Home")

Admin Panel - Home: 

![](screenshots/admin_home.png "Admin Panel Home")

More screenshots can be viewed from the [screenshots folder](https://github.com/waifung0207/ci_bootstrap_3/blob/master/screenshots/) under this repository.


### TODO

* Changelog file
* Better documentation (e.g. on [Gitbook](http://gitbook.com/))
* Enhance Form Builder library to support more field types
* Widget helper to include reusable views (e.g. for Admin Panel components)
* Example of using Image CRUD
* Database migration setup (consider using [Phinx](https://phinx.org/) instead of CodeIgniter built-in one)
* Custom 404 error page
* API authentication (by API key or JSON Web Token, i.e. JWT)
* More helpers to enhance code reusability
