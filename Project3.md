## Documentation for Project 3
## SIMPLE TO-DO APPLICATION ON MERN WEB STACK - aws virtual server

## STEP 1 — BACKEND CONFIGURATION

-- Starting by ssh into my server labelled 'Projec 3 - MERN' from my vscode terminal in windows machine 

`sudo apt update`--(running command to update my list of packages in Ubuntu package manager)
![BackendConfig-Update](.\Image-3\BackendConfig-Update-1.PNG)  

`sudo apt upgrade`--(running command to upgrade to lastest list of packages in Ubuntu package manager)
![BackendConfig-Upgrade](.\Image-3\BackendConfig-Upgrade-2.PNG)

`curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash`--(Retieving location of Node.js software from Ubuntu repositories)
![BackendConfig-Node.js-Locate](.\Image-3\BackendConfig-Node-Locate-3.PNG)

`sudo apt-get install -y nodejs`--(Installing Node.js software on Express server, This command installs both nodejs and npm-- NPM is the Node package manager)
![BackendConfig-Node.js-Install](.\Image-3\BackendConfig-Node.js-Install-4.PNG)

`node -v``npm -v`--(confirming verisions of Nodejs and NPM installed)
![BackendConfig-Node.js-Version](.\Image-3\BackendConfig-Node.js-Version-5.PNG)

`mkdir Todo`--(Create a new directory for my To-Do project)
![BackendConfig-CreateDir](.\Image-3\BackendConfig-CreateDir-6.PNG)

`ls -lih`--(see more useful information about files and directories,showing different properties and size in human readable format)
![BackendConfig-View-Properties](.\Image-3\BackendConfig-View-Properties-7.PNG)

`cd Todo`--(change my current directory to the newly created Todo Directory)
![BackendConfig-ChangeDir](.\Image-3\BackendConfig-ChangeDir-8.PNG)

`npm init`--(Initialising my project,to enable new file named "package.json" be created. This file normally contains information about my application and the dependencies that it needs to run.)
![BackendConfig-InitializeProject](.\Image-3\BackendConfig-InitializeProject-9.PNG)

`ls`--(Confirming package.json file is created in the Todo directory)
![BackendConfig-Confirm-JsonPackage](.\Image-3\BackendConfig-Confirm-JsonPackage-10.PNG)

## STEP 2 — INSTALL EXPRESSJS

`npm install express`--(Install express software using npm - node package manager)
![Expressjs-Install](.\Image-3\Expressjs-Install-1.PNG)

`touch index.js`--(created a new file "index.js" in Todo directory)
![Expressjs-Create-File](.\Image-3\Expressjs-Create-File-2.PNG)

`ls`--(confirm my index.js file is successfully created )
![Expressjs-View-Content](.\Image-3\Expressjs-View-Content-3.PNG)

`npm install dotenv`--(Install the dotenv module)
![Expressjs-Install-dotenv](.\Image-3\Expressjs-Install-dotenv-4.PNG)

`vim index.js`--(Open the index.js file using vim text edior and pasted snippet code)
![Expressjs-Create-IndexjsFile](.\Image-3\Expressjs-Create-IndexjsFile-5.PNG)

`node index.js`--(start my server to see if it works, Server is running on port 5000 in my terminal)
![Expressjs-StartServer](.\Image-3\Expressjs-StartServer-6.PNG)

--(Amended security group inbound rule for Express server to listen to Port 5000)
![Expressjs-SecGroup-5000](.\Image-3\Expressjs-SecGroup-5000-7.PNG)

`curl -s http://169.254.169.254/latest/meta-data/public-ipv4`;`curl -s http://169.254.169.254/latest/meta-data/public-hostname` --(Retrieving my server Public IP address and Publid DNS name from my terminal.Testing how to retrieve files content in my metadata directory.
![Expressjs-Metadata-PublicIPAdd-DnsName](.\Image-3\Expressjs-Metadata-PublicIPAdd-DnsName-8.PNG)

`http://<PublicIP-or-PublicDNS>:5000`--(Using web browser to access my server Public IP or Public DNS name configured to listen on port 5000)
![Expressjs-Broswer-Server-PublicDnsName](.\Image-3\Expressjs-Broswer-Server-PublicDnsName-9.PNG)

`mkdir routes`--(create folder "routes" within the Todo project directory. and also creating a file api.js within the route directory)
![Expressjs-CreateDir-Routes](.\Image-3\Expressjs-CreateDir-Routes-10.PNG)

`touch api.js`--(create a file "api.js" within the route folder of the Todo project directory)
![Expressjs-CreateFile-Api](.\Image-3\Expressjs-CreateFile-Api.js-11.PNG)

`vim api.js`--(Open the api.js file using vim text edior and pasted snippet code)
![Expressjs-OpenFile-Vim](.\Image-3\Expressjs-OpenFile-Vim-12.PNG)

## STEP 3 — MODEL DIRECTORY

`npm install mongoose`--(Install the mongoose to make use of mongodb datadase)
![Model-install](.\Image-3\Model-install-1.PNG)

`mkdir models && cd models && touch todo.js`--(create folder "models" within the Todo project directory and also creating a file todo.js within the models folder)
![Model-Create-DirModels-FileTodo](.\Image-3\Model-Create-DirModels-FileTodo.js-2.PNG)

`vim todo.js`--(configure todo.js file using vim text edior by pasting snippet code)
![Model-ConfigFile-todo.js](.\Image-3\Model-ConfigFile-todo.js-3.PNG)

`vim api.js`--(Update my routes from api.js file in the route directory. Change directory to route folder to configure api.js file by deleting pervious snippet in vim text edior, then replace with new snippet code. )
![Model-ConfigFile-todo.js](.\Image-3\Model-ConfigFile-todo.js-3.PNG)

## STEP 4 — MONGODB DATABASE

`touch .env`,`vim .env`--(Creating a file ".env" in my Todo directory, this is to access environment variables.Open the .env file using vi text edior and add my connection string to access my database)
![MongoDB-create-.env](.\Image-3\MongoDB-create-.env-1.PNG)

`vim index.js`--(Open the index.js file using vim text edior, deleting content then replacing snippet code)
![MongoDB-Replace-Index](.\Image-3\MongoDB-Replace-Index.js-2.PNG)

`node index.js`--(Start my server using the command. Server running on port 5000 and Database connected successfully)
![MongoDB-DBconnectString](.\Image-3\MongoDB-DBconnectString-3.PNG) 

## STEP 5 — Testing Backend Code without Frontend using RESTful API

`http://18.235.233.67:5000/api/todos`--(Creating a POST request to my API, this request sends a new task to my To-Do list so the application could store it in the database.)
![TestingBackendCode-PostRequestAPI](.\Image-3\TestingBackendCode-PostRequestAPI-1.PNG)

`http://18.235.233.67:5000/api/todos`--(Creating a GET request to my API, This request retrieves all existing records from out To-do application (backend requests these records from the database and sends it back as a response to GET request)
![TestingBackendCode-PostRequestAPI](.\Image-3\TestingBackendCode-PostRequestAPI-1.PNG)

## STEP 6 — FRONTEND CREATION

`npx create-react-app client`--(To start out with the frontend of the To-do app, this is to scaffold our app. A new folder is created called client in To-do directory - this adds all the react code)
![Frontend-CreateReactApp-ClientFolder-Install](.\Image-3\Frontend-CreateReactApp-ClientFolder-Install-1.PNG)

`npm install concurrently --save-dev`--(Installing dependencies "concurrently" is used to run more than one command simultaneously from the same terminal window)
![Frontend-InstallDependencies-Concurrently](.\Image-3\Frontend-InstallDependencies-Concurrently-2.PNG)

`npm install nodemon --save-dev`--(Installing dependencies "Nodemon" is used to run and monitor the server. If there is any change in the server code, nodemon will restart it automatically and load the new changes.)
![Frontend-InstallDependencies-Nodemon](.\Image-3\Frontend-InstallDependencies-Nodemon-3.PNG)

`vi package.json`--(In Todo directory changing calvert in snippet code for package.json file to suit dependecies installed)
![Frontend-Replace-Package.json](.\Image-3\Frontend-Replace-Package.json-4.PNG)

`"proxy": "http://localhost:5000,"`--(Change directory to client folder then configure Proxy in package.json, by adding the key value pair in file)(Obj: To access the application directly from the browser by simply calling the server url like "http://localhost:5000" instead of entire path "http://localhost:5000/api/todos")
![Frontend-AddProxy-Client-Package.json](.\Image-3\Frontend-AddProxy-Client-Package.json-5.PNG)

`npm run dev`--(Output: dependency concurrently "npm start-watch" running from the root project directory and change directory to client and concurrently start app "cd client && npm start". My Todo app opens and start running on localhost:3000)
![Frontend-Run-App](.\Image-3\Frontend-Run-App-6.PNG)

`http://54.87.252.155:3000`--(On my network, Viewing client side web application through the broswer using public IP address. One can see front end UI)
![Frontend-Broswer-Network-PublicIP](.\Image-3\Frontend-Broswer-Network-PublicIP-7.PNG)

`mkdir components && cd components && touch Input.js ListTodo.js Todo.js`--(In src directory within Todo directory 3 file were created)
![ReactComponent-CreateFiles](.\Image-3\ReactComponent-CreateFiles-1.PNG)

`vi Input.js`--(Open the Input.js file in the component folder within src directory using vi text edior, copy and paste snippet code)
![ReactComponent-Replace-Input.js](.\Image-3\ReactComponent-Replace-Input.js-2.PNG)

`npm install axios`--(cd into my client from my terminal then install Axios, a HTTP client based for the browser and node.js)
![ReactComponent-Install-Axios](.\Image-3\ReactComponent-Install-Axios-3.PNG)

`vi ListTodo.js`--(Open the ListTodo.js file in the component folder within src directory using vi text edior, copy and paste snippet code)
![ReactComponent-Replace-ListTodo](.\Image-3\ReactComponent-Replace-ListTodo-4.PNG)

`vi Todo.js`--(Open the Todo.js file in the component folder within src directory using vi text edior, copy and paste snippet code)
![ReactComponent-Replace-Todo](.\Image-3\ReactComponent-Replace-Todo-5.PNG)

`vi App.js`--(Adjustment to our react code, change directory into src folder. Using vi text edior open and paste in App.js file snippet code)
![ReactComponent-Adjustment-App.js](.Image-3\ReactComponent-Adjustment-App.js-6.PNG)

`vi App.css`--(Adjustment to our react code, change directory into src folder. Using vi text edior open and paste in App.css file snippet code)
![ReactComponent-Adjustment-App.css](.\Image-3\ReactComponent-Adjustment-App.css-7.PNG)

`vi Index.css`--(Adjustment to our react code, change directory into src folder. Using vim text edior open and paste in Index.css file snippet code)
![ReactComponent-Adjustment-Index.css](.\Image-3\ReactComponent-Adjustment-Index.css-8.PNG)

`npm run dev`--( My Todo app opens and start running on localhost:3000. To-Do app ready and fully functional with the functionality: creating a task, deleting a task and viewing all your tasks)
![ReactComponent-Start-TodoApp](.\Image-3\ReactComponent-Start-TodoApp-9.PNG)

`http://52.203.0.44:3000`--(created a simple To-Do and deployed it to MERN stack. Written codes for frontend application using React.js that communicates with a backend application written using Expressjs. we also created a Mongodb backend for storing tasks in a database. tested Backend API code with Postman)
![ReactComponent-Start-TodoApp](.Image-3\ReactComponent-Start-TodoApp-10.PNG)

