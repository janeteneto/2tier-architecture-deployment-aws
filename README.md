**- We are going to use use two virtual macines using AWS instances, one will have the app, and the other will have the database that we want to access to fill the an app page called `/posts`

1. Create AWS instance and connect in a Git terminal through SSH (there is a separate README for the steps, they are the same)

2. We need to have access to the `app` file that is on the `tech221_virtualisation file`, se we use the command `scp` to secure, copy and paste the file in our App Instance. In **another terminal, for your local machine**, run command:
````
scp -i "tech221.pem" -r /c/Users/user/tech221_virtualisation/app ubuntu@ec2-54-246-130-94.eu-west-1.compute.amazonaws.com:/home/ubuntu
````
- It should start copying the files to the instance
- `/c/Users/user/tech221_virtualisation/app` - is the path to where your app file is
- `ubuntu@ec2-54-246-130-94.eu-west-1.compute.amazonaws.com:/home/ubuntu` - is the instance where you want to paste the file. You can find this on the `Connect > SSH Client` page on your instance

- Now, we will mannually install what we need:
1. Run `sudo apt-get install python-software-properties` to install python dependencies

2. 
