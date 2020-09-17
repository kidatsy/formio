Deploying Form.io to Heroku
===============================
This library is an adaptation of formio/formio to allow it to be deployed to Heroku. Form.io is a revolutionary combined Form and API platform for Serverless applications. This repository serves as the core Form and API engine for https://form.io. This system allows you to build "serverless" data management applications using a simple drag-and-drop form builder interface. These forms can then easily be embedded within your Angular.js and React applications using the
```<formio>``` HTML element.

Walkthrough video and tutorial
-------------------
For a walkthrough tutorial on how to use this Open Source platform to build a Serverless application, watch the video [0 to M.E.A.N in 30 minutes](https://www.youtube.com/watch?v=d2gTYkPFhPI)

Form Building & Rendering Demo
-------------------
Here is a link to a demo of the Form Building and Form Rendering capability that can be hooked into this API platform.

http://codepen.io/travist/full/xVyMjo/

Run with Docker Compose
------------------
The fastest way to run this library locally is to use [Docker](https://docker.com).

 - [Install Docker](https://docs.docker.com/v17.12/install/)
 - Download and unzip this package to a local directory on your machine.
 - Open up your terminal and navigate to the unzipped folder of this library.
 - Type the following in your terminal
    ```
    npm install
    docker-compose up
    ```
 - Go to the following URL in your browser.
    ```
    http://localhost:3001
    ```
 - Use the following credentials to login.
    - **email**: admin@example.com
    - **password**: CHANGEME
 - To change the admin password.
    - Once you login, click on the **Admin** resource
    - Click **View Data**
    - Click on the **admin@example.com** row
    - Click **Edit Submission**
    - Set the password field
    - Click **Save Submission**
    - Logout

 - Have fun!

Manual Installation (Node + MongoDB)
-------------------
To get started you will first need the following installed on your machine.

  - Node.js - https://nodejs.org/en/
  - MongoDB - http://docs.mongodb.org/manual/installation/
    - On Mac I recommend using Homebrew `brew install mongodb-community`
    - On Windows, download and install the MSI package @ https://www.mongodb.org/downloads
  - You must then make sure you have MongoDB running by typing `mongod` in your terminal.

Running with Node.js
-------------------
You can then download this repository, navigate to the folder in your Terminal, and then type the following.

```
npm install
npm start
```

This will walk you through the installation process.  When it is done, you will have a running Form.io management
application running at the following address in your browser.

```
http://localhost:3001
```

The installation process will also ask if you would like to download an application. If selected, the application can be found at the following URL.

```
http://localhost:8080
```

You can also see the contents of the application (for modification) within the ```app``` folder which exists inside of the folder where you downloaded this repository.

Development
--------------------
To start server with auto restart capability for development simply run this command:
```
npm run start:dev
```

Deploying to Heroku
--------------------
The changes here are reflected in this comment on an issue on the original repository: https://github.com/formio/formio/issues/961#issuecomment-694082340

Namely:
1. Fork this library if you would like your own variant. It should work out of the box though.
2. Don't use the docker container for the stack/framework. If you've set that up already, run `heroku stack:set heroku-18` to revert back to the heroku stack.
3. You will be using the regular heroku stack instead, so add the `nodejs` buildpack in the Heroku settings.
4. Set up your mongo DB somewhere - we would recommend using MongoDB Atlas, as it has free sandbox pricing, rather than any Heroku add-ons. You'll need the URL for the resulting DB for the next step.
5. Set the `NODE_CONFIG` env var to: `{"mongo": "<MONGOURL>","host":"<APPNAME>.herokuapp.com","protocol":"https","domain":"https://<APPNAME>.herokuapp.com"}`, replacing `<MONGOURL>` with the mongo url you got from step 4 and `<APPNAME>` with the name of your app.
6. Make sure to set the `ROOT_EMAIL` and `ROOT_PASSWORD` env variables to set up the initial admin account on first start up. Set the `OVERRIDE_ROOT_USER_CREATION` to `true` if you would like to not keep generating new admin accounts with each subsequent deployment.

License
--------------------
This library is extending the original library here: https://github.com/formio/formio, under the OSL-v3 license, which is a copy-left OSI approved license. Please read the license @ https://opensource.org/licenses/OSL-3.0 for more information. Their goal for the change to OSLv3 from BSD is to ensure that appropriate Attribution is provided when creating proprietary products that leverage or extend this library.
