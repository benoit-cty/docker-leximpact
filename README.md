
## WARNING : This is a work in progress that doesn't work yet.

# Docker files for LexImpact

This repository is a quick setup of LexImpact using Docker Compose.

Just run :
```
docker-compose up
```

And go to http://localhost:9001 to use LexImpact locally.

Images used :
 - Alpine Node 12
 - Python 3.7
 - PostgreSQL:latest

The database is saved in a docker volume named *postgres_leximpact_data*