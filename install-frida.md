# Install frida server on ndroid Genymotion (check kernel `adb shell getprop ro.product.cpu.abi`)



* **Download last version release `frida-server` for Android**

  ```wget https://github.com/frida/frida/releases/download/12.11.6/frida-server-12.11.6-android-x86.xz``` 
  
  or 
  
  follow this is for other release from frida-server https://github.com/frida/frida/releases



* **After download success, please extrack `frida-server` file using command below**

  ```xz -d frida-server-12.11.4-android-x86.xz```



* **Push `frida-server` file into android genymotion**

  ```adb push frida-server-12.11.4-android-x86 /data/local/tmp/frida-server``` 


* **Give file permission for execute `frida-server` file on android genymotion**

  ```adb shell chmod 755 /data/local/tmp/frida-server``` 
  
  
* **Running `frida-server` using command below**

  ```adb shell /data/local/tmp/frida-server &```
<br><br><br>
* **After all proses working, please check you'r frida client on you'r terminal using command below (first install `frida-tools` on you'r local machine)**
  * **Ubuntu**
  
    ```pip install frida-tools```
  
  * **MacOs**
  
    ```pip install frida-tools```
  
* **after that, running this command for check if it is working**
  
    ```frida-ps -U```
