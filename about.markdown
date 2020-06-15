---
layout: page
title: About
permalink: /about/
---
## Initial installation of React-native and npm.
The first task of the project was to correctly setup a react-native development environment so that we could begin working on the project when we gained access to the code base. First step was to install the correct version of node js, this is a simple process as node js provides a simple wizard installer that also allows for the installation of a npm, which is a package manager for node js. Once node js and npm are installed you can use npm to install react-native this was done using this command npm i -g react-native-cli. The next step was to setup the windows environment variables and paths. This was to make sure that windows could find the locations of the various applications that were needed to build the project. Using this tutorial and some help from my team members I configured the windows environment variables correctly so that the react-native project could be built and run on the system.
https://medium.com/@prasadjivane/react-native-environment-setup-on-windows-10-47a3b5e833b9#:~:text=Open%20the%20folder%20in%20visual%20studio%20code%20and%20type%20npm%20install.&text=The%20easiest%20way%20to%20run,List%20of%20devices%20connected.


## Firebase console

During the first two weeks when we did not have access to the code base of the project I tried to make use of the time by making sure our public facing parts of the project on firebase were up 
to scratch. Using the login provided by our lecturer I logged into the firebase console to try familiarise myself with the console so that I would be able to use it effectively in the future. I inspected the database on firebase to look at how the data was structured. Below is a screenshot from the database showing a message stored in the database. I also found that the usernames and passwords from user accounts were not being encrypted at all. While the app does not currently have any active users it still raised an ethical concern as the app was live on the google play store. This was something that would need to be fixed before any actual release of the app.
