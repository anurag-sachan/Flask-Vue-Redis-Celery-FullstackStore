# Fullstack-Flask-Vue-Redis-Celery-Project

## How to Run

- Clone the repository.
  
  ```shell
  git clone https://github.com/anurag-sachan/Flask-Vue-Redis-Celery-FullstackStore.git
  ```

- Spin the docker container for redis-instance and update the configurations [**here**](app.py).
  
    > If you are unsure about the redis setup, you can always use docker. It's extremely simple. <br/>
    > Go to base folder. Run the command below :

    ```shell
    # This will create a redis container named `my-redis-container`
    
    docker run --rm --name my-redis-container -p 6379:6379 -d redis
    ```

    > To check if the instance is running properly
    > 1. redis-cli ping
    > 2. redis-cli -d 0
    > 3. keys *

- Setup the Celery workers (for tasks) & beat (for schedule jobs)
  ```shell
  celery -A app.celery_app worker --loglevel=info
  ```

  ```shell
  celery -A app.celery_app beat --loglevel=info
  ```
    
- Run the Backend:
  > If database.db is not present

  ```shell
  run python3 DB.py
  ```
  ```shell
  run python3 app.py
  ```
  
  > If database.db is already present
  ```shell
  run python3 app.py
  ```

- [Optional]: If you want to insert dummy data into the postgres db run the below command from your terminal:

  ```shell
  cp dummy-data.csv pgdata
  ```
  ```shell
  docker exec -it mydb psql -h 127.0.0.1 -d productdb -p 5432 -U anurag
  ```
  ```shell
  \copy product FROM '/var/lib/postgresql/data/dummy-data.csv' DELIMITER '$' CSV HEADER;
  ```

- Run the frontend:

  cd frontend/

  ```shell
  # to install required node_module files

  npm install
  ```

  ```shell
  npm run dev
  ```

## Screenshots
- Please refer to the working demo-images from [**here**](demo-jpg).

<br/>
Thanks,

Anurag.