Instructions to run the project

# Clone the project with recursive flag to clone the submodules

git clone git@github.com:romulo-iorio/cosmobots-test-blog.git --recursive-submodules

# Go to the project directory

cd cosmobots-test-blog

# Run the project once, but comment the line 27 and uncomment the line 26 on docker-compose.yml file, to run the project without the api

docker-compose up

# On a terminal window, go inside the api container

docker exec -it cosmobots-api bash

# Run the following commands to create credentials file

rm -rf config/credentials.yml.enc && rm -rf config/master.key && EDITOR="nano" bin/rails credentials:edit

# Add the following content to the credentials file

devise_jwt_secret_key: C0sM0b0t5_53Cr3t (this is an example secret, you can use any secret you want)

# Save the file and exit the editor

# Run the following commands to create the database and run the migrations

bin/rails db:migrate

# Run the following command to test the api

bin/rails server -b 0.0.0.0

# If it is working, you can stop the server and exit the container, also stop the containers running

# Now run the project again, but comment the line 26 and uncomment the line 27 on docker-compose.yml file, to run the project completely
