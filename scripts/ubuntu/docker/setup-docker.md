# Setup Docker

1. Create a file named `<script_name>.sh` in your server.
    Use below command to create file:

    ```bash
    nano `setup-docker.sh`
    ```

2. Copy the contents of [setup-docker.sh](./setup-docker.sh) into your `setup-docker.sh` file in your server.
    - Press Control `X` and `Y` and then Press `Enter`

3. You can confirm the content using this command:
    ```bash
    cat setup-docker.sh
    ```
4. When everything is right, run the sh file
    ```bash
    sh setup-docker.sh
    ```

5. 
    ```bash
    sudo usermod -a -G docker root
    ```

**when you got error about docker connect:**
https://medium.com/@praveenadoni4456/error-got-permission-denied-while-trying-to-connect-to-the-docker-daemon-socket-at-e68bfab8146a



## For deployment scripts

1. [deploy-aws-ecr.sh](./deploy-aws-ecr.sh)
2. [deploy-docker-hub.sh](./deploy-docker-hub.sh)
