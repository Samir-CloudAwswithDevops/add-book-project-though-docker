<img width="1920" height="1080" alt="Screenshot (357)" src="https://github.com/user-attachments/assets/caf26d2e-58fb-48e7-a1aa-0d8d681c511a" />
<img width="1920" height="1080" alt="Screenshot (358)" src="https://github.com/user-attachments/assets/c1883e37-923c-4ac9-b88b-68c118123cf7" />

####Book-project-deployment-though docker ####

###👉  Create an Amazon RDS Instance  👉 Click “Create database”

                                      👉 Choose a database engine -MySQL , full configuration
                                            
                                      👉 Choose version - MySQL 8.0.x
                                       
                                      👉 Choose a Template- Free tier (if eligible) , Dev/Test(Production)
        
                                      👉 Choose a Master username - admin 
  
                                      👉 Choose a Master password - self managed - Set a strong password.Confirm the password

                                      👉 Configure Instance Size - db t3.micro

                                      👉 Connectivity - vpc(default) , subnet group , security group

                                      👉 Choose a accessible - public
                                      
                                      👉 Choose Create Database 

 
 #👉 create ec2- docker-c7xi.large ,procced with keypair ,attach IAM role(ec2-fullaccess), security group

  
 #👉 connect ec2    #👉 sudo su -

                    #👉 yum install docker -y

                    #👉 systemctl start docker

                    #👉 systemctl enable docker

                    #👉 yum install git -y

                    #👉 yum install mariadb105-server

                    #👉 git clone https://github.com/Samir-CloudAwswithDevops/add-book-project-though-docker.git

                    #👉 ls cd backend -inside #👉 vi test.sql inside # change rds <endpoint> password :wq!

                    #👉 cd backend inside -docker build -t backend .

                    #👉 cd backend inside - MySQL -h <rds endponit> -u admin -P < test.sql
                    passwotrd - Samir
    
                    # show books 

                   #👉 cd backend inside - docker run -dt -p 84:80 backend .
 
                   #👉 cd backend inside - docker ps then  ## docker images

                   ## copy public ip:84 hit browser show output hello

                  #👉 cd client/src/pages/config.js ## change publicip:84

                  #👉 cd client inside - docker build -t frontend

                  #👉 cd client inside - docker run -dt -p 82:80 frontend 

                  #👉 cd client inside - docker ps then docker images

                  #👉 #### copy publicip:82 hit browser  ### 🎉 Deployment Complete!
 
