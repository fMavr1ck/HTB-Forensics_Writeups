![alt text](image.png)

Fist ssh into server 
![alt text](image-1.png)

After succeccfully entering into machine via ssh we are currently in root directory. After trying ls command on root directory or any other directory nothing is listing here. something is strange
![alt text](image-2.png)

Nothing showed useful as ls is not showing any thing ... 
as the chall says that the rootkit is hiding something so as it will manipulate the shared library .

Using ldd tool list the dynamic dependancies

![alt text](image-3.png)

Found one suspicious library.
After looking at the lib it is hooking events ..
The next step is to how can we remove this library from loading ..

![alt text](image-4.png)
We discover a suspicious library. Further inspection reveals that this library hooks filesystem-related functions such as readdir and fopen, commonly used by rootkits to hide files and directories:
Simple technique is to rename the libraray ..

![alt text](image-5.png)

As here we can see that the ls was loading the malicious one that was named as hook.so but now after renaming it it is not loading the shared library.
Now as we have sucessfully prevented the malicious preload from ruunig now list file in root got nothing then after traversing diff directoreis got the flag in the var one.

![alt text](image-6.png)

BINGO CHALL SOLVED ..!!



