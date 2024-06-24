# Instructions to run the project:

1. Clone the project with recursive flag to clone the submodules

```bash
git clone --recursive git@github.com:romulo-iorio/cosmobots-test-blog.git
```

2. Go to the project directory

```bash
cd cosmobots-test-blog
```

3. Run the project once, but comment the line 27 and uncomment the line 26 on docker-compose.yml file, to run the project without the api

```bash
docker-compose up
```

4. On a terminal window, go inside the api container

```bash
docker exec -it cosmobots-api bash
```

5. Run the following commands to create credentials file

```bash
rm -rf config/credentials.yml.enc && rm -rf config/master.key && EDITOR="nano" bin/rails credentials:edit
```

6. Add the following content to the credentials file

```
devise_jwt_secret_key: C0sM0b0t5_53Cr3t (this is an example secret, you can use any secret you want)
```

7. Save the file and exit the editor

8. Run the following commands to create the database and run the migrations

```bash
bin/rails db:migrate
```

9. Run the following command to test the api

```bash
bin/rails server -b 0.0.0.0
```

10. If it is working, you can stop the server and exit the container, also stop the containers running

11. Now run the project again, but comment the line 26 and uncomment the line 27 on docker-compose.yml file, to run the project completely
