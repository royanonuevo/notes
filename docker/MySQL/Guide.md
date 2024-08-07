# Run MySQL/Workbench in Local Machine

1. Copy the `docker-compose.yml` and modify the environment variables if needed
2. run the command: `docker compose up`
3. Open `MySQL Workbench` app
4. Create a new connection
    - Connection Name: `a name you want`
    - Username: `root`
    - Password: `<root password`
    - Port: `3306`



## If no `Docker Compose` file, you can run this command:
```bash
docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -p 3306:3306 -d mysql
```