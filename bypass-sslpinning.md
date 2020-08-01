# Tutorial for bypass SSL Pinning

* **Script (filename `sslbypass.js`)**

  ```
  /* 
     Universal Android SSL Pinning Bypass
     by Mattia Vinci and Maurizio Agazzini 

     $ frida -U -f org.package.name -l universal-ssl-check-bypass.js --no-pause

      https://techblog.mediaservice.net/2018/11/universal-android-ssl-check-bypass-2/
  */

  Java.perform(function() {

      var array_list = Java.use("java.util.ArrayList");
      var ApiClient = Java.use('com.android.org.conscrypt.TrustManagerImpl');

      ApiClient.checkTrustedRecursive.implementation = function(a1, a2, a3, a4, a5, a6) {
          // console.log('Bypassing SSL Pinning');
          var k = array_list.$new();
          return k;
      }

  }, 0);
  ```
  
  if successful it will appear like this
  
  ```
  macos@rootbakar ~ % frida -U -f com.twitter.android -l sslbypass.js --no-pause
     ____
    / _  |   Frida 12.11.6 - A world-class dynamic instrumentation toolkit
   | (_| |
    > _  |   Commands:
   /_/ |_|       help      -> Displays the help system
   . . . .       object?   -> Display information about 'object'
   . . . .       exit/quit -> Exit
   . . . .
   . . . .   More info at https://www.frida.re/docs/home/
  Spawned `com.twitter.android`. Resuming main thread!                    
  [SSL PINNING TWITTER::com.twitter.android]->  
  ```
  
  <img src=http://cdn-file.progress28.com/ssl-pinning.png width=500px height=300px />    
      
  
* **Bypass command for running using frida**

  ```frida -U -f com.twitter.android -l sslbypass.js --no-pause```
  
<br><br><br>  
  
**NOTE:**<br>
Please using android `API 24` version `7.0` and install `OPEN GAPSS`<br>
<img src=http://cdn-file.progress28.com/genymotion.png width=500px height=300px /> 
