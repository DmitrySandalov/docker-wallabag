1. Clone this repo

        git clone https://github.com/DmitrySandalov/docker-wallabag.git
        cd docker-wallabag

2. Change Salt in `Dockerfile` to some other long string

        RUN sed -i "s/('SALT', '')/('SALT', '160e9a2cc5f769c80ddee79950faf5f6')/" ...

3. Build image:

        docker build -t wallabag .

4. Prepare local Wallabag storage (`poche.sqlite` is from this repo)

        mkdir /home/user/wallabag-db/
        cp conf/poche.sqlite /home/user/wallabag-db/
        chmod -R 777 /home/user/wallabag-db/

5. Start Wallabag:

        docker run -d -p 8080:80 -v /home/user/wallabag-db/:/var/www/html/db/ wallabag

6. Go to Wallabag (`user: poche`, `pass: poche`)

        http://localhost:8080/

https://www.wallabag.org/
