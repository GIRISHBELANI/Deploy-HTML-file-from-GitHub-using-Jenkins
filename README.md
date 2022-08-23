
# Deploy HTML file from GitHub using Jenkins

1. Create Dockerfile and HTML file in your local computer.


2. Push your files into your Project GitHub Repository using Git.


3. Install Jenkins on your EC2 instance (8080 port allowed)

and paste your Public IP with 8080 port on Chrome
```
http://<your_IP_address>:8080
```
Now, complete the installation steps and login to Jenkins

4. Go to Credentials ---> global ---> Add Credentials ---> Username and Password

Add your GitHub Credentials here.


![](https://github.com/GIRISHBELANI/Deploy-HTML-file-from-GitHub-using-Jenkins/blob/master/1.%20Credentials.png%20.png?raw=true)

![](https://github.com/GIRISHBELANI/Deploy-HTML-file-from-GitHub-using-Jenkins/blob/master/2.%20Add%20GitHub%20Credentials.png?raw=true)


5. Go to Dashboard ---> Create a Job ---> Freestyle Project ---> Ok

6. General ---> Source Code Management ---> Git ---> Paste your repository URL ---> Select your Credentials

![](https://github.com/GIRISHBELANI/Deploy-HTML-file-from-GitHub-using-Jenkins/blob/master/3.%20Source%20Code%20Management.png?raw=true)


Build ---> Execute Shell ---> write build and run commands ---> Save

```
sudo docker build -t newimage .
```
```
sudo docker run -itd -p 80:80 newimage
```

![](https://github.com/GIRISHBELANI/Deploy-HTML-file-from-GitHub-using-Jenkins/blob/master/4.%20Build.png?raw=true)

Click on "Build Now"

![](https://github.com/GIRISHBELANI/Deploy-HTML-file-from-GitHub-using-Jenkins/blob/master/5.%20Build%20Now.png?raw=true)

**Note:** If your build get failed and you are getting an error, then follow below steps
```
sudo: a terminal is required to read the password;
either use the -S option to read from standard input
or configure an askpass helper
sudo: a password is required
```
![](https://github.com/GIRISHBELANI/Deploy-HTML-file-from-GitHub-using-Jenkins/blob/master/6.%20Error.png?raw=true)

7. Go to your Putty ---> 

```
cd /
cd /etc
sudo vi sudoers
```
Add 2 commands after below lines
##### # Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL
```
jenkins    ALL=(ALL:ALL) ALL
jenkins    ALL=(ALL) NOPASSWD: ALL
```
![](https://github.com/GIRISHBELANI/Deploy-HTML-file-from-GitHub-using-Jenkins/blob/master/7.%20Giving%20permission%20to%20jenkins.png?raw=true)

 8. Now restart the jenkins  
 ```
 sudo systemctl restart jenkins
 ```
 and login again

 9. Again try to do "Build Now"

 10. Paste your Public IP on Chrome and check your running website or application 
