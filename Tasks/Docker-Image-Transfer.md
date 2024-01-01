# Docker Image Transfer Documentation

## Summary:
 I recently worked on a task that involved transferring a custom Docker image tagged as `news:devops` from our App Server 1 to App Server 3 within our Stratos DC environment. The goal was to make this image readily available for our testing team's use on App Server 3.

## Steps Taken:

### Step a: Saving the Docker image as an archive on App Server 1:
1. **Saving the image as a tar file:**
   - Firstly, I ran the command:
     ```bash
     docker save -o mydockerimage.tar news:devops
     ```
   - This created a neat and organized tar file named `mydockerimage.tar`, encapsulating our `news:devops` Docker image.



### Step b: Transferring the image archive to App Server 3:
1. **Sending the tar file to App Server 3:**
   - To transfer this image over to App Server 3, I used the `scp` command:
     ```bash
     scp mydockerimage.tar banner@stapp03:/home/banner
     ```
   - This safely delivered `mydockerimage.tar` to the remote server App Server 3 in the `/home/banner` directory.

### Step c: Loading the image archive on App Server 3:
1. **Loading the Docker image from the tar file:**
   - Lastly, on App Server 3, I loaded the image with the command:
     ```bash
     docker load < mydockerimage.tar
     ```
   - This command loaded the `news:devops` Docker image from the `mydockerimage.tar` file on App Server 3.
![image1](./images/apache1.png)