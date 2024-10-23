# open-trip-planner2-docker

## create directory for data and config
```
mkdir data_map
```
## download OSM
```
curl -L https://download.geofabrik.de/europe/germany/berlin-latest.osm.pbf -o data_map/osm.pbf
```
## build graph and save it onto the host system via the volume
```
docker run --rm -v "$(pwd)/data_map:/var/opentripplanner" docker.io/opentripplanner/opentripplanner:latest --build --save 
```
## load and serve graph
```
docker run -it --rm -p 8080:8080 -v "$(pwd)/data_map:/var/opentripplanner" docker.io/opentripplanner/opentripplanner:latest --load --serve
```
