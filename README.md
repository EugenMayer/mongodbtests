Different docker images to reproduce memory leaks or segmentation faults in php modules

+ imagick : reproduction of segfault : https://github.com/mkoppanen/imagick/issues/156
+ mongo: reproduction of segmentation faults using the mongodb driver: https://github.com/mongodb/mongo-php-driver/issues/209

All docker images have the debug symbols installed, including valgrind for debugging purposes

## Testing
### imagick extension
Issue: https://github.com/mkoppanen/imagick/issues/156
```
docker-compose up imagickwheezy
docker exec -i -t imagickwheezy bash
valgrind --leak-check=full /usr/bin/php -S localhost:8085
CM-c
```

same for jessie

```
docker-compose up imagickjessie
docker exec -i -t imagickjessie bash
valgrind --leak-check=full /usr/bin/php -S localhost:8085
CM-c
```

### mongodb extension
Issue: https://github.com/mongodb/mongo-php-driver/issues/209#issuecomment-224675831
```
docker-compose up mongowheezy
docker exec -i -t mongowheezy bash
valgrind --leak-check=full /usr/bin/php -S localhost:8085
CM-c
```

same for jessie

```
docker-compose up mongojessie
docker exec -i -t mongojessie bash
valgrind --leak-check=full /usr/bin/php -S localhost:8085
CM-c
```

