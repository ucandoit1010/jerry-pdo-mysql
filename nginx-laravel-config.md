#  NGINX for Laravel
ref :
https://gist.github.com/tsolar/8d45ed05bcff8eb75404#gistcomment-2299798

## sub_directory

  ```  
  location ^~ /sub_directory {  
      alias /var/www/choppies/sub_directory/public;  
      try_files $uri $uri/ @sub_directory;  
      location ~ \.php {  
          include snippets/fastcgi-php.conf;
          fastcgi_pass unix:/run/php/php7.0-fpm.sock; 
          fastcgi_param SCRIPT_FILENAME /var/www/choppies/sub_directory/public/index.php;
      }  
  }  

  location @sub_directory {
      rewrite /sub_directory/(.*)$ /sub_directory/index.php?/$1 last;  
  }  
```
