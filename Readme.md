# React Easy Deploy

## _Deploy React.Js applications with ease_

React Easy Deploy is a promise driven script to help you in deploying your React.Js application with ease.

## Features

- Install necessary npm packages.
- Create a production build locally.
- Transfer the build to the server specified.
- Install and configure NGINX server on AWS instance.

## Tech

React Easy Deploy uses various tools and packages for deployment.

- [ssh2] - SSH2 client and server modules written in pure JavaScript for node.js.
- [node.js] - Node.js® is an open-source, cross-platform JavaScript runtime environment.
  - [Child process] - The node:child_process module provides the ability to spawn subprocesses.

## Installation

React Easy Deploy is best suitable with [Node.js](https://nodejs.org/) v12+ to run.
Install package using the below code.

```sh
npm i react-easy-deploy
```

## Setup

This is a one time setup required to run the script. Replicate the below steps in your project directory.

```
Root Folder
    |__  script.js
    |__  private_key (.pem file to access the server)
```

script.js

```
import deploy from "react-easy-deploy";
deploy();
```

Private key:
Place the private key (.pem) file that was used when creating the AWS EC2 instance in the same folder where script.js file is present.

## Create AWS EC2 instance

- Login to the aws account
- Navigate to EC2 dashboard -> Instances
- Click on "Launch instances"
- Create a key-pair (if don't have an existing one on aws) and download it. Specify the keypair using the dropdown.
- Click on Allow HTTP and HTTPS requests from the internet.
- Click on "Launch instance"

Once the instance is ready:

- Navigate to the instance summary by click on "Instance ID" under "Instances"
- Click on "Connect"
- Follow the steps mention under the "SSH Client" tab on your local machine. Make sure private key is not publicly viewable and in the same directory from where you run ssh command.
- Once inside the instance type "exit" to logout.

## Deploy

- Go to your project directory and add script.js and private key in .gitignore.
- Run the script using
  ```
  node script.js
  ```
- When prompted input the following:
  - Public IP address (found in instance summary)
  - User-server Public DNS addres: format should be user@ec2-server_info_here.compute.amazonaws.com (found in "SSH Client" tab after clicking "Connect")
  - Private key path: Enter private key path here. If already present beside script.js, ignore and press enter.

After following the above mentioned steps your app should be live on the server.

## License

MIT

[//]: # "These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax"
[node.js]: http://nodejs.org
[ssh2]: https://www.npmjs.com/package/ssh2
[child process]: https://nodejs.org/api/child_process.html
