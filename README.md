# team42: Player One - The Player's Game Rating Platform
This project is an React application on game rating and sharing. To use this app, please follow the following steps.
## Installing and running locally
    Important: Please do not refresh on the main page for many time, we have a very limited cloudinary quota
1. clone git repo:
    ```
    git clone https://github.com/csc309-winter-2020/team42.git
    ```
2. go to project top level directory:
    ```
    cd team42/
    ```
3. Build client and start the server using 
    ```
    npm local-start
    ```
4. The app should be available at ```localhost:5000```, have fun. (We will refer to ```localhost:5000/``` as root from now on)

## Viewing the deployed app
The app is deployed via heroku, and it is available at [```http://player-1.herokuapp.com/```](http://player-1.herokuapp.com/). (as before, we will refer to ```http://player-1.herokuapp.com/``` as our root)

# Overview of functionalities

## Main Page
Once you open up root page, you can see the main page for our site. It is consist of the following
- A navigation bar at the top, with game categories for users to choose games to browse as well as login and sign up buttons. (also a search bar implemented in phase 2)
    - The "featured" tab contains five hottest games,
    - The remaining five tabs are five different genres, and each tab should contain five hottest games in that genre. 
    - **Search Bar**: You can type in the box to filter the search results, or click the small downward arrow at the right end to expand the selection list and select a game from there. Once you select your game of interest, you should be redirected to the game's page. 
- Five pictures of 5 featured games shown as Carousel Slides.The Carousel sides is set to be auto play with stop of 5 seconds for each picture. Notice that these five games are exactly the same as those ones in the featured tab. Our design intention is that hottest games at the time of openning up the page should be more eye-grasping and thus making the user stay on our website longer. : )
- Below the large carousel slides, is the section for showing games from different genres. Each genre has a short description associated with it, and five hottest games' pictures in that genre shown in the small carousel slides. 


## Default Available Login Credentials (SIGN IN)
You can login to the app by clicking the `SIGNIN` button at the top right of the main page. 
There are the following three login credentials hardcoded into our app currently, they are
 - For user: username `user` with password `user`, it is intended to be a normal player's user account. 
 - For superuser: username `superuser` with password `superuser`. A super user represents a professional agency, could be game rating company or game makers, etc.
 - For admin: username `admin` with password `admin`; This is the account of the admin of the site. Unlike the previous two types of users, an admin is allowed to modify other users' data, including but not limited to changing password, adding user, deleting user. 

## SIGN UP
You can sign yourself up as a normal user by clicking the sign up button to the right end of the top navigation bar. Once you have successfully signed up for our webapp, you should immediately notice that you are signed in, and you can no longer see the sign in/ sign up buttons. In stead, you will see your username displayed at the top right. 



## Account Page For User/ Superuser
An user (superuser or user) has access to his/her own account page after successful login. An account page is where a user can view/edit profile and view recent activities.
To go to the account page, please click `My Account` in the dropdown menu displayed when you hover your mouse over the username at the top right corner.

In the account page, an user is currently able to:
- edit his/her handle name by clicking the pencil icon next to it
- view the total number of his/her reviews and likes received for them
- view his/her personal bio
- add a new tag to describe himself/herself or his/her favorite games
- view a list of recently liked games and go to that game page by clicking the link
- view a list of recent reviews and go to that games page by clicking the link

## Manage Page For Admin
After successful login, an admin user can access the Manege page by clicking `Manage` in the dropdown menu displayed when
hovering mouse over the admin user name. *Due to the hardcoded nature of this app, this management interface is not connected to anything else, and is for the purpose of demonstrating layout.*

In the Admin page, he/she can 
- Manage Users
    - Add a new user by providing Username and Password
    - View all the current user in the system. 
    - Override an existing user's password by entering a new password in the `NewPassword` field and click on the `UPDATE` button, after which an alert will show, prompting the username of the user and the new password. 

- Manage Games 
    - Add a new game by entering the name of the game and description of a game and click `ADD GAME`
    - Remove a game by clicking `REMOVE` button in the game entry.
    

## Game Page
Anyone can view the game page without signing in into the app, however, for he/she to make a comment/long comment depending on the type of user that he/she is, logging in is required. *There are in total 26 hardcoded games for our app at initial state.*

- **For User:** A general user can add comment for games, press like/dislike buttons for a game, and press like/dislike/funny buttons for comments and long comments.
    - The user can like/ dislike the game. The user can only either dislike or like the game, i.e. he/she can't both like the game and dislike the game. Also, the user can't like or dislike the game more than once. Notice that if a user has previously liked the game, then when he/she press dislike button, the number of dislikes is incremented, and his like for the game is automatically cancelled. This also holds when the user has previously disliked the game, and wish to press like now. 
    - The user can press like/dislike/funny for long comments and short comments. The like and dislike work exactly the same as those for the game, which is described above. The funny button is independent, and intentioanlly designed such that one can press it as many times as he want. (so maybe some comment is really funny but not quite related to the game, then the user saw it can click funny a few times. )
    - The user can add his/her new comment by typing a new comment message in the text input box and then hitting the `SUBMIT` button below. The new comment will be added to the *top* of existing comment list. 
    - The user can also modify the the comment that he/she left by entering a new comment and press the button below. You can see that the old comment being replaced by the new one. (when a comment is modified, the like/dislike/funny counts are reset to zero, since a modification in comment could make the comment have a entirely different meaning and we think it would be wierd if it still has likes/dislikes/funny from the previous version.)
    - Note: The current policy for these short comments is that it has to be longer than 30 characters (informative) and less than 500 characters (not too long). Also, the submitted comment will replace all the newline 'returns' with spaces. We did this because it is possible that some malicious user type a lot of returns in some comment and this might ruin the user experience for others.

- **For Superuser:** A super user can do **anything** that a normal user can do, and in addition to that, he/she can add long comments for the game. By clicking the `want to share your review?` expansion panel, the super user can see an interface for entering a new long comment. As opposed to short comments, long comments have to be at least 500 characters long. Also, long comments represent professional agencies's viewpoint on the game, which we expect to be professional. Hence, we do not allow professinal users to modify the contents of the long comment. 

- **For Admin:** We think admin should be limited to his/her own job and should not use the admin account for personal opinion, for example, like writing a comment. Hence, the only thing that a admin is allowed to do on a game page is to delete comments. The admin can do so by clicking the ```delete``` button associated with the comment that he/she wants to delete. 

