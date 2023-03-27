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

    create .gitignore file  and add .env to it 
    

5. run docker image 

    ```
    export env_var2=Edwin
    docker run --env env_var1=Anjan -e env_var2 --env-file ./env env_greetings
    ```

