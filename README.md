# docker


```bash
version: '3'

services:
  postgres-db:
    image: 'postgres:11'
    ports:
    - 15432:5432
    environment:
    - POSTGRES_DB=admin
    - POSTGRES_USER=admin
    - POSTGRES_POST=5432
    - POSTGRES_PASSWORD=admin
    volumes:
      - ./files/migrations:/docker-entrypoint-initdb.d

  pgadmin:
    image: 'dpage/pgadmin4'
    ports:
    - 5480:80
    environment:
    - PGADMIN_DEFAULT_EMAIL=admin@codetick.com
    - PGADMIN_DEFAULT_PASSWORD=admin
    - POSTGRES_DB=admin
    - POSTGRES_USER=admin
    - POSTGRES_PASSWORD=admin
    depends_on:
      - postgres-db
```
