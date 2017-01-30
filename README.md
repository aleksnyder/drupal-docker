# Very Simple Drupal Docker Container
This is a very simple Docker Container for Drupal sites.  

##Features
Very Simple Drupal Docker Container contains separate containers for nginx, PHP 7, MySQL, PHPmyAdmin, Composer, and Drush.  There is a working volume mounted in `/www/html` where you can add, edit, and delete files.  When a change is made to the `www/html` folder on your local machine, it will automatically update the `var/www/html` folder inside the Docker Container.  Additionally, any database tables added to the MySQL container will stay in the `/data` folder as persistent data even after you shutdown the docker container.

If you'd like to change the local directory used for the Docker volume, edit the PROJECT_ROOT variable in the `.env` file.  Same goes for the database username, password(s), and name listed in the same file.  Any additional variables added to the file will need to be updated in the `docker-compose.yml` file.

##Sample Commands
Composer and Drush are setup to run outside the mounted directory without having to access Bash.  This allows for easier setup since you don't have to be inside the local server to run commands.

**Run Composer Install**
```
docker-compose run composer install
```
Same syntax can be used for composer commands such as update and remove.  Just replace install with your desired command.

**Download latest Drupal release to the /www/html folder**
```
docker-compose run drush dl drupal --drupal-project-rename="mysite"
```
The above command install the latest Drupal 8 release in the `/www/html` and `/var/www/html` folder.  Similar to the Composer command, you can run any drush command using the above syntax.  Remember to prefix the command with `docker-compose run`.