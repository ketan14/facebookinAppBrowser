facebookinAppBrowser
====================

/*
Facebook Sharing and like option with InAppbrowser

From facebook Developer account I find out to share the application for iOS and android as below link.
*/

   https://www.facebook.com/dialog/feed?
     app_id=[your_appID]
     &display=popup&caption=An%20example%20caption
     &link=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fdialogs%2F
     &redirect_uri=https://developers.facebook.com/tools/explorer
     
     
     from this URL we can make the directly response for the phonegap application with  InAppbrowswer as below.
     
     
     var ref = window.open("https://www.facebook.com/dialog/feed?app_id=205805252877602&link=http://www.example.com/&picture=http://fbrell.com/f8.jpg&name='Myapp'&caption=&description='Shar%20with%20New%20this'&redirect_uri=https://www.facebook.com/", '_blank', 'location=yes');

  
    ref.addEventListener('loadstart', function(event) {
                         
                         });
    ref.addEventListener('loadstop', function(event) {
                         console.log(event.type + ' - ' + event.url);
                         var post_id = event.url.split("post_id=")[1];
                         var cancel_url = event.url.split("#")[0];
                         if(post_id != undefined){
                         setTimeout(function() {
                                    
                                    ref.close();
                                    
                                    }, 5000);
                         }
                         if(cancel_url != undefined && cancel_url == your_redirect_uri){
                         setTimeout(function() {
                                    ref.close();
                                    }, 1000);
                         }
                         });
    ref.addEventListener('exit', function(event) {
                         
                         });
And also we have the addEventListner for the ref URL
