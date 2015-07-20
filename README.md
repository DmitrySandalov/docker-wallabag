### Image from Docker Registry

1. Put the sample Database to write-accessible folder for `www-data` Docker user

        mkdir /home/user/wallabag-db/
        wget -O /home/user/wallabag-db/poche.sqlite https://github.com/DmitrySandalov/docker-wallabag/raw/master/conf/poche.sqlite 
        chmod -R 777 /home/user/wallabag-db/

2. Run image

        docker run -d -p 8080:80 -v /home/user/wallabag-db/:/var/www/html/db/ dmitrysandalov/docker-wallabag

### Self-made Docker image

1. Build image from this repo

        git clone https://github.com/DmitrySandalov/docker-wallabag.git
        cd docker-wallabag
        docker build -t wallabag .

2. Put the sample Database to folder write-accessible for `www-data` Docker user

        mkdir /home/user/wallabag-db/
        wget -O /home/user/wallabag-db/poche.sqlite https://github.com/DmitrySandalov/docker-wallabag/raw/master/conf/poche.sqlite 
        chmod -R 777 /home/user/wallabag-db/

3. Start Wallabag:

        docker run -d -p 8080:80 -v /home/user/wallabag-db/:/var/www/html/db/ wallabag

### Notes

* Note 1. To access Wallabag use the following link (`user: poche`, `pass: poche`)

        http://localhost:8080/

* Note 2. Optional: change Salt in `Dockerfile` to some other long string and regenerate initial `poche.sqlite`

        sed -i "s/('SALT', '')/('SALT', '"`< /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c32;`"')/" /var/www/html/inc/poche/config.inc.php

https://www.wallabag.org/
