---
layout: page
title: About
permalink: /about/
---

# Ryan Hubbard Project 1 Portfolio


## Initial installation of React-native and npm.
The first task of the project was to correctly setup a react-native development environment so that we could begin working on the project when we gained access to the code base. First step was to install the correct version of node js, this is a simple process as node js provides a simple wizard installer that also allows for the installation of a npm, which is a package manager for node js. ![nodejs](/assets/nodejswebsite.png) Once node js and npm are installed you can use npm to install react-native this was done using this command npm i -g react-native-cli. The next step was to setup the windows environment variables and paths. This was to make sure that windows could find the locations of the various applications that were needed to build the project. Using this [tutorial](https://medium.com/@prasadjivane/react-native-environment-setup-on-windows-10-47a3b5e833b9#:~:text=Open%20the%20folder%20in%20visual%20studio%20code%20and%20type%20npm%20install.&text=The%20easiest%20way%20to%20run,List%20of%20devices%20connected) and some help from my team members I configured the windows environment variables correctly so that the react-native project could be built and run on the system.
![environmentvariables](/assets/environmentvariables.png)



## Firebase console

During the first two weeks when we did not have access to the code base of the project I tried to make use of the time by making sure our public facing parts of the project on firebase were up 
to scratch. Using the login provided by our lecturer I logged into the firebase console to try familiarise myself with the console so that I would be able to use it effectively in the future. I inspected the database on firebase to look at how the data was structured. Below is a screenshot from the database showing a message stored in the database. I also found that the usernames and passwords from user accounts were not being encrypted at all. While the app does not currently have any active users it still raised an ethical concern as the app was live on the google play store. This was something that would need to be fixed before any actual release of the app.

![Database](/assets/MicrosoftTeams-image.png)

## Gitlab vs Github.
For the first couple weeks of the semester we could not work on the project at all because the current build of the app was stuck on the polytech’s Gitlab servers which happened to be down. After we finally got access to the gitlab repository our first course of action was to migrate the repository to Github where we decided it would be safer than on the Gitlab servers. We also decided that making use of the projects feature of Github would be ideal for our sprint based approach we were taking. We could make a Github project for each sprint and assign tasks to various team members keeping track of them with a Kanban board layout.

![SprintProject](/assets/sprintportfolio.png)

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

![forgotpassword](/assets/forgotpassword.png)

During this I ran into some issues due to my lack of familiarity with React project file structures. The file locations that were given in the tutorial did not match up with the file structure of the project I was working on. This was a good learning opportunity because it made me spend time looking at the locations of files and their contents. This helped me learn the purpose of these files so that when I needed to make changes to them in the future I would have a basic understanding of where they were so my workflow would be improved.  

Once the forgot password screen was created and the relevant navigation was implemented, I added a button below the login/signup buttons that would navigate the users to the forgot password screen.

The next step in the process was where I ran into a problem, the tutorial then asked me to edit the config file of firebase. According to the tutorial there should be a firebase.js file in the config folder of the React project. However in our project this did not exist, it was apparent that the way our firebase implementation was different to how it was done in the tutorial. Unfortunately this was as far as I got in my attempt to implement a password reset feature, this taught me that my understanding of React was not great and was compounded by the fact we were building features into an app that already existed. This is a challenge that I have not faced before as throughout this degree we have primarily worked on projects individually and even when we work on group projects we generally start from scratch. The challenge that working on an existing project presents is that without great documentation it takes more time to understand how various components of a project work. This adds complexity to any task that is being completed as you have to first learn how a system works before you can start to edit and build upon that system.

## Installation errors on new machine during lockdown
![stuck](/assets/stuck.png)

After having to move to a different machine during the lockdown I have run into many errors when trying to run the project. The one above was giving me issues because it could not verify I had accepted the license agreements for the android SDKs. After some googling I used android studio to download and switch to a different android SDK and I accepted the licenses correctly during setup. This fixed that error and moved me on to a new error.

![errorSDK](/assets/errorSDK.png)

This error occured because the computer could not find the path to my android SDK, by manually setting the path of my ANDROID_HOME system variable in windows environment variables. i was able to fix this error before running into another one.

This is a new error i have not seen before when trying to run a react-native project. My attempts to fix it have so far failed. I have reinstalled node_modules, and restarted my pc. I have run gradle clean on the android folder in the project.

After discussing with my project group members, I discovered that I was using an incorrect version of nodejs and react-native. My version numbers did not match the version numbers being used by my team members and this was causing errors when i tried to run the project. Once I had found the correct version numbers from my team members I reinstalled nodejs and npm and the project ran fine without any issues.

## Splash Screen

After having trouble trying to implement some more advanced features on the app, after a sprint retrospective I decided that I would try to implement something simple like a splash screen for the app. To do this I followed this [tutorial](https://medium.com/@appstud/add-a-splash-screen-to-a-react-native-app-810492e773f9).
The first error I encountered when trying to implement the splash screen was that I didn’t correctly name the splash icons that i downloaded from the tutorial. This was causing errors when trying to launch the project because of the ‘@’ sign in the file names. After reading the error message and re-reading the tutorial i discovered that i had missed a step when following the tutorial and subsequently renamed them without the ‘@’ signs this resolved the error.

![splashicon](/assets/wrongnamesplash.png)


After following the tutorial some more and setting up the splash screen for an android app which all went well until i tried to edit the app.js file to make the app hide the splash screen. At this point the app would run but it would be stuck on the splashscreen and never hide and continue to open the app. This was because the tutorial used a hook method that I didn’t know how to implement into the app, as the tutorial assumed that this was a fresh project that only I was working on.

![hookmethod](/assets/hookmethod.png)

After some googling I found a potential work around by using an in built function in nodejs to hide the splash screen when the app is ready to launch. However this also did not work.

![component](/assets/component.png)


## Splash screen troubleshooting

After my first attempt at implementing a splash screen failed, I spent some time trying to troubleshoot it. This mainly involved googling the issue and trying to implement the various fixes that were suggested by React users. The first of the fixes that was suggested was running a gradle clean on the project folder, the intention of this command is to clean up any old files that remain from previous builds of the project. This was the output from running the clean command, it failed due to a missing file. 

![gradleclean](/assets/gradleclean.png)

I then ran npm install to make sure that I had all the correct modules.
After running npm install on the project I tried to run gradle clean again this time it completed successfully, however it did not fix my issue with the app being stuck on the splash screen. Nonetheless this was still a useful command to know how to use as it appeared to be a common fix for various issues with react-native apps.

![gradlecleanwork](/assets/gradlecleanworking.png)

From my googling I found many people with a similar issue however most of their solutions seemed to be issues with various packages not running correctly and most of them had already successfully implemented a splash screen and it subsequently broke when they updated their packages. These were not very helpful to me as my splash screen has never worked in the first place. However I found that reading through the posts was helpful as it helped me gain background knowledge of React and gave me ways I could potentially use to debug the project in the future.


## Timeline text only post 

Timeline Text Only Post

In an attempt to get something to actually work I followed a tutorial from a blog post app that I would hopefully be able to adapt to implement text based timeline posts on the app. I followed this [tutorial](https://code.tutsplus.com/tutorials/creating-a-blogging-app-using-react-part-3-add-display-post--cms-28685)
Making sure to use Git branching so that I could edit the project without fear of potentially breaking the master branch. For this attempt of resolving an issue I decided that I would try to follow the tutorial closely and ignore what was already in the project. I did this in the hope that I would be able to get the feature working and then work with my teammates to correctly implement it into the current working app.

The first step in the tutorial was to install a node module with npm that would allow the app to validate user credentials upon login and then create a session for that user.

npm install express-session --save

Once installed I edited the App.js file to start implementing the module I had just installed. I followed the tutorial and implemented the following lines of code.

![tutorialimage](/assets/tutorialforportfolio.png)


The next step in the tutorial was where our project differed from the one in the tutorial as the file structure was different. So in order to follow the tutorial accurately I created the file structure that was in the tutorial and added the home.html file that was given by the tutorial. I hoped doing it this way would actually get the feature to work even if it didn’t make any sense with the current state of the app.  I then continued to edit the app.js file to add routes to the html file that was added in the previous step. This was not something that I had seen in our project before but I added it anyway in the hopes that it would work.

![htmlfileadd](/assets/htmlfilestructure.png)

![route](/assets/routemethod.png)

Next I edited the home.html file I had created to implement various React native libraries that would be needed for creating text posts on the page. After I did this I decided to try and run the app to see if my changes had broken it yet, to my surprise the app compiled and ran on my virtual device. However upon logging in to the app nothing had changed. This told me that the changes I had implemented were not actually being run. This was because the tutorial was based upon a different React project so when I tried to follow the tutorial with our team’s project the code I added wasn’t being run. At this point I decided to stop following the tutorial as it wasn’t feasible to try and refactor our app to be able to use the code from the tutorial.


## Team Communication

At the beginning of the semester we made use of our in class time as a team to communicate with each other regarding technical issues that we were facing. This gave us a great platform to discuss and solve problems that arose when we were working on the project. 

![standup](/assets/standups.png)

Unfortunately as the country went into COVID-19 related lockdown this was unable to continue. However as a team we found other ways to communicate using various online services. Our main method of communication was to make use of microsoft teams, we could use the message board type features of this to post about what we were working on or use it to organise standup meetings each week. We could also use this to work collaboratively on fixing errors that were encountered, below is a screenshot from the back-end issues section of our Teams group. While this was not ideal compared to being able to meet face to face it was a good compromise given the situation we were in. 

![backendteams](/assets/backendteams.png)


## Zoom Conferencing

For our stand-up meeting we made use of Zoom video conferencing which has many features that make it pretty close to being as good as the real thing. The primary feature that makes zoom good to use for stand-up meetings is its screen share feature. With this we were able to share specific applications to our team members which made it much easier to solve problems together rather than having to manually screenshot various issues. This made what would have been a tedious process quite, quick and efficient.

![zoommeetings](/assets/zoommeeting.png)
