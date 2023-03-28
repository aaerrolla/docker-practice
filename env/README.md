# Demo of how to use env variables in docker

This example demonstrates how to work with environmental variables , mainly how to pass env var values to docker container.

1. create a simpe shell script file named greetings.sh

    ```
    #!/usr/bin/env sh

    echo Hello $env_var1 $env_var2 $env_sec_var1 $env_sec_var2 
    ```
2. create Dockerfile 
    ```
    FROM alpine:latest
    COPY greetings.sh .
    RUN chmod +x /greetings.sh
    CMD ["/greetings.sh"]
    ```

3. build the docker image 

    ```
    docker build -t env_greetings .

    ```
4. create .env file with below entries 

    ```
    env_sec_var1=VerySecretKey
    env_sec_var2=VerySecretValue
    ```
    Very Important 

    if your .env contains secrets like passwords or keys, then create .gitignore file  and add .env to it so it will not be comitted to git repo. 
    

5. run docker image 

    ```
    export env_var2=Edwin
    docker run --env env_var1=Anjan -e env_var2 --env-file ./env env_greetings
    ```

