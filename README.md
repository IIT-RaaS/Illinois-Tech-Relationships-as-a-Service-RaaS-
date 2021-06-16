# Illinois Tech Relationships as a Service (RaaS)
A proposed friendships/dating service for use by Illinois Institute of Technology students

Service Setup:
1. create an alias (iitrelationships@gmail.com) for your hawk account (...@hawk.iit.edu)
2. create two folders: "Matching Forms" and "Sign-Up Form"
3. place sign-up form in the Sign-Up Form folder and create a spreadsheet for responses (with default name)
  1. restrict sign-up form to users of specific domain (iit.edu)
4. in the Sign-Up Form folder, create a spreadsheet titled "Serviced Users"
5. in Retrieve Folders/Files.gs, run getFolderIdHelper, getSpreadsheetIdHelper, and getSignUpFormIdHelper and update global id variables
6. create a copy of the script for every suspected 19 users (20 triggers per script - 1 for sign-up form)
7. in each copy, in Triggers.gs, change the conditional in onSignUp to service 19 users
8. create one fake sign-up
  1. in each script copy, in Sign Ups.gs, run main to authorize script with necessary permissions
  2. remove the fake sign-up from the form and delete row from responses spreadsheet
  3. delete any folders in the "Matching Forms" folder

1. A numbered list
    1. A nested numbered list
    2. Which is numbered
2. Which is numbered

Potential Bugs:
* two users submit likes/dislikes for each other within 10 seconds => two scripts might simultaneously access same spreadsheet
  * workaround: I expect this to be very rare, so if I get a script error, I'll manually add the users back to each other's candidates lists
  * future development: implement a form execution queue (this will be extremely difficult with multiple copies of same script)
* fail to read from serviced users spreadsheet within 30 secs
  * workaround: I expect this to be very rare, so if I get a script error, I'll delete the last user in Serviced Users spreadsheet
and manually rerun main in Sign Ups.gs
