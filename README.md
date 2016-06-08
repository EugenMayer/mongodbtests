Different docker images to reproduce memory leaks or segmentation faults in php modules

+ imagick : reproduction of memory issue
+ mongo: reproduction of segmentation faults using the mongodb driver

All docker images have the debug symbols installed, including valgrind for debugging purposes

## Testing
### imagick
```
docker-compose up imagickwheezy
docker exec -i -t imagickwheezy bash
valgrind --leak-check=full /usr/bin/php -S localhost:8085
CM-c
```

### mongo
```
docker-compose up mongowheezy
docker exec -i -t mongowheezy bash
valgrind --leak-check=full /usr/bin/php -S localhost:8085
CM-c
```

same for jessie
