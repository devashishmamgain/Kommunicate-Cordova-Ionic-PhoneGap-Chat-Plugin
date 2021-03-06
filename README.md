# Kommunicate-Cordova-Ionic-PhoneGap-Chat-Plugin
Kommunicate plugin for Ionic/Phonegap/Cordova

## Installation
You can add the plugin using the below command:
 
`cordova plugin add https://github.com/Kommunicate-io/Kommunicate-Cordova-Ionic-PhoneGap-Chat-Plugin.git`

For ionic, use the below command:

`ionic cordova plugin add https://github.com/Kommunicate-io/Kommunicate-Cordova-Ionic-PhoneGap-Chat-Plugin.git`

## Authentication

To authenticate a user you need to create a user object and then pass it to the `login` function:

```
    var kmUser = {
        'userId' : this.userId,   //Replace it with the userId of the logged in user
        'password' : this.password,  //Put password here
        'authenticationTypeId' : 1,
        'applicationId' : '22823b4a764f9944ad7913ddb3e43cae1',  //replace "applozic-sample-app" with Application Key from     Applozic Dashboard
        'deviceApnsType' : 0    //Set 0 for Development and 1 for Distribution (Release)
    };
```

Then call the `login` function from the plugin:

```
kommunicate.login(kmUser, function(response) {
        //login success
    }, function(response) {
       //login failed
    });
  }
```

You can check if the user is logged in or not by calling the `isLoggedIn()` function from the plugin:

```
 kommunicate.isLoggedIn((response) => {
      if(response === "true"){
        //The user is logged in, you can directly launch the chat here 
      }else{
        //User is not logged in, maybe you need to call login function here
      }
    });
```

## Launching chat screen

You can open the chat screen by calling the below function:

```
kommunicate.launchConversation((response) => {
          //conversation launched successfully
        }, (response) => {
         //conversation launch failed
        });
```

## Launching individual chat thread

You can open an individual chat thread by calling the below function and passing the `groupId`:

```
let convObj = {
        'groupId' : groupId, //pass the groupId here
        'takeOrder' : true //skip chat list on back press, pass false if you want to show chat list on back press
      };
      
kommunicate.launchParticularConversation(convObj, function(response) {
        //Conversation launched successfully
      }, function(response) {
        //Conversation launch failed
      });
```

## Starting a new Conversation

You can start a new conversation by using the below function:

```
 let convInfo = {
      'agentId':'reytum@live.com',
      'botId': 'Hotel-Booking-Assistant'
     };
     
  kommunicate.startNewConversation(convInfo, (response) => {
      
       console.log("Kommunicate create conversation successfull : " + response);
    },(response) => {
      console.log("Kommunicate create conversation failed : " + response);
    });
 ```
 
## Logging out the user

You can logout the user from Kommunicate using the below function:

```
kommunicate.logout(function(response){
       //logout successfull
    }, function(response){
      //logout failed
    });
```

For sample code you can refer to our sample app made in ionic3 https://github.com/Kommunicate-io/Kommunicate-Ionic-Cordova-Sample-App
