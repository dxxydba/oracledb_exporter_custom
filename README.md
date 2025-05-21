# oracledb_exporter_custom


i am assume oracle database already exist in my environment

1. build docker image with custom metric, in path /monitoring_oracledb_exporter/custom_oracledbexporter, with command : 
    docker build -t oracledb_exporter_custom .

2. running docker compose oracledb_exporter, /monitoring_oracledb_exporter/docker_compose/oracledb_exporter/, with command
    docker compose up -d

    if a successuflly, it is expose portal localhost:9161

3. prepare and running scrape prometheus, in path /monitoring_oracledb_exporter/docker_compose/prometheus_compose/, with command
     docker compose up -d

     if a succesfully, it is expose portal localhost:9090, and check prometheus already read scrape portal localhost:9161.

4. prepare and running grafana dashboard, in path /monitoring_oracledb_exporter/docker_compose/grafana_compose/, with command
     docker compose up -d

     if a succesfully, it is expose portal localhost:3000, then configure grafana dashboard Datasource and import Dashboard : 

     Datasource : 
     1. add new datasource
     2. choose prometheus
     3. fill in the field portal prometheuse, if same machine localhost:9090 and if different machine {iprometheus}:{port}
     4. save

     import dashboard.
     1. import dashboard 
     2. can be 2 choose, import .json or load ID grafana dashbaord, my custom metric .json, include montoring active dataguard apply.
     3. save

    note : you can edit custom-metric.toml with the query you want.



