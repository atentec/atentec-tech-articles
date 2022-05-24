# Jaspersoft Report Configuration
- Author: `Eman Elkafrawy`
- Email: eman@atentec.com

This document describes steps required to configure an environment for Jaspersoft as a containerized service.

## Setup jasper reports ENV.
1. Install jasper reports server on ur OS
2. Install jasper soft studio on ur OS
3. Start jasper report server and login 
    - (URL) => http://localhost:8080/jasper
    - (auth) => {username: jasperadmin, password: jasperadmin}

## Dockerize jasper server reports
- (install docker)
- (install composer)
- (create empty project)=> using this command line to download docker-compose.yml from MARIADB github
```
curl -sSL https://raw.githubusercontent.com/bitnami/bitnami-docker-jasperreports/master/docker-compose.yml > docker-compose.yml
```

- open docker-compose.yml
- change portnumber to -> 8080 (jasper server port) and set a new port you need to run docker 
- add
```
JASPERREPORTS_USERNAME=jasperadmin
JASPERREPORTS_PASSWORD=jasperadmin
```
to access jasper report auth
```
docker-compose up -d
```

- run jasper server again with new port(container port)
```
http://localhost:POSTNUMBER/jasperserver
```

## to make a report 

1. run jasper studio
2. create new data adapter to set your json file or you API-> DataAdapter.xml 
3. create new report.jrxml (template and add data set to that template DataAdapter.xml) 
4. design your template with fields
5. add to report.xml link of your jasper server to store report on the server -> net.sf.jasperreports.data.adapter and value DataAdapter.xml
6. now you an acess your reports 