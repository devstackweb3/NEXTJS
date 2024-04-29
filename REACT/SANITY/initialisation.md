# SANITY PROJECT DEPLOYMENT

## STEP 1 | Terminal VS Code 
Command line: npm -y create sanity@latest

CONFIGURATION (SET UP) PROJET SANITY
Select "Create new project"

Your project name: "test"

Use the default dataset configuration: "Yes"

Project output path: C:\Users\Full Stack Dev\Desktop\PROJETS\FREELANCE\TRAINING-WEBSITES\NEXTJSREACT\handcrafts\sanity

Select project template: "Blog (schema)"

Do you want to use Typescript: "Yes"

Package Manager: "npm"

## STEP 1.1 | CONFIGURATION COMMANDE UPDATE SANITY ARCHITECTURE

Package.json

add line under "scripts": {...}: 
"generate": "sanity schema extract && sanity typegen generate",

## AUTHENTICATION ISSUE | NOT ABLE TO BE RECOGNIZED AS ADMIN
This issue is encountered when a previous sanity project server has been deployed locally and hosted on the same address as "http://localhost:3333". To resolve the case, it is necessary to disconnect manually from sanity in the new created project before launching server. 

### STEP 1.0 | SANITY SERVER DISCONNEXION (if 2nd project deployment)
add line under "scripts": {...}:
"logout": "sanity logout",

### STEP 1.1 | DISCONNECT ORDER
Terminal VS Code: npm run logout

## STEP 1.2 | LAUNCH SANITY SERVER
Terminal VS Code: npm run start

Do you want to start a development server? **Yes**
