#Wordpress on App Engine
~~sub-section~~

## Wordpress
![](./img/wordpress.png)

~~sub-section~~

1. Free and Open Source CMS based on PHP and MySQL

2. Its magic lies is seen with its plugin architecture and template system.

3. As of January 2015 , 23.3% of the top 10 Million websites were Wordpress based.

~~sub-section~~

## Ok . Why delpoy it on  Google App Engine?

~~sub-section~~

 GAE is Google Cloud Platform's PaaS

1. Run on Google Infrastructure
2. Automatic Scaling 
3. No need to worry about System Admin tasks.
4. Ease with intergrating other Google Cloud Platform services.

~~sub-section~~

## This is what we will be  building today

[gdgnairobigae.appspot.com](http://gdgnairobigae.appspot.com)

![](./img/finalproj.png)
~~sub-section~~

## To launch we will cover the following
1. Requirements
2. Setting up Google Cloud Platform Project
3. Editing Config Files
4. Running it Locally
5. Deploying it on production
6. Tips and Tricks 

~~sub-section~~
##What you need?

- [PHP SDK](https://developers.google.com/appengine/downloads#Google_App_Engine_SDK_for_PHP)

- [MySQL Server](http://dev.mysql.com/downloads/)

- [Google Cloud Platfrom Account](http://cloud.google.com/console)

~~sub-section~~

##Setting up a Google Cloud Platfrom Project

~~sub-section~~

## Go to the console

![](./img/01.png)

~~sub-section~~

## Create a new project once in the console

![](./img/02.png)

~~sub-section~~
## Status of new project that has been created
![](./img/03.png)

~~sub-section~~
## Download the GAE SDK 

![](./img/04.png)

~~sub-section~~
### We will perform the following in the next steps

1. Creating a Google Cloud Storage Bucket
2. Creating a Google Cloud SQL Instance
3. Downloading the Wordpress on Google App Engine Starter kit

~~sub-section~~
## Hit Compute Option

![](./img/05.png)
~~sub-section~~
## Create a Google Cloud Storage Bucket

![](./img/06.png)
~~sub-section~~

## Create a bucket name
![](./img/07.png)

~~sub-section~~
## Create a  Cloud SQL instance

![](./img/08.png)

~~sub-section~~
## Create a Cloud SQL instance (..cont)

![](./img/09.png)
~~sub-section~~
##Created Cloud SQL instance

![](./img/10.png)

~~sub-section~~
## Downloading the Google App Engine PHP starter-project

![](./img/11.png)

~~sub-section~~

## Move to the directory with your Google App Engine files

![](./img/16.png)

~~sub-section~~

## Edit the config files

~~sub-section~~

## Edit wp-config.php

![](./img/12.png)

~~sub-section~~

![](./img/13.png)
~~sub-section~~

## Edit app.yaml
![](./img/14.png)

~~sub-section~~

![](./img/15.png)

~~sub-section~~
## Running WordPress locally

~~sub-section~~

##  Load the database
![](./img/17.png)

~~sub-section~~

On Mac and Windows, the default is to use the PHP binaries bundled with the SDK and you just need the launcher

![](./img/18.png)

~~sub-section~~
On Linux, or to use your own PHP binaries, use:

    $ APP_ENGINE_SDK_PATH/dev_appserver.py --php_executable_path=PHP_CGI_EXECUTABLE_PATH path_to_this_directory

Now, with App Engine running locally, visit `http://localhost:8080/wp-admin/install.php` in your browser and run
the setup process, changing the port number from 8080 if you aren't using the default.

~~sub-section~~

### Deploy!

~~sub-section~~

![](./img/19.png)

~~sub-section~~
Just like you had to do with the local database, you'll need to set up the Cloud SQL instance. The SDK includes
a tool for doing just that:

![](./img/20.png)

~~sub-section~~
Accept Cloud SQL to manage your services

![](./img/21.png)
~~sub-section~~
## Create Database

![](./img/17.png)

~~sub-section~~

Now, just like you did when WordPress was running locally, you'll need to run the install script by visiting:

    http://<PROJECT_ID>.appspot.com/wp-admin/install.php

~~sub-section~~
## Go to the Admin and Login
![](./img/24.png)

~~sub-section~~
### Activating the plugins, configuring email, and hookng up WordPress to your Cloud Storage Bucket

~~sub-section~~

#### Activating the plugins

![](./img/22.png)

~~sub-section~~

#### Configuring email and hooking WordPress up to your Cloud Storage

![](./img/23.png)

~~sub-section~~

## That's all! (PHEW)

~~sub-section~~

## Congratulations 

![](./img/finalproj.png)

~~sub-section~~

### Maintaining Tips

1. Maintain a local version of the app to maintain themes and plugins.
2. To update a theme or plugin install it locally and redeploy
3. Remember you can't upload on Google App Engine's files system.


