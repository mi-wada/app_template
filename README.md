1. docker compose build
2. docker compose run --rm api rails new . --force --no-deps --database=postgresql --api
3. docker compose run --rm front sh -c "cd .. && rm -rf app && create-react-app app"
4. replace 'api/config/database.yml' to
   ```
   default: &default
      adapter: postgresql
      encoding: unicode
      host: db
      username: postgres
      password: password
      pool: 5
   ```
5. docker compose run api rake db:create
