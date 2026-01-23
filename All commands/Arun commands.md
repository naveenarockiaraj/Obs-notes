GIT COMMENDS:
		git clone git@bitbucket.org:pythonprojects1/scraping.git

		git status

		git add . ========> full file add aagum

		git add Dockerfile app.py requirements.txt static/ templates/ =========> seperate file only add

		git commit -m "scraping data in API and update data in DB"  ==========> Working details add and commit

		git push ======> final 

		git diff (filename)=======>what is differnt in file and change first check git status then use this commend

		git stash======>hide

		git stash pop =====>unhide


python -m venv myenv
source env/Scripts/activate ==========> New Environment File



cd (DirectoryName) ========> add directory file

cd .. ========> remove that directory file



python -m unittest -v tests/test_(fileName) =========>code testing in powershell

pytest --html = report.html =========> html file of unittest report


import secrets
secrets.SystemRandom().getrandbits(128)


commend of change the code 

:%s/(currentName)/(updateName)
:wq exit the page





cat =====> read,

docker ps | grep (filename) ========>seperate ah file yedukkum

code (filename)======>vscode la file ah view pannalam

✔ ~/workspace/orchrepo/src/compose [master|✚ 2]
10:42 $ cd conf/orch_vhosts/               ==================> code of default.conf this change the ip address then cd ../../ go the compose file,
check the commend fig this use of docker, then type this commends,

fig stop nginx;
fig rm nginx;
fig up -d nginx; =======> d discover logs are load in background

./orchdown;./orchrm;./orchup;

docker run --rm -d --name product_details -p 192.170.1.234:3307:3306 -e MYSQL_ROOT_PASSWORD=arun -e MYSQL_ROOT_HOST='%' -v mysql_volume:/var/lib/mysql mysql/mysql-server


	C:\Windows\System32\drivers\etc



docker ps | grep tlc
fig logs -f tlc --tail=1000;


Api la Error message change panna itha use pannanum file is i18:

include like ======> cd (filename)

gradle pTML;

include 'gradle-convention-plugins'
include 'bom'
include 'i18n'
include 'di'
include 'jsonschema'
include 'domain-model'
include 'utils'
include 'exceptions'
include 'otpclient'
include 'logclient'
include 'validator'
include 'microservice'
include 'api-model'
include 'dao'
include 'mail'
include 'pkiclient'
include 'auditlog'
include 'quartz-mongodb'
// application subprojects
include 'app'
include 'report'
include 'notification'
include 'download'
include 'apigateway'


Once u change the API message are API coding You commend the below lines;

sample of i18 message:

direcory of ws/orch/src/(filename)

domain-model ========> this is the DB entries
api-model ========> this is request and response of code
dao ======> this is query
i18 ======> this is message properties

then add the commend of src :
gradle docker


this process ========> UI ======>API gateway(authendication,authorized) ======>APP/TLC(controller,service,implementation)=======>DB,Request,Query,Message(dependency)model view controller


Hotfix Process:

Hotfix
create branch
current release from release
hotfix in suffix added in the 3rd tab
git checkout the url
git cherry-pick paste the merge-id
git push
create pull request
delete the branch


How to get a serial number in PKI cert:

docker ps |grep pki
copy the container id compose-pki-1
curl http://api.pki.iotium:8080/pki/vpn-ca/certs/ -X POST > inode.p12  ===========>api.pki.iotium change the local the ui runs in local so change the name
"openssl pkcs12 -in inode.p12 -passin pass: -nodes -nokeys -clcerts -out inode.pem"  OR  openssl pkcs12 -in inode.p12 -passin pass: -nodes -nokeys -clcerts -out inode.pem -legacy

openssl x509 -in inode.pem -text



OTA run Local:

cd portal
npm run format; rm -rf build/; npm run build; docker buildx bake otaui; docker build -t iotium/ota-portal:<TicketID> .;
cd compose
.env
portal ==> <TicketID>
direnv allow
fig stop otaui; fig rm -f otaui; fig up -d otaui --no-deps;


npm run format; rm -rf build/; npm run build; docker buildx bake otaui; docker build -t iotium/ota-portal:dev .;
fig stop otaui; fig rm -f otaui; fig up -d otaui --no-deps;

cd ~/workspace/otarepo/src/portal
npm run format;rm -rf build/; npm run build;fig build otaui;
cd  ~/workspace/otarepo/src/compose
fig stop otaui; fig rm -f otaui; fig up -d otaui --no-deps;

npm run build-locale;npm run build-css;rm -rf build/; npm run build;fig build otaui; 
"OR"
npm run format;rm -rf build/; npm run build;npm run build-css; npm run build-locale;fig build otaui;
fig kill otaui; fig rm -f otaui; fig up -d otaui;




docker file rearranging use the below commends weekly 2 or 3 times

docker rmi -f $(docker images -f "dangling=true" -q)
docker rmi -f $(docker images | grep  "ota-develop")



netstat -ano | findstr 3306 ======> port problem use in gitbash command
stop-process <PID> ======> use in window powershell.




CONFLICT PROCESS:

git checkout 9f894a6
# Note: This will create a detached head.
git merge remotes/origin/develop




To configure mail server in OTA:
-------------------------------
In env file change the below
MAIL_SMTP_USERNAME=<mailid>
MAIL_SMTP_PASSWORD=<mailid - pwd>
MAIL_SMTP_FROM=<mailid>
cd ~/workspace/otarepo/ota-compose
fig kill notification; fig rm -f notification;fig up -d notification;
fig kill keycloak-configloader;fig rm -f keycloak-configloader;fig up -d keycloak-configloader;


All software languages link:
https://devdocs.io/



SE Docker ah Run Panna:

first go to docker-entrypoin.sh command if condition.
orch portal --- dockerignore add "build"
Follow below commands
cd  workspace/orchrepo/src/portal/pheonix
Then do : npm run build
Then : cd  ../
Then Run Below command :
 docker build -t iotium/orch-ui:LAT-19274-UI .
Then Run :
docker push iotium/orch-ui:LAT-15283-b1

stop && RM && UP process  ======> apisix && apisix-init



docker build -t iotium/orch-ui:LAT-18829 .

docker push iotium/orch-ui:LAT-18829 .

  
Setup Customer Organization
  
Login as "oadmin"

Goto Swagger API documentation and Create Org using API.
Name : Customer Org
Parent Org Id : 1445c3b6f0fe454992fc0767dfde11fd
Create user otasupport under customer org using UI
First Name: OTA
Last Name: TA Support
Mail : otasupport@DEPLOYMENT_NAME.remoteaccess.view.com
Scope : Local
Org : Customer Org
./tools/samba-tool user setexpiry otasupport --noexpiry For not to expire the password
Login into keycloak and set email verified for otasupport user.
Now login as otasupport and setup everything from UI.
Update the lastname as "Support" instead of "TA Support"


		
Device Onboard :
	To initiate http device,
		docker-compose -f devtools.yml up -d httpbin
		./tools/getIP httpbin
		Note: Add ip and URL in etc/host
		To initiate RDP device,
		docker-compose -f devtools.yml up -d rdesktop
		./tools/getIP rdesktop
		Note: Add ip and URL in etc/host


UPDATE device_details SET "repnetIP" = 192160004 WHERE id = 17;



Password has been changed successfully. Recent password update takes couple of minutes to reflect.




""""""""""OTA BUILD CHANGES""""""""""""
1.DOCKERFILE :
		# FROM node:14.18.1@sha256:c5b4544cee41df44e2bcaaaba642235fb01408c11411ca16fa454598c1168063 AS builder

		# RUN mkdir /code
		# COPY ./config /code/config
		# COPY ./public /code/public
		# COPY ./scripts /code/scripts
		# COPY ./locales /code/locales
		# COPY ./src /code/src
		# COPY .env /code/.env
		# COPY jsconfig.json /code/jsconfig.json
		# COPY package-lock.json /code/package-lock.json
		# COPY package.json /code/package.json

		# RUN cd /code && npm --silent install && npm run build

		# base image
		FROM node:14.18.1@sha256:c5b4544cee41df44e2bcaaaba642235fb01408c11411ca16fa454598c1168063
		LABEL maintainer="ioTium OTA Engg <otaeng@iotium.io>"

		EXPOSE 8084

		RUN mkdir /main
		# COPY --from=builder /code/build /main
		COPY ./build /main
		RUN npm --prefix /main install

		ARG GIT_COMMIT=unspecified
		ARG BUILD_IMAGE_ID=unspecified
		ENV GIT_COMMIT=${GIT_COMMIT}
		ENV BUILD_IMAGE_ID=${BUILD_IMAGE_ID}
		ENV ASSETS_CDN_URL=''

		# Environment Variables
		ENV MAPBOX_TOKEN=''
		ENV KB_DOCUMENT_VERSION='latest'

		COPY entrypoint.sh /
		COPY healthcheck.js /
		RUN chmod +x /entrypoint.sh

		ENTRYPOINT ["/entrypoint.sh"]

		CMD ["server"]
		
2. .dockerignore 

	
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""