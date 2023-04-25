# SOMETHING

-ensure /posts is working
- restart instances - build AMI's for Nodejs server and Mongod 
- janete app/db ami
- sg rules for app instance and db instance
- app ami config: port 3000, port 80, reverse proxy
- db ami config: port 27017, port 22

- no need to access db, we only config aws, no need to shh in
- mongod.cong changed to 0.0.0.0
- 
