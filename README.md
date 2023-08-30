<h1 align="center"><b>Docsify setup document </u></b></h1>


<div style='break-after:always'></div>

# Table of Contents

[Overview](#overview)

[Setup docsify in podman container](#2-setup-docsify-in-podman-container)

[Login github](#login-github)

[Markdown basic syntax](#Markdown-basic-syntax)



## **Overview** 

> Podman is a containerization tool for Linux-based operating systems. You can follow these steps to install Podman on Ubuntu:



**system updates**:

- First, update your system so that you have the latest package progress and dependencies:


```
 sudo apt update
```


![Alt text](pod%201.png)


## Install Podman 

- Now install the podman package

```
  sudo apt install -y podman 
```

![Alt text](pod2.png)


- The **(-y)** command line option lets you automatically say **"yes"** to everything the command asks for, which is useful for automating tasks without the need to provide manual confirmation.

  
##  Check Podman Version 

- podman is installed, you can check its version using the podman --version command:

```
podman --version
```

![Alt text](pod3.png)


- If podman is successfully installed in your system, then it will show you the version number.



## 2. Setup docsify in podman container

- To set up Docsify in a Podman container, you need to follow the below steps:

**Create a Directory for Docsify**

- Create a directory where you'll keep your Docsify documentation files. For example

> - You can create a new folder. then  you can use the "mkdir folder_name" command in terminal to create a new folder.

```
mkdir uk
```


> - Move inside the directory and create files.

```
cd uk
```

![Alt text](pod4.png)

## Create the File and Open it for Editing:

```
touch index.html
```

```
touch README.md
```

![Alt text](pod5.png)


- You can use a text editor like vim to create and edit the file. Open your terminal and run:

* Then after that, we have to write the HTML code in Index.html

 ```
vim index.html
```

![Alt text](pod7.png)


```
vim README.md
```


![Alt text](pod6.png)
 

## Create Dockerfile 
```
 FROM node:latest
 LABEL description="A demo Dockerfile for build Docsify."
 WORKDIR /docs
 RUN npm install -g docsify-cli@latest
 EXPOSE 3000/tcp
 ENTRYPOINT docsify serve .

```
<div style='break-after:always'></div>

## Build docker image


 ```
docker build -f Dockerfile -t docsify/demo .

``` 
<div style='break-after:always'></div>


## Run the New Container and Set the Directory


- Run the new container and enter the desired directory where you want to work with Docsify. Replace **/path/to/your/directory** with the actual path to your desired directory:

- **Let me explain the options -d, -p, and -v that are used in Podman containers**

> - **"-d"** **(Detach Mode)** : This option allows the container to run in the background, meaning the container will run as a separate process and free up your terminal.It's useful for users who don't want to see the container's output in the terminal.

> - **"-p"** **(Port Forwarding)** : This option enables port forwarding between the container and the host system. This means you can access the services running inside the container without external categorization.

> - **"-v"** **(Volume Mount)** : This option allows you to mount a file or directory between the container and the host system. As a result, you can use your host file system within the container, enabling data sharing for your container.

- ***First, create a Podman container for Docsify.***

```
podman run -d -p 3000:3000 -v /home/poem/docs:/docs localhost/docsify
```

![Alt text](pod8.png)


- Check if the container was created with the **“podman ps”** command.

```
podman ps
```

![Alt text](pod9.png)


## Access your Docsify documentation

- Open your web browser and enter **http://localhost:3000** in the address bar. This will allow you to view your Docsify documentation served from the container. You should see the Docsify interface displaying your documentation content.

![Alt text](pod88.png)

<div style='break-after:always'></div>



# 3.  Started with GitHub


## Step 1.

## Login github

**Now go to GitHub but how to login to GitHub account is given below**

 **Here's a step-by-step guide to hosting Docsify docs on GitHub**


**Sign in or log in to your Github account.**

> Log in to your GitHub account.


![Alt text](POD%2021.png)


## Create a New Repository

**On GitHub, click the "New" button to create a new repository. Give it a name of your choice**

![Alt text](ggggt3.png)


## Step 2: Fill Repository Details

> 1. In the **"Repository name"** box, type **"DK12"**

> 2. In the **"Description"** box, type a short description.

> 3. Select whether your repository will be **"Public or Private"**

> 4. Select Add a README file.

> 4. Click **"Create repository."**

![Alt text](git%20pub.png)


## Step 3 : Stage and Commit Changes

**use of the Git commands - commit, clone, push, and pull**


> **git add** to stage changes, **commit** them with git commit, and push them to the remote repository with git push. This process enabled you to integrate your Docsify documentation into a GitHub repository and manage it under centralised version control

> - **Commit**: The git commit command is used to permanently store the changes made to code. Whenever you make changes to your code that you want to keep, you create a "commit" that contains a brief description of the changes you made. This helps keep track of the project's history.

> - **Push** : The git push command is used to upload the committed changes from your local computer to a remote Git repository. When you make changes to your code and commit them, you need to push those changes to your remote repository so that others can see and access them.



<div style='break-after:always'></div>

```
git add .
```
```
git commit -m "just for understanding"
```
```
git push https://github.com/kavitakeenable/Rashi.git
```



![Alt text](POD77.png)


## Step 4 : Clone the Repository

**Choose the "Clone" option on GitHub to get the repository URL. Copy this URL**


> - **Clone**: The git clone command is used to copy the entire remote Git repository onto your local machine. It's a way to get a complete copy of all files and history from the remote repository onto your system. This is often used when you want to start working on a project that is hosted remotely.


![Alt text](git%20ras.png)


```
 git clone https://github.com/kavitakeenable/Rashi.git
```



![Alt text](pod99.png)



## Step 5 Integration Docsify and GitHub

- To integrate Docsify with GitHub, include the repository name in the URL path. 

```
Podman run -d -p 3000:3000  --name=docsify -v /home/poem/Rashi:/docs:docsify/demo```
```

![Alt text](pod66.png)


## Step 6 Access Account Settings

> **Direct to your account settings. Look for your profile picture or username at the top-right corner and click on it to access your account settings.**
>- Within the account settings, search for a section related to "Tokens," **"Setting"** or **"Developer Settings."**

|   **profile account**       | **Setting**          | 
|---|----|
|![Alt text](git%20to.png)    |![Alt text](git%20to2.png) |


## Create New Token

>- Choose the option to create a new personal access token.

>- Click the button to generate the token.

  ### Personal Access tokens

![Alt text](git%20tok.png)

 ### Generate New token

![Alt text](token.png)
 
### Set Permissions

> Specify what the token can do. Choose permissions like accessing repositories or performing read/write actions.

![Alt text](git%20note.png)

>- Once generated, you'll typically see the token displayed on your screen.
Copy and Store Securely.

![Alt text](git%20acces.png)


>- Copy the token to your clipboard.
Store the token in a safe place, like a password manager or a secure document.


**Similarly you can push when you have to update any code you will push and when you have to take any code from remote server then you will pull**

![Alt text](pod58.png)


<div style='break-after:always'></div>


# 3.Markdown Basic Syntax

## Overview

> Markdown is a plain text formatting language used to create simple and structured documents. It is commonly used for web content, readme files, documentation, email, and various other types of text-based content. Below I'm doing some common Markdown syntax examples and their explanations:

## 1. Headings
> Headings are created using the # symbol, with one # indicating Heading 1 and six # indicating Heading 6.

![Alt text](md7.png)

**output**


![Alt text](md90.png)



## 2. Text Formatting

>![Alt text](md1.png)

**Output**

> Bold Text: **Bold Text** or __Bold Text__


> Italic Text: *Italic Text* or _Italic Text_


> Strikethrough Text: ~~Strikethrough Text~~


## 3. Blockquota 

 To create a blockquote in Markdown, you use the > symbol. Place the > symbol before the text you want to include in the blockquote.

![Alt text](md3.png) 

**Output**

![Alt text](md%205.png)

#  Reference Link:

#### Markdown use the reference link 
     https://www.markdownguide.org/cheat-sheet/

#### GitHub use the reference link 
     https://docs.github.com/en/get-started/quickstart/hello-world

#### Docsify use the reference link 
      https://docsify.js.org/#/

    
