[[Indiadevot]]
**Steps to change in dev site**
1. ./tools/dumpall >>>>>>>>to take backup
2. cp .env {date}env >>>>>>backup
3. ==before pull (or) checkout have to stackdown (./stackdown)==
4.  :%s/ota-develop-1442/ota-develop-1443/ >>>>>>>>build chenge
5. after the build have changed then only need to checkout the branch
6. ./stackup >>>>>>>>to bring up
7. watch docker ps >>>>>>to watch docker
8. esc : q >>> quit
9. esc : q! >>>>dont save
10. esc : wq >>>>write or save and quit
11. watch docker service ls >>>>to seee the running service
12. docker ps>>>>>>> to see the container 
13. mv ==.env24092024== .env >>>>>>>>to change the backuped env
14. ./tools/restart keycloak >>>>>>>>>to rstart container
#### ### indiadevot
ssh -i indiadevot_key.pem ubuntu@52.13.78.107
cd ota>>> and press tab button

![[Pasted image 20240819111405.png]]
![[Screenshot (21).png]]
