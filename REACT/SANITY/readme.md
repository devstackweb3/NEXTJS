# NEXTJS REACT - SANITY
Objective: Establishing a local server in which articles will be stored and retaken within an external NEXTJS Project through reusable REACT components using tailwindcss to design articles in their best UX overviews.
## STEP 1 | Initialize & Configure SANITY LOCAL SERVER independantly
**Terminal cmd:** npm i -g @sanity/cli
### STEP 1.1 | Configuration of Local Server
Follow the instructions and adapt according to the needs: 
- Typescript | YES
- Routes | YES
- NEXTJS | YES

## STEP 2 | Deploy SANITY LOCAL SERVER
**Terminal cmd:** sanity start

or 

**Terminal cmd:** npm run start

**Terminal cmd:** Do you want to start a development server instead? **"YES"**

## STEP 3 | Connect SANITY to initial NEXTJS REACT Project
Go under the terminal of NEXTJS project targeted and launch:

**Terminal cmd:** npm i @sanity/client

### STEP 3.1 | Configure ID project linking
Within NEXTJS REACT Project, external folder to sanity, establish new keys inside the .env file. 
```
NEXT_PUBLIC_PROJECT_ID='38...'

NEXT_PUBLIC_DATASET='production' 
```
**WARNING SECURITY:** Don't forget to mention within the gitignore file the .env document to exclude its publication on github. 

### STEP 3.2 | Establish the client connectivity with SANITY LOCAL SERVER
Create a folder called "utils" if not yet made.
Inside it create a file called "sanity-client.ts"

```
//sanity-client.ts file
import { createClient } from '@sanity/client'

export default createClient({
  projectId: process.env.NEXT_PUBLIC_PROJECT_ID,
  dataset: process.env.NEXT_PUBLIC_DATASET,
  useCdn: false,
  apiVersion: '@latest-version-on-date',
})
```
This file (react component created) will serve as a reference access point to connect to the local database established with SANITY through articles, news or blog posts registered on the local server.

'createClient' can be then called through the NEXTJS REACT pages architecture application to connect to the properties of the database created.

# Issues encountered

### How can I display whole document (post|article created) from SANITY local server linked with an external project in NEXTJS REACT (using pages architecture)?

By using a unique enclosing tag referring to the reusable REACT component imported as a named import. 
