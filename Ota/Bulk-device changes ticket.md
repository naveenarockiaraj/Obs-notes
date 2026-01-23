*utills file line 614*
const BULK_ACTION_HEADERS = {
  user: [
    "Review User Details",
    "Configure User Assignments",
    "Confirmation Summary",
  ],
  device: [
    "Review Device Network Details",
    "Review Device Location Details",
    "Add Device Connections",
    "Confirmation Summary",
  ],
};

*line 627*
const BULK_ACTION_FOOTER = {
  user: [
    "Errors must be resolved before proceeding",
    "Each user must be assigned a role to continue",
  ],
  device: [
    "Errors must be resolved before proceeding",
    "Errors must be resolved before proceeding",
    "Each device must have at least one connection",
    "Add users to provide remote access to your newly onboarded devices",
  ],
};

when im using this code 
in role assignment is working fine when the logged user is org admin it showing all user role and when it is portfolio user it showing the site and access use 
but 
when i logged as portfilo user and when i try to assign role as site admin and when i click the site assignment it not showing the sites it showing as empty ....
but for the org and root user its working fine