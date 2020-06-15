---
layout: page
title: About
permalink: /about/
---
## Initial installation of React-native and npm.
The first task of the project was to correctly setup a react-native development environment so that we could begin working on the project when we gained access to the code base. First step was to install the correct version of node js, this is a simple process as node js provides a simple wizard installer that also allows for the installation of a npm, which is a package manager for node js. Once node js and npm are installed you can use npm to install react-native this was done using this command npm i -g react-native-cli. The next step was to setup the windows environment variables and paths. This was to make sure that windows could find the locations of the various applications that were needed to build the project. Using this [tutorial](https://medium.com/@prasadjivane/react-native-environment-setup-on-windows-10-47a3b5e833b9#:~:text=Open%20the%20folder%20in%20visual%20studio%20code%20and%20type%20npm%20install.&text=The%20easiest%20way%20to%20run,List%20of%20devices%20connected) and some help from my team members I configured the windows environment variables correctly so that the react-native project could be built and run on the system.
.


## Firebase console

During the first two weeks when we did not have access to the code base of the project I tried to make use of the time by making sure our public facing parts of the project on firebase were up 
to scratch. Using the login provided by our lecturer I logged into the firebase console to try familiarise myself with the console so that I would be able to use it effectively in the future. I inspected the database on firebase to look at how the data was structured. Below is a screenshot from the database showing a message stored in the database. I also found that the usernames and passwords from user accounts were not being encrypted at all. While the app does not currently have any active users it still raised an ethical concern as the app was live on the google play store. This was something that would need to be fixed before any actual release of the app.

## Gitlab vs Github.
For the first couple weeks of the semester we could not work on the project at all because the current build of the app was stuck on the polytech’s Gitlab servers which happened to be down. After we finally got access to the gitlab repository our first course of action was to migrate the repository to Github where we decided it would be safer than on the Gitlab servers. We also decided that making use of the projects feature of Github would be ideal for our sprint based approach we were taking. We could make a Github project for each sprint and assign tasks to various team members keeping track of them with a Kanban board layout.


## Resolving issues with the project from gitlab.

Unfortunately when we gained access to the code base on gitlab and transferred it to github it did not immediately work when we tried to build it on our computers. At first we thought it was an issue with mismatched versions of node/react-native but even when we made sure our versions matched the ones from the project it did not work. Eventually thanks to our team member Aisea we found a fix for our problem. The reason the project would not build was an error in some regular expressions in the \node_modules\metro-config\src\defaults\blacklist.js file. This was fixed by updating the file with this code snippet.

var sharedBlacklist = [
/node_modules[\/\\]react[\/\\]dist[\/\\].*/,
/website\/node_modules\/.*/,
/heapCapture\/bundle\.js/,
/.*\/__tests__\/.*/
];

Once this fix was implemented we were able to build the project and inspect the app on our phones so that we could begin development on it.


## Password Reset

The first feature I attempted to implement was the addition of a password reset, this could be done with the use of firebase which has a password reset feature that will handle the emailing of users. This allows developers to have this feature without needing to have access to their own mail server. In order to implement this feature I will be following this [tutorial](https://heartbeat.fritz.ai/how-to-implement-forgot-password-feature-in-react-native-and-firebase-app-890b572d9759 ) for react-native.


The first step to implement a password reset feature was to add a link to a forgot password screen from the signup screen of our app. For this I needed to create a forgot password screen that users could click on to begin the password reset process. In this [commit](https://github.com/tawaab1/enabling-love/commit/27a86678fba0bb514aefdceb3defd4ce3e57188c) to our github repo I added a forgot password screen and the navigation that were required to access this screen. 

During this I ran into some issues due to my lack of familiarity with React project file structures. The file locations that were given in the tutorial did not match up with the file structure of the project I was working on. This was a good learning opportunity because it made me spend time looking at the locations of files and their contents. This helped me learn the purpose of these files so that when I needed to make changes to them in the future I would have a basic understanding of where they were so my workflow would be improved.  

Once the forgot password screen was created and the relevant navigation was implemented, I added a button below the login/signup buttons that would navigate the users to the forgot password screen.

The next step in the process was where I ran into a problem, the tutorial then asked me to edit the config file of firebase. According to the tutorial there should be a firebase.js file in the config folder of the React project. However in our project this did not exist, it was apparent that the way our firebase implementation was different to how it was done in the tutorial. Unfortunately this was as far as I got in my attempt to implement a password reset feature, this taught me that my understanding of React was not great and was compounded by the fact we were building features into an app that already existed. This is a challenge that I have not faced before as throughout this degree we have primarily worked on projects individually and even when we work on group projects we generally start from scratch. The challenge that working on an existing project presents is that without great documentation it takes more time to understand how various components of a project work. This adds complexity to any task that is being completed as you have to first learn how a system works before you can start to edit and build upon that system.

