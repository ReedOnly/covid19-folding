# Covid-19 Folding
This wil run folding at home on the Radix platfor by toing protein folding to contribute to the COVID-19 pandemic

### Docker compose: 
```
docker-compose up --build
```
### Docker: 
```
docker build --rm -f "foldingathome/Dockerfile" -t covid19folding:latest "foldingathome"
docker run --rm -it  -p 36331:36330/tcp -p 8080:7396/tcp covid19folding:latest
```

Both docker-compose and docker will serve the Web control page at `localhost:8080`

## Team score:
https://stats.foldingathome.org/team/254927


## Radix:
- https://console.playground.radix.equinor.com/applications/covid-19-folding

- https://node1-covid-19-folding-dev.playground.radix.equinor.com/
- https://node2-covid-19-folding-dev.playground.radix.equinor.com/
