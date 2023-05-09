# Config Symfony 6 + Mysql (Enviroment Docker)
Tested in W11 PRO (24/04/2023). 

# Steps to enjoy this setup

## INSTALLATION (FIRST TIME)

1. Create new directory in your PC, virtualmachine...
2. Open new console (cmd, powershell...) and navigate to your directory. 
3. Download this repository

``` git clone https://github.com/ilguirao/symfony-6-docker.git . ```

4. Configure your data for Git
    - In file **/docker/php/Dockerfile** replace:
        - "name@mail.com" to your "e-mail"
        - "Your Name" to your "Name"

5. Configure vars into .env.example and rename to .env

6. Download and install Docker (https://www.docker.com)

7. Create Docker Container 

``` docker-compose up -d --build ```

8. Execute bash -> Replace (php_docker_container_name) with php container name. Remember "docker ps"

``` docker exec -it (php_docker_container_name) bash ```

9. Create new Symfony Project

    - If you want a new web project you can execute:

    ``` symfony new --webapp my_project ```

    - If you want a new app project you can execute:

    ``` symfony new my_project ```

### All ready for enjoy your new project! If you want, you can close this console session.

## WORKING WITH YOUR PROJECT ()

1. Open new console (cmd, powershell...) and navigate to your directory.
2. Run Docker

``` docker-compose up -d ```

3. Execute bash

``` docker exec -it test-docker-php-1 bash ```

4. Execute serve to view your symfony project at your navigator

``` symfony serve ```

5. Click or navigate to 

``` http://localhost:8000 ```

**TIP:** When you need execute new commands for create tables (doctrine) or others, you can open a new cmd console to do it or close "symfony serve" with ctrl + C.

### Enjoy and learn with symfony 6.

# Vars to configure (if you want, doesn't needed)

- File **docker-compose.yaml**
    - **MYSQL SECTION:**
    - You can change default directory name on your save your db files: ./db/

    .***/db***:/var/lib/mysql

    - **PHP SECTION:**
    - You can change default directory name on your save your symfony project files: ./www/
    
    .***/www***:/var/www

## License
[MIT](https://choosealicense.com/licenses/mit/)
