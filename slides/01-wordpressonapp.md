#Wordpress on App Engine

~~sub-section~~

##What you need?

- [PHP SDK](https://developers.google.com/appengine/downloads#Google_App_Engine_SDK_for_PHP)

- [MySQL Server](http://dev.mysql.com/downloads/)

- [Google Cloud Platfrom Account](http://cloud.google.com/console)

~~sub-section~~

##Setting up Google Cloud Platfrom Project

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
##On the Console go to your app and hit Compute

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
Getting into the Google Cloud Platfrom Site 

~~sub-section~~
## Downloading the Google App Engine PHP starter-project

~~sub-section~~

Download the starter project for Either Variants

1. Mac OSX
2. Windows
3. Linux

Visit  [googlecloudplatform.github.io/appengine-php-wordpress-starter-project](http://googlecloudplatform.github.io/appengine-php-wordpress-starter-project/)

~~sub-section~~

### Step 2: Edit the config files

~~sub-section~~

Edit `wp-config.php` and `app.yaml`, replacing `your-project-id`
to match the Project ID (not the name) that was assigned to your
Google Cloud Platform project.

~~sub-section~~

## Running WordPress locally

~~sub-section~~

Using MySQL, run `databasesetup.sql` to set up your local database. For a default installation (no root password)
this would be:

    mysql -u root < databasesetup.sql

But really, all it's doing is running this line -- the WordPress installation script will do the heavy lifting
when it comes to setting up your database.

    CREATE DATABASE IF NOT EXISTS wordpress_db;

To run WordPress locally on Windows and OS X, you can use the
[Launcher](https://developers.google.com/appengine/downloads#Google_App_Engine_SDK_for_PHP)
by going to **File > Add Existing Project** or you can run one of the commands below.

~~sub-section~~

On Mac and Windows, the default is to use the PHP binaries bundled with the SDK:

    $ APP_ENGINE_SDK_PATH/dev_appserver.py path_to_this_directory

On Linux, or to use your own PHP binaries, use:

    $ APP_ENGINE_SDK_PATH/dev_appserver.py --php_executable_path=PHP_CGI_EXECUTABLE_PATH path_to_this_directory

Now, with App Engine running locally, visit `http://localhost:8080/wp-admin/install.php` in your browser and run
the setup process, changing the port number from 8080 if you aren't using the default.
Or, to install directly from the local root URL, define `WP_SITEURL` in your `wp-config.php`, e.g.:

    define( 'WP_SITEURL', 'http://localhost:8080/');

You should be able to log in, and confirm that your app is ready to deploy.

~~sub-section~~

### Deploy!

~~sub-section~~

If all looks good, you can upload your application using the Launcher or by using this command:

    $ APP_ENGINE_SDK_PATH/appcfg.py update APPLICATION_DIRECTORY

Just like you had to do with the local database, you'll need to set up the Cloud SQL instance. The SDK includes
a tool for doing just that:

    google_sql.py <PROJECT_ID>:wordpress

This launches a browser window that authorizes the `google_sql.py` tool to connect to your Cloud SQL instance.
After clicking **Accept**, you can return to the command prompt, which has entered into the SQL command tool
and is now connected to your instance. Next to `sql>`, enter this command:

    CREATE DATABASE IF NOT EXISTS wordpress_db;

~~sub-section~~

You should see that it inserted 1 row of data creating the database. You can now type `exit` -- we're done here.

Now, just like you did when WordPress was running locally, you'll need to run the install script by visiting:

    http://<PROJECT_ID>.appspot.com/wp-admin/install.php

Or, to install directly from the root URL, you can define WP_SITEURL in your `wp-config.php`, e.g.:

    define( 'WP_SITEURL', 'http://<YOUR_PROJECT_ID>.appspot.com/');

~~sub-section~~


### Activating the plugins, configuring email, and hooking up WordPress to your Cloud Storage

~~sub-section~~

#### Activating the plugins

Now, we just need to activate the plugins that were packaged with your app. Log into the WordPress
administration section of your blog at `http://<PROJECT_ID>.appspot.com/wp-admin`, and visit the
Plugins section. Click the links to activate **Batcache Manager** and **Google App Engine for WordPress**.

#### Configuring email and hooking WordPress up to your Cloud Storage

Now visit **Settings > App Engine**. Enable the App Engine mail service - this will use the App Engine Mail
API to send notifications from WordPress. Optionally, enter a valid e-mail address that mail should be sent
from (if you leave this blank, the plugin will determine a default address to use). The address of the account
you used to the create the Cloud Console project should work.

Stay on this page, because in order to be able to embed images and other multimedia in your WordPress content,
you need to enter the name of the Cloud Storage bucket you created when going through all the Prequisites earlier
under **Upload Settings**.

Hit **Save Changes** to commit everything.

~~sub-section~~

## That's all! (PHEW)

~~sub-section~~

Congratulations! You should now have a blog that loads rapidly, caches elegantly,
sends email properly, and can support adding images and other media to blog posts! Most importantly,
it will take advantage of Google's incredibly powerful infrastructure and scale gracefully to
accomodate traffic that is hitting your blog.

~~sub-section~~

### Maintaining

~~sub-section~~

You'll want to keep your local copy of the application handy because that's how you install other plugins and update
the ones that are packaged with this project. Due to the tight security of the
App Engine sandbox, you can't directly write to files in the application area -- they're static. That's
also why we hooked your uploads up to Cloud Storage. So, to install plugins, you log into the admin area
of your local WordPress instance, install or update any plugins you want there, and
redeploy. Then go into the admin area for your hosted WordPress instance to activate the plugins.

