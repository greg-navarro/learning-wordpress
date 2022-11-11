In setting up my development environment, I have attempted to select the easiest path in order to get to the important stuff... learning wordpress developement so I can be capable of fixing that damn website (and others as well).

To this end we are using MAMP for our Apache server, but since the mysql situation on my computer does not appear to be working very well, we need another database.

The next solution that seems teneable is using a docker image for mysql.

NOT USING THIS Command to start container: docker run --name wordpress-mysql -it --rm -d -e MYSQL_ROOT_PASSWORD=root

NOT USING THIS $ docker run --name mysql-test -e MYSQL_ROOT_PASSWORD=root -d mysql:tag



Wordpress set-up credentials
Database, using a mysql docker image:
    docker-compose env name: learning-wordpress (appears to use directory command 'docker-compose up' was issued from)
	docker image name: learning-wordpress_db_1
	docker volume name: learning-wordpress_wordpress_db
	database name: wordpress
	database user: wordpress
    database user password: wordpress
    root user: root
	root password: root 


So, fun update!!!

Apparently to access the mysql container from a port on the host port forwarding needs to be set up. So I think that makes this a significantly less desirable option.

Instead, I've managed to get mysql running on my Mac.  While the settings menu seemingly isn't working I was able to start the mysql server by directly invoking the program with the 'start' command.

https://stackoverflow.com/questions/41995912/macos-cant-start-mysql-server

Anyways, the server is working and I was able to reinitialize the database from the settings menu and set up a new root user.

Now the challenge is to set up wordpress database and user. The database was easy enough to create, but I am getting errors when trying to create the user and grant privileges to the database.

CREATE USER 'wordpress'@'%' IDENTIFIED BY 'wordpress';
GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpress'@'%';
FLUSH PRIVILEGES;

Note that database name, user, and password are all the same here.

Lol, I was trying to issue the command 'CREATE NEW USER' instead of 'CREATE USER'.