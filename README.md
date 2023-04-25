# Config Symfony 6 + Mysql (Enviroment Docker)
Tested in W11 PRO (24/04/2023). 

# Steps to enjoy this setup

## INSTALLATION (FIRST TIME)

1. Create new directory in your PC, virtualmachine...
2. Open new console (cmd, powershell...) and navigate to your directory. 
3. Download this repository

``` git clone https://github.com/ilguirao/docker-symfony-6.git . ```

4. Configure your data for Git
    - In file **/docker/php/Dockerfile** replace:
        - "name@mail.com" to your "e-mail"
        - "Your Name" to your "Name"

5. Download and install Docker (https://www.docker.com)

6. Create Docker Container 

``` docker-compose up -d --build ```

7. Execute bash

``` docker exec -it test-docker-php-1 bash ```

8. Create new Symfony Project

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
    - ***MYSQL_ROOT_PASSWORD:*** Password to access db
    - ***MYSQL_DATABASE:*** Name for your default db
    - You can change default directory name on your save your db files: ./db/

    .***/db***:/var/lib/mysql

    - **PHP SECTION:**
    - You can change default directory name on your save your symfony project files: ./www/
    
    .***/www***:/var/www

    
    - **ADMIN FOR DB:** 
    I choose the recommended in official image of mysql, but you can change Adminer to phpMyAdmin or others. Only need replace this code for other:
    ```
    adminer:
        image: adminer
        restart: always
        ports:
            - 8080:8080 
    ```

## License
[MIT](https://choosealicense.com/licenses/mit/)