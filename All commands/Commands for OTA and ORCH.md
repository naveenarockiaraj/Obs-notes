[[OTA and ORCH]]
1. docker ps >> to check the status of the docker
2. ./orchdown;./orchrm; >> when the two file is online we have to down the one file. using this command.
3. cd workspace/orchrepo/src/compose/ >> to compose the file
4. direnv allow >> to allow the docker desktop to online
5. fig down; fig rm -f; fig up -d; >> to down the docker and remove and upload the file(docker compose :: fig)
6. fig log -f >>To check the logs
7. fig stop >> to stop all component
8. ls>>>>> to select the folder
9. cd ..>>>>>>for go out from the folder
10. code README.md>>>>to read every file
11. code filename >>>>>>to read specific file
12. fig kill;fig up -d;
13. ./orchdown; ./orchrm; >>>>>>>>orchestrator🐍
14. for QA debug logs
	    have to change the qa site dockercompose.yml
	    `KEYCLOAK_LOGLEVEL: DEBUG`
```
 ./tools/janusdb
 select * from user_details;
 select * from user_details where "objectGUID"='d380d6a80d6147a1bb38a3ee5bf2a0e2';
  exit
```
> [!Build tag change]
> docker tag iotium/ota-apigw:dev iotium/ota-apigw:OTQA-4366
> docker tag iotium/ota-portal:dev iotium/ota-portal:OTA_G
> docker tag iotium/ota-portal:dev iotium/ota-portal:OTQA-4310bulk

> [!otaui build (and) npm start config]
> npm run build-locale;npm run build-css;rm -rf build/; npm run build;fig build otaui; 
> "OR"
> npm run format;rm -rf build/; npm run build;npm run build-css; npm run build-locale;fig build otaui;
> fig kill otaui; fig rm -f otaui; fig up -d otaui;

> [!after taking the new build:]
> direnv allow 
> fig down; fig rm -f;
> fig up -d;

> [!To clear all data in ota]
> 
> fig down -v 
> docker-compose up -d keycloak 
> docker-compose up -d keycloak-disable-https 
> docker-compose restart keycloak 
> docker-compose up -d

> [!To clear all data in ORCH]
>
> docker container prune
> docker image prune
> docker system prune -a
> docker volume rm $(docker volume ls)

![[Pasted image 20240903170235.png]]


INTO janusdb file command
![[Pasted image 20240813152834.png]]


Options:
      --ansi string                Control when to print ANSI control characters ("never"|"always"|"auto") (default "auto")
      --compatibility              Run compose in backward compatibility mode
      --dry-run                    Execute command in dry run mode
      --env-file stringArray       Specify an alternate environment file
  -f, --file stringArray           Compose configuration files
      --parallel int               Control max parallelism, -1 for unlimited (default -1)
      --profile stringArray        Specify a profile to enable
      --progress string            Set type of progress output (auto, tty, plain, quiet) (default "auto")
      --project-directory string   Specify an alternate working directory
                                   (default: the path of the, first specified, Compose file)
  -p, --project-name string        Project name

Commands:
  attach      Attach local standard input, output, and error streams to a service's running container.
  build       Build or rebuild services
  config      Parse, resolve and render compose file in canonical format
  cp          Copy files/folders between a service container and the local filesystem
  create      Creates containers for a service.
  down        Stop and remove containers, networks
  events      Receive real time events from containers.
  exec        Execute a command in a running container.
  images      List images used by the created containers
  kill        Force stop service containers.
  logs        View output from containers
  ls          List running compose projects
  pause       Pause services
  port        Print the public port for a port binding.
  ps          List containers
  pull        Pull service images
  push        Push service images
  restart     Restart service containers
  rm          Removes stopped service containers
  run         Run a one-off command on a service.
  scale       Scale services
  start       Start services
  stats       Display a live stream of container(s) resource usage statistics
  stop        Stop services
  top         Display the running processes
  unpause     Unpause services
  up          Create and start containers
  version     Show the Docker Compose version information
  wait        Block until the first service container stops
  watch       Watch build context for service and rebuild/refresh containers when files are updated

Run 'docker compose COMMAND --help' for more information on a command.