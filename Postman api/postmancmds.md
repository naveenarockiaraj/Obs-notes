[[postmancmds]]
- `cd ${COMPOSE_DIR}` >>>>> to stop the terminal
- `mkdir -p postman/collections postman/reports`
- cp ${WORKSPACE}/src/apitest/sanity/postman/* postman/collections/>>>>>>>>>have alternating code
- `cp /c/Users/nraj/workspace/otarepo/src/apitest/sanity/postman/* postman/collections/`
- fig kill postman>>>kill postman
- fig rm -f postman>>>remove postrman
- docker-compose --profile sanity ${COMPOSE_OPTIONS} up -d postman>>>>>>>have alternating code
- `docker-compose --profile sanity -f docker-compose.yml -f apitest.override.yml up -d postman`

echo $?
docker compose logs -f postman>>>>>>>to check the log 

**For API testing,**

IF needed
**to clear all data in ota**
fig down -v 
docker-compose up -d keycloak 
docker-compose up -d keycloak-disable-https 
docker-compose restart keycloak 
docker-compose up -d

**Before starting testing**
fig down; fig rm -f; fig up -d
cd workspace/otarepo/src/apitest
git pull>>>>>>>pull the latest code
And have to import the data to the postman.

**For generate the Html Report**
cd ${COMPOSE_DIR}>>>>>if it needed
otherwise enter these code in composed terminal.
mkdir -p postman/collections postman/reports
cp ${WORKSPACE}/src/apitest/sanity/postman/* postman/collections/
docker-compose --profile sanity ${COMPOSE_OPTIONS} up -d postman>>>>>if it didn't work go for the next line code
docker-compose --profile sanity -f docker-compose.yml -f apitest.override.yml up -d postman

**exitcode checking**(
postman_container_id=$(docker-compose --profile sanity ${COMPOSE_OPTIONS} ps -a -q postman)
alternate code
postman_container_id=$(docker-compose --profile sanity -f docker-compose.yml -f apitest.override.yml ps -a -q postman)
exit_code=$(docker inspect $postman_container_id --format='{{.State.ExitCode}}'))

if we use a "***postman_container_id=$(docker-compose --profile sanity -f docker-compose.yml -f apitest.override.yml ps -a -q postman***)*" symbol as a variable it will store the data to the given name and we have to check the variable out put using these command "***echo $postman_container_id***"

**newman local run**(for Html report in local)
this should be run in -apitest/sanity/postman/ terminal(not in compose)
``npm install -g newman-reporter-html && newman run ota-sanity.postman_collection.json --insecure --environment=ota-sanity.postman_environment.json --reporters=cli,junit,html --reporter-junit-export=/c/Users/nraj/workspace/otarepo/src/apitest/sanity/postman/postman/reports/ota-sanity-report.xml --reporter-html-export=/c/Users/nraj/workspace/otarepo/src/apitest/sanity/postman/postman/reports/ota-sanity-report.html``

# for log file
`npm install -g newman-reporter-html && newman run ota-sanity.postman_collection.json --insecure --environment=ota-sanity.postman_environment.json --reporters=cli,junit,html --reporter-junit-export=/c/Users/nraj/workspace/otarepo/src/apitest/sanity/postman/postman/reports/ota-sanity-report.xml --reporter-html-export=/c/Users/nraj/workspace/otarepo/src/apitest/sanity/postman/postman/reports/ota-sanity-report.html > /c/Users/nraj/workspace/otarepo/src/apitest/sanity/postman/postman/reports/ota-sanity-log.txt 2>&1`

cat ota-sanity-report.html
fig rm -f postman
fig kill postman
rm -rf postman