# Configuration of Amazon RDS in Phpmyadmin

### Follow the steps along to list below to get the work done

![db](https://github.com/Sahilbhawke/argoproject/blob/17d175f839efa7bb23ffba2b28000d65d240a5b2/db.png?raw=true)

## Table of Content

- [Understanding phpmyAdmin](https://github.com/Sahilbhawke/argoproject#understanding-phpmyadmin)

- [Download phpmyadmin and Configure for RDS](https://github.com/Sahilbhawke/argoproject#installation)
   
  * [Installation of phpMyAdmin](https://github.com/Sahilbhawke/argoproject#installation)
    
  * [Configuration for RDS](https://github.com/Sahilbhawke/argoproject#configuration-for-rds)

-  [Navigate to the browser and test](https://github.com/Sahilbhawke/argoproject#access-phpmyadmin-from-your-local-browser)
  

  ## Understanding PHPMyAdmin
##### PhpMyAdmin is a free software tool written in PHP, intended to handle the administration of MySQL over the Web. phpMyAdmin supports a wide range of operations on MySQL and MariaDB.

## Installation

- You need to go to the root Directory of the project. Like my project is in /var/www/html/.
  
  `cd /var/www/html/`

-  Now Download the phpMyAdmin from an authorized website using wget command.

    `wget https://files.phpmyadmin.net/phpMyAdmin/4.7.3/phpMyAdmin-4.7.3-all-languages.zip`

-  Unzip phpMyAdmin.
   
   `unzip phpMyAdmin-4.7.3-all-languages.zip`
   
-  Now rename phpMyAdmin and go to phpMyAdmin Directory.

   `mv phpMyAdmin-4.7.3-all-languages phpmyadmin` 

-  And go into the renamed Directory.

   `cd phpmyadmin`

## Configuration for RDS

-  Here we need to Rename and Edit the configuration file for phpMyAdmin, use these following commands.

   `mv config.sample.inc.php config.inc.php`
    
    `vim config.inc.php`

- As Amazon RDS, you need to add the following lines after the block of localhost config.

  ```bash
   $i++;
   $cfg['Servers'][$i]['host'] = 'xxxxxxxxxxxx.ap-northeast-1.rds.amazonaws.com';
   $cfg['Servers'][$i]['port'] = '3306';
   $cfg['Servers'][$i]['socket'] = '';
   $cfg['Servers'][$i]['connect_type'] = 'tcp';
   $cfg['Servers'][$i]['extension'] = 'mysqli';
   $cfg['Servers'][$i]['auth_type'] = 'cookie';
  ``` 
- Save file and Close.

- You can get 'RDS MYSQL ENDPOINT' from AWS RDS console.
 
 ![image](https://github.com/Sahilbhawke/argoproject/blob/17d175f839efa7bb23ffba2b28000d65d240a5b2/image%20(1).png?raw=true)

- Restart Apache service.

  `sudo systemctl restart apache2.service`

 ### NOTE: Also check your RDS inbound port 3306 is Open in RDS Security group for access MySQL to phpMyAdmin.

## Access PhpMyAdmin from your local browser.

- Enter `http://SERVER_IP/phpMyAdmin` enter username and password of your RDS. and access it.

- Now you can access phpMyAdmin and choose your host.

 ![image](https://github.com/Sahilbhawke/argoproject/blob/17d175f839efa7bb23ffba2b28000d65d240a5b2/image.png?raw=true)
  
## Authors

- [Bitcot](https://www.bitcot.com/)

![Logo](https://ca.slack-edge.com/T038JGHAM-U10U9592T-7448ec25ea73-54)

## Documentation

[How to configure amazon rds in phpmyadmin.](https://docs.google.com/document/d/1KF7EPu5LpfZ0Pi8buJxOOu_SX8d9DIqHSMS4Kmxsxmo/edit?usp=sharing)

  
## Appendix

#### March 26, 2021 by Vijay Yadav 
