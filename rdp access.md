case one 
https://qa-ra.staging.neeve.dev/deviceprofilepage/4240
user i used ([venkatesan.sivanandan@view.com](mailto:venkatesan.sivanandan@view.com))
i logged with  user in chrome and access the device 
then i logged in into the same user in the edge browser with the same user and i try to access the device the edge  browser session is active and the chrome session have disconnected 
this scenario is same use same device but in different browser only one session at a time 

case two 
https://qa-ra.staging.neeve.dev/deviceprofilepage/4240
i logged with two users 
user 1 ([venkatesan.sivanandan@view.com](mailto:venkatesan.sivanandan@view.com)) (edge)
user 2 (naveen.arockiaraj@neeve.ai) (chrome)
i logged in edge with user 1 and i access the device the session is active in chrome session 
then i logged in into the chrome browse with user 2 then i access the device the edge session is now alive but the chrome session have been disconnected 
this scenario is different user with same device only one session allowed at a time 
![[Pasted image 20260822111015.png]]

case three
https://qa-ra.staging.neeve.dev/deviceprofilepage/4240
user  ([venkatesan.sivanandan@view.com](mailto:venkatesan.sivanandan@view.com))
in chrome browse i logged into a user and access the device a seession is active then i try to make a new session when teh newly opened session have active the previous session gets loggout 
thsi secanrio is same user same browser try two session to access but only one session is active the another session gets logged out 

![[Pasted image 20260822113726.png]]