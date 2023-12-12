## Clone this project
1. Test the project locally.
 `[https://github.com/Yadnyawallya/Angular-project.git]`

 ## Initialise and start the project
  - npm install.
  - npm run start.

## Download Winsp

- https://winscp.net/eng/download.php.
- Download and install the Wincp .
- Add the Dist file. (angular Bulid File into the right hand section.)

## Set up an AWS EC2 instance
- 1.Create an IAM user & login to your AWS Console.
    Access Type - Password
    Permissions - Admin
- 2.Create an EC2 instance.
   Select an OS image - Ubuntu
- 3.Create a new key pair & download .pem file.
   Instance type - t2.micro

## Connecting to the instance using ssh
ssh -i instance.pem ubunutu@<IP_ADDRESS>
 ## Configuring Ubuntu on remote VM
- Updating the outdated packages and dependencies
       sudo apt update
- Install Nginx - sudo apt install nginx
      sudo systemctl status nginx or sudo service nginx.
       sudo systemctl start nginx

## Deploying the project on AWS
- 1. Create The new Directory on server.
     `sudo mkdir /path/of /new/directory/`
- 2. Copy the path source of the directory.
     `/home/ec2-user/dist/project  ---path source`
- 3. open the new directory 
     `/data/nginx -- destination`
- 4.  copy the source code into destionation
  * ` sudo cp -R`     ----source destination.
  *  `sudo cp -R /home/ec2-user/dist/project /data/nginx.`
- 5. now path wiil be
 `/data/nginx/project`   ---webroot

## nginx  configuration setting

-  Change the Directory.
      `cd /etc/nginx`
 -  Hit the `ls` command
   -- `go to conf.d`
   -- `cd conf.d`
 -  Create the new file using VIM command
       * `sudo vim ang-test-01.conf`
 -   Add the Server configuration file.

 #### Server Configuration
     // Configuration syntex file
      `server {
	       listen 80;
	       server_name example.com;
	           root /var/www/html;
	             index index.html;
	  location /
       {
	       try_files $uri $uri / /index.html;
	     }
     }`
-  Check the Cofiguration details on My Project do exact same as shown in Example.

 #### Server Configuration
       // Check the Configuration Syntex.
             `server {
	                    listen 80;
	                    server_name 3.111.217.205;  // your ec2 instance public IP address
	                     root /data/nginx/project;   //folder path wich copy 
	                      index index.html;
	           location / {
	               try_files $uri $uri / /index.html;
	            }
     }`
   
-  Exit from vim file using below command
    - press esc button then shift + colon. 
    - press wq! or x.
      
 ## Restart the Nginx
  Use Below command
-  sudo nginx -t

-  sudo systemctl status nginx or sudo service nginx.
  
-  sudo systemctl start nginx.

  ##### NOTE: We will have to edit the inbound rules in the security group of our EC2, in order to allow traffic from our particular port.

#### Project Deployed On AWS.

//
# ProjectNginxWeb

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 12.2.18.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.
