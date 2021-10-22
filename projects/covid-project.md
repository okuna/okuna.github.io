# 491 Covid Project 

## Overview 

The goal of this project was to create an interactive web app replicating the functionality of [UH LumiSight](https://uh.campus.lumisight.com) with the Meteor stack. Our app was created collaboratively in a group of four people and has the following features:

- Users can create an account and log in with a password
- After logging in, users perform the following actions: 
  - A daily Covid symptom check in
  - Log vaccine information and upload a photo of their vaccine card
  - Submit a Covid test result 

The project page along with source code can be found here: https://491-team-9.github.io

## Personal takeaways

This project was my first exposure to the Meteor tech stack, which bundles Node, Mongo, and React running over a socketed connection. Although I had experience with Node and Mongo individually, I had no experience with how Meteor's neat packaging of the components worked. One thing that took some adjustment was that there didn't seem to be a large distinction between server and frontend code. For example, here are the steps that I'd take to implement something like viewing a picture on a user: 

1. Update the data model in the database (ex: User.Picture)
2. Update the the service class in the backend to support the new database operation needed (ex: UserService.GetUserPicture(string userId))
3. Update the backend controller to support a new RESTful API route and link the new route to the new service call (ex: GET user/picture)
4. Update the frontend service to make the new API call (ex: UserService.GetUserPicture()) 
5. Update the data model in the frontend to support the new data (ex: User.Picture)
6. Update the viewmodel to call the frontend service to make the API call
7. Update the View to add UI to call the viewmodel 

In Meteor, these steps are sort of mushed together, and it is no longer clear whether code is running on the front or backend. For instance, it's possible to do call something like `collection.insertOne({ object.. })` from the same file containing view code! 

## Personal contributions

I contributed to the group in the deployment of the app, in helping to manage meetings and check-ins, and in implementing the vaccine card photo upload feature. 

To deploy the app, I had to create a Meteor account, read the documentation, and install Meteor on my machine. This took a few hours due to my unfamiliarity with Meteor and Galaxy hosting. I also assisted with creating a shared team Github account. 

In helping to manage the project, I frequently posted to the team channel and tried to schedule weekly synchronous meetings over Discord. I also did pair programming to help a teammate get the project running on their machine. I also worked with my team to try and establish best coding practices for the project, such as checking out issue branches and merging into a development branch for further testing. 

Implementing the vaccine photo upload feature was my most time-consuming contribution to the project. I had to become familiar with several Node packages including SimeleSchema, Uniforms, and SemanticUI. After a lot of trial and error, I was finally able to get a file upload button to render and accept a file which was then turned into an ObjectURL. 

After getting an ObjectURL representing the selected file, the next challenge was to store the image. My initial approach was to try and store it as a binary Blob in Mongo, but it seemed that SimpleSchema didn't support this data type. Furthermore, I had difficulties trying to send the binary data to the server. I learned that binary data can't easily be sent as a JSON object, which is what Meteor appeared to be sending its requests as. 

My solution was to base64 encode the image as a string and store it in the database in that format. MongoDB has a limit of 16MB per object, so this approach worked for a single vaccine card image. Displaying the image in the frontend was easy, as the `<img>` tag could automatically accept the base64 encoded image as its `src`. 

![img](images/upload-card.png)
*A screenshot of the vaccine card upload UI*

## Conclusion

My first Meteor project was a success and fulfilled all the requirements. If we had more time, I would like to make some optimizations on storing the image data as binary instead of a base64 string. I'm looking forward to becoming more familiar with Meteor in the upcoming Meteor Hackathon.
