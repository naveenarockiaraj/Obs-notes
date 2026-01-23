Hi Team,
This is the expected behavior:
Given:
- USER: Test user
- Role: TestRole_5node
- Permission of TestRole_5node: `NODE:REBOOT`,`EVENT:VIEW`,`ACTIVITY:VIEW`
Then:
- This user have only read access, but the the node and its properties the navbar will visible, 
- because User have permission for `NODE:READ`  integrated with the node end point `api/v2/node`, 
- but if we open any of it it will show as  *Access Denied ! You don't have access to this page. Please contact your administrator*
But:
 - on API if we call the `api/v2/node` with this user the response of all node we can see, 
 - for cluster `api/v2/cluster` response also we can able to see the details.
 - because all the endpoints of these permission are connected with `api/v2/node`
	 -- The permission are integrated with node end point `api/v2/node` is :`NODE:REBOOT`, `NODE:READ`, `NODE:ADMIN`, `NETWORK:READ`, `NETWORK:CONNECT_DISCONNECT`, `NETWORK:ADMIN`, `NETWORK:DIAGNOSTIC`, `SERVICE:READ`, and `SERVICE:ADMIN`
So only the user can able to view the node details from API response.

In UI we blocked it because the node and its properties are blocked with permission of current users role which is read only, so only the user cant able to view node and its properties in UI
Hi Team,

This is the expected behavior:

### **Given**:

- **User**: Test user
- **Role**: TestRole_5node
- **Permissions of TestRole_5node**: `NODE:REBOOT`, `EVENT:VIEW`, `ACTIVITY:VIEW`

### **Details**:

1. **UI Behavior**:
    
    - The user has **read-only access** for `EVENT:VIEW` and `ACTIVITY:VIEW`.
    - Only users with `NODE:READ` or `NODE:ADMIN` permissions can view the node list and its details in the UI.
    - Since the current user only has the `NODE:REBOOT` permission, they cannot view the node list or its properties in the UI.
    - However, the `NODE:REBOOT` permission is integrated with the `api/v2/node` endpoint, which allows the user to see node properties via the API .
    - If the user tries to open a node or property page in the UI, they see the following error:  
        _"Access Denied! You don't have access to this page. Please contact your administrator."_
2. **API Behavior**:
    
    - When the `api/v2/node` endpoint is called using this user's credentials, the response includes details of all nodes.
    - Similarly, the `api/v2/cluster` endpoint returns cluster details.
    - This behavior occurs because the following permissions are integrated with the `api/v2/node` endpoint:
        - `NODE:REBOOT`
        - `NODE:READ`
        - `NODE:ADMIN`
        - `NETWORK:READ`
        - `NETWORK:CONNECT_DISCONNECT`
        - `NETWORK:ADMIN`
        - `NETWORK:DIAGNOSTIC`
        - `SERVICE:READ`
        - `SERVICE:ADMIN`
3. **Summary**:
    
    - **API**: The user can view node details through the API because of the `NODE:REBOOT` permission, which is integrated with the `api/v2/node` endpoint.
    - **UI**:
        - Access to nodes and their properties in the UI is restricted because the user lacks `NODE:READ` or `NODE:ADMIN` permissions.
        - This blocks their ability to view the node list or its properties in the UI, resulting in an _Access Denied_ message when attempting to access these pages.