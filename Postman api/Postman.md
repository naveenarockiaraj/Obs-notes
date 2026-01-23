==important== **need to study this**
how to upload a pic in postman app
	reff link
1. https://learning.postman.com/docs/sending-requests/create-requests/test-data/
2. https://community.postman.com/t/how-to-upload-images-to-a-post-request/15256
3. https://stackoverflow.com/questions/39660074/post-image-data-using-postman      


[[postman]] 
Before importing the file to postman we have to get the new Pull and only we have to import it.
otherwise it will show error that format is wrong.

API testing
1. we have to write the script for the API and have to check weather the environment variable and global variable are available or not..

**GET and SET variables**
![[Pasted image 20240619124151.png]]
![[Pasted image 20240619125219.png]]// set variables
pm.globals.set('name', 'naveen1');
pm.collectionVariables.set('name', 'aro');
pm.environment.set('name', 'raj');
pm.variables.set('name', 'navi');

// get variables
let glovarValue = pm.globals.get('name');
console.log(glovarValue)>>>>>>>>>>>>>>>>>>>>Give the name to the variables and console it.
// console.log(pm.globals.get('name'))>>>>>>>>>>give the total step in the console to get values.
let collvarValue = pm.collectionVariables.get('name')
console.log(collvarValue);
let envValue = pm.environment.get('name')
console.log(envValue)
let varValue = pm.variables.get('name')
console.log(varValue)
