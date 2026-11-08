# PROJECT SPIRIT
## Technical Documentation

### . Project Description

Project Spirit is a hands-on AWS cloud engineering project focused on deploying a secure,  available three-tier web application with HTTPS.

The application enables users to submit and retrieve records through a web interface, with data stored in a MySQL database.

### . Technology Stack

| Component | Technology |
|---|---|
| Frontend | HTML, CSS, Vanilla JavaScript |
| Web Server | Apache HTTP Server |
| Backend | Python, Flask |
| Database | MySQL / Amazon RDS |
| Compute | Amazon EC2 |
| Networking | Amazon VPC |
| Load Balancing | Application Load Balancer |
| SSL/TLS | AWS Certificate Manager |
| DNS | Amazon Route 53 |

### . Application Components

**Frontend**

Provides the user interface for submitting and viewing records. Built with HTML, CSS and Vanilla JavaScript.

**Backend**

A Python Flask application exposing REST API endpoints:

- `POST /api/records` – Creates a new record.
- `GET /api/records` – Retrieves saved records.

**Database**

MySQL stores application records in the `records` table.




### . Planned AWS Deployment

The application will be deployed using the following components:

- Amazon VPC with public and private subnets.
- Frontend and backend EC2 instances.
- Internet-facing Application Load Balancer.
- Internal Application Load Balancer.
- Amazon RDS for MySQL.
- AWS Certificate Manager.
- Amazon Route 53.

### . Implementation Progress

| Phase | Description | Status |
|---|---|---|
| 1 | Application Development | Completed locally |
| 2 | IAM USER ADMIN CREATION |
| 3 | VPC and Networking | Pending |
| 4 | Security Configuration | Pending |
| 5 | EC2 Deployment | Pending |
| 6 | RDS Deployment | Pending |
| 7 | Load Balancing | Pending |
| 8 | HTTPS and DNS | Pending |
| 9 | Integration and Testing | Pending |

### . Deployment Evidence

Screenshots, configuration details, architecture diagrams and test results will be added as each implementation phase is completed

###  . CREATING AN IAM USER AND ASSIGNING PRIVILEGES

 An IAM user in AWS is an entity you create to securely control access to your AWS resources, with its own credentials and permissions.

Navigate to AIM > users>create user

<img width="2513" height="924" alt="AdobeExpressPhotos_c1afc46a374f4176b1fd9475c6c2ea4c_CopyEdited" src="https://github.com/user-attachments/assets/2a8a25c0-cfe5-41b0-9c26-ed2e22c9aae0" />

<img width="2526" height="934" alt="AdobeExpressPhotos_f8756325ca6d43ab914ff90e1d582544_CopyEdited" src="https://github.com/user-attachments/assets/7ef6d230-ff35-4050-ab0d-3d47bbcf3c09" />


### . CREATING A VPC

A VPC (Virtual Private Cloud) is a securely isolated section of a cloud provider’s network where you can launch and manage resources like servers and databases within your own private virtual network. 

REGION: EUROPE(STOCKHOLM)

VPC NAME : PROJECT-SPIRIT

Availability zone:

Availability Zones are distinct, physically separated data centers within a cloud region that provide redundancy and high availability by ensuring your applications remain operational even if one zone fails. For this project, two availability zones would be required for fault tolerance and high availability.

AVAILABILITY ZONES : FIRST : eun1-az1 (eu-north-1a) SECOND : eun1-az2 (eu-north-1b)

### SUBNETS
A subnet (subnetwork) is a smaller, logical segment of a network within a VPC that helps organize and control how resources communicate with each other. 

2 PUBLIC FOR COMMUNICATING WITH THE INTERNET 
4 PRIVATE FOR isolating resources APP+ DATABASE from public access for enhanced security.

NAT GATEWAY : In a VPC, a NAT Gateway acts as a bridge that lets private subnet resources like databases initiate outbound connections to the internet while keeping them unreachable from the public internet.



<img width="2522" height="935" alt="AdobeExpressPhotos_a587ba54f24c40f2a4ebba1a6a2f4f3c_CopyEdited" src="https://github.com/user-attachments/assets/26b6bc88-fa09-49f0-96cd-7429b6189657" />


<img width="2543" height="933" alt="AdobeExpressPhotos_f21b029aace743a2b37fdddbe8c681ba_CopyEdited" src="https://github.com/user-attachments/assets/10c33f26-0847-4059-a7d0-5e07077b9c68" />


<img width="2524" height="928" alt="AdobeExpressPhotos_cceac0fcba9242959e477ce9baea6fd4_CopyEdited" src="https://github.com/user-attachments/assets/f7cdd99b-e309-4831-b4f8-b8873cd9b9bd" />


VPC SUCCESSFULLY CREATED

<img width="2531" height="921" alt="AdobeExpressPhotos_1a5b8659a3e8405289a981d1d4e5f30e_CopyEdited" src="https://github.com/user-attachments/assets/ee97baaa-8476-40b7-9eb1-a1cf21637dc4" />



### . CREATING AN S3 BUCKET

An S3 bucket is a cloud storage container in AWS used to store, organize, and manage data such as files, images, and backups securely.

<img width="2535" height="939" alt="AdobeExpressPhotos_df8145b6b2f84f19868a090e5ebb0042_CopyEdited" src="https://github.com/user-attachments/assets/44be9e1b-750c-4c78-be17-547c10a2e0f1" />


<img width="2513" height="931" alt="AdobeExpressPhotos_845ad36272fd4e6292b57a8b30506db3_CopyEdited" src="https://github.com/user-attachments/assets/c7ff4a10-909d-423d-860e-6297435aa7b9" />

<img width="2518" height="928" alt="AdobeExpressPhotos_985039269ebe4d6cb98104f79cd3d400_CopyEdited" src="https://github.com/user-attachments/assets/b26512c4-9d74-4687-81e3-686d5134caef" />

<img width="2519" height="931" alt="AdobeExpressPhotos_7e4f86674ac342e79a0ead96394a9480_CopyEdited" src="https://github.com/user-attachments/assets/3085cf43-866e-4159-bc89-ac5bfb0b19b0" />

<img width="2526" height="916" alt="AdobeExpressPhotos_9e603591578147f0be0e0b0ba9a9f7cb_CopyEdited" src="https://github.com/user-attachments/assets/d815144f-ae5f-4afa-9812-1c306ad2e15e" />


The next step is to upload the file needed for the application and database that was cloned from github

Endeavour to remove (readme.md Documentation.md .gitignore and other files that are not needed by application before uploading to s3)

<img width="2528" height="929" alt="AdobeExpressPhotos_c5e69e361d114e2089683c88992a53c3_CopyEdited" src="https://github.com/user-attachments/assets/7d0004a8-961d-4f9d-97ca-b1e7218a9473" />

<img width="2529" height="925" alt="AdobeExpressPhotos_b07f287246ae4d59a6a35ceed05df45b_CopyEdited" src="https://github.com/user-attachments/assets/529c2309-b79e-4b4b-b9ea-540449de3ff7" />



### .  Create an IAM role to attach to ec2 instance


Go to AIM> ROLES> CREATE ROLE Use case choose EC2 >next > search for (Amazonec2roleforssm)> next name of role(alt-3tier) > create role


<img width="2512" height="938" alt="AdobeExpressPhotos_0c06fbf8887446b69b0499e90da7f0b5_CopyEdited" src="https://github.com/user-attachments/assets/2c9805b1-3b8f-481d-a0d6-e031c7797592" />

   RENAMING SUBNETS FOR EASY ASSIGNMENT
<img width="2512" height="932" alt="AdobeExpressPhotos_1811fdf463b74aa680839836f2848651_CopyEdited" src="https://github.com/user-attachments/assets/6814ed79-4aa6-4538-b28b-9e26e824b244" />


This would make it easier to assign subnets to run both the app and database.

###  . DATABASE
A database is a structured place where information is stored, organized, and managed so it can be easily accessed, updated, and used by applications. For this project, I will be using MYSQL because it has a free tier.


### .CREATING A DATABASE SUBNET GROUP
A DB Subnet Group is a collection of subnets in different Availability Zones that defines where an Amazon RDS database can be deployed within a VPC.

Navigate to RDS> Subnet Groups> Create DB Subnet Groups> fill up the necessary info

<img width="2512" height="934" alt="AdobeExpressPhotos_15fa32c6e34e4737bbb733f128ace6d1_CopyEdited" src="https://github.com/user-attachments/assets/ea7356c1-730d-48f8-9d02-cce79aa5ae93" />

<img width="2523" height="946" alt="AdobeExpressPhotos_e724e4b3252e4d3db39985d53fe3b023_CopyEdited" src="https://github.com/user-attachments/assets/e2fcd82d-d508-4781-9836-40d3d37e51e9" />

<img width="2517" height="938" alt="AdobeExpressPhotos_0191cef54e9c476886b0665ad01f3b64_CopyEdited" src="https://github.com/user-attachments/assets/8f5dabfd-0962-4a35-b337-135ee451c222" />

Subnet Groups successfully created

<img width="2518" height="932" alt="AdobeExpressPhotos_f16ae79820fc49e98cb4d06019eb95d2_CopyEdited" src="https://github.com/user-attachments/assets/4506d040-161e-427f-8a2d-b882a6907d5b" />

<img width="2519" height="936" alt="AdobeExpressPhotos_1a2e66c73fe347ed9cc053922f037a5f_CopyEdited" src="https://github.com/user-attachments/assets/75e16fb0-4b7b-4958-8a54-28af3aabfa02" />


### . CREATE SECURITY GROUPS(DATABASE)
A Security Group acts like a virtual firewall that controls what kind of network traffic is allowed to reach your cloud resources and what can leave them. 
Search EC2> Security Groups> create SG > Fill up the necessary details.

The rules are set so that only the resources running in the VPC can communicate with the database. This SG is for the database.

<img width="2515" height="942" alt="AdobeExpressPhotos_6cfdafa785d74e868244f40588234f27_CopyEdited" src="https://github.com/user-attachments/assets/d5774ea1-787a-4626-8fe2-f62ccb23d6d6" />

<img width="2545" height="951" alt="AdobeExpressPhotos_c9731381ca10436789ec5926aa4a1bb3_CopyEdited" src="https://github.com/user-attachments/assets/154046f5-588c-4902-8f90-e5c395f9426b" />


### CREATING DATABASE
For this project, I will be using MYSQL because it has a free tier. Search RDS> Databases> Create Database>choose MYSQL> Fill up the necessary details.

<img width="2528" height="936" alt="AdobeExpressPhotos_10cf4cce91fd4125bdf455a4f50a2b28_CopyEdited" src="https://github.com/user-attachments/assets/8a84cba4-a2da-4e69-89df-c10442b014c2" />

<img width="2531" height="944" alt="AdobeExpressPhotos_65448ee642734269a1f7d58c737893e6_CopyEdited" src="https://github.com/user-attachments/assets/e3806527-7fca-47aa-81c3-5a777134a335" />

<img width="2516" height="940" alt="AdobeExpressPhotos_4dbe27f17b50472d8dadf2d193bf06aa_CopyEdited" src="https://github.com/user-attachments/assets/6fed0ca3-e803-44cc-bfc2-c53cfaa688a9" />

<img width="2520" height="930" alt="AdobeExpressPhotos_f3f8abd97bc34a16b48c11ce73edc07b_CopyEdited" src="https://github.com/user-attachments/assets/9ef33a19-e69d-412d-9fa2-65b1567ac0d2" />

<img width="2519" height="934" alt="AdobeExpressPhotos_e8d594a58d7f41cc92f2a06572ed9369_CopyEdited" src="https://github.com/user-attachments/assets/76b6a9c8-7902-4d72-95e2-19b11b37de7b" />

<img width="2523" height="924" alt="AdobeExpressPhotos_91b5e91198a04ef3b5c8235070bacbba_CopyEdited" src="https://github.com/user-attachments/assets/7db2472d-7af4-4abb-8d4e-793018859858" />



### .  CREATING SECURITY GROUP (Public facing load balancer)

A Security Group for an Internet-Facing Load Balancer allows public web traffic (HTTP/HTTPS) from the internet while controlling which internal servers the traffic can reach.

EC2> SECURITY GROUP> CREATE SECURITY GROUP >

<img width="2540" height="926" alt="AdobeExpressPhotos_cec013febcce41e3b27e9b40ffe9b211_CopyEdited" src="https://github.com/user-attachments/assets/76c9d9d7-7cc9-4a52-b4ed-df42d0b71468" />

### . CREATING SECURITY GROUP (WEB SERVER)

The web server is protected from direct internet access, only accepts traffic from the load balancer and internal VPC resources, and uses the VPC CIDR range to define which internal IPs are allowed.

<img width="2512" height="937" alt="AdobeExpressPhotos_9a15e63480d84c0ab2e7b7d11debc53d_CopyEdited" src="https://github.com/user-attachments/assets/d879b5fe-d540-411e-a204-a66ea6697e03" />



### . CREATING SECURITY GROUP(APPLICATION 
This Application Security Group allows traffic on port 4000 only from the Load Balancer, keeping the app servers protected from direct internet access.

<img width="2518" height="929" alt="AdobeExpressPhotos_570af90ba83643e3ae0a3d89a76d67ba_CopyEdited" src="https://github.com/user-attachments/assets/5f85341c-3198-4609-869c-2c87304c8376" />

### .  CREATING SG (INTERNAL LOAD BALANCER) 

An Internal Load Balancer is a load balancer that distributes traffic only within a private network (VPC) between internal servers, and is not accessible from the public internet. A Security Group (SG) for an Internal Load Balancer allows traffic only from specific internal resources like application servers within the VPC, and blocks access from the public internet.

<img width="2530" height="946" alt="AdobeExpressPhotos_c2460b66e79b4532a468463687fbfce0_CopyEdited" src="https://github.com/user-attachments/assets/295dd26a-43e4-42e7-bcc8-5350375c0326" />


UPDATING DATABASE.PY  FILE

After creating the necessary security groups, the next step is to update the databse.py file with the database username, password and endpoint. This would be done by navigating to the file location and opening the file with visual studio code. This would enable the application to connect to the database. After updating the file with vs code, it has to be updated in the S3 bucket as well.
This would be done by navigating to the location where the file located on S3 bucket and update using drag and drop, then click upload.

<img width="2528" height="928" alt="AdobeExpressPhotos_38f83769eba4421eb6da855909b7ec1a_CopyEdited" src="https://github.com/user-attachments/assets/b4bb5512-3639-4068-b0de-3d3ca2a29a5b" />

### . LAUNCHING AN EC2 INSTANCE

An EC2 instance is a virtual server in AWS that you can use to run applications, host websites, or perform computing tasks just like a physical computer.
Navigate to EC2 > instance> launch instances > FILL the necessary details

<img width="2531" height="937" alt="AdobeExpressPhotos_6fd18b2782d3479083d021510367ca59_CopyEdited" src="https://github.com/user-attachments/assets/6bd56418-9651-4700-807e-a71296ea205a" />


<img width="2531" height="937" alt="AdobeExpressPhotos_939525ce0e7a41bd8c257ac9e5cf5d32_CopyEdited" src="https://github.com/user-attachments/assets/8b1d4faf-ddb6-4536-a636-5123f36d2c2d" />


<img width="2540" height="941" alt="AdobeExpressPhotos_ac34db1fb0804a5699c241a5ed7f7586_CopyEdited" src="https://github.com/user-attachments/assets/4ed427e3-b8b2-4095-9555-79c99e16dd14" />


<img width="2524" height="934" alt="AdobeExpressPhotos_bb470808a77c4ce4a8a87237026fef04_CopyEdited" src="https://github.com/user-attachments/assets/f6844f87-fa69-4900-8e0e-8b6508e7d999" />


<img width="2522" height="607" alt="AdobeExpressPhotos_c42b1591814f415faa60d9161e405970_CopyEdited" src="https://github.com/user-attachments/assets/42734ca7-da92-4867-821f-65b1f0f8206a" />


<img width="2536" height="932" alt="AdobeExpressPhotos_ec79dcc5d24e4cf59aa599f3d823e14b_CopyEdited" src="https://github.com/user-attachments/assets/d50189f2-14fe-40a0-960a-8baa14d6c1b6" />



<img width="2522" height="926" alt="AdobeExpressPhotos_bc1d04cfb7334397ac5e0063a6a8206c_CopyEdited" src="https://github.com/user-attachments/assets/fefb53c1-9b39-4d14-a420-f0c702581e18" />

Instance is up and running


<img width="2527" height="928" alt="AdobeExpressPhotos_8d4f1de6f9c24509a8aa0c2485ade9b9_CopyEdited" src="https://github.com/user-attachments/assets/12e00272-f941-4f18-b39c-b7f04b70b947" />


<img width="2529" height="926" alt="AdobeExpressPhotos_ec4b53af080d452397f5be34d21653dc_CopyEdited" src="https://github.com/user-attachments/assets/2e594ab6-a30f-4cf5-b1ef-83e8aadb42b0" />

### CONNECTING TO INSTANCE

Sudo su to run as the root user.

<img width="2545" height="1088" alt="AdobeExpressPhotos_dd8699a5966840d3a7ac30dd16018bf9_CopyEdited" src="https://github.com/user-attachments/assets/acfb0e0e-1518-47f9-8890-a49af3dbf956" />

### . INSTALLING AND CONNECTING MYSQL DATABASE

As the root user, the next step is to install mysql.

Follsow the steps on github link below to install mysql. 
https://github.com/Harmonygrams/amazon-linux-2023-mysql-installation-guide/blob/main/ReadMe.md

<img width="2544" height="971" alt="AdobeExpressPhotos_bb7e3a139baf4d3d9e0cf89b2ed7db9a_CopyEdited" src="https://github.com/user-attachments/assets/680b5883-5368-42cc-868c-0c757955bbf1" />


<img width="2545" height="987" alt="AdobeExpressPhotos_c827a2301dbd487aaa64fb466e5fa337_CopyEdited" src="https://github.com/user-attachments/assets/db1c6349-acfe-49f9-ab6b-262ab9858e00" />

<img width="2545" height="649" alt="AdobeExpressPhotos_0349f9616a714f579eb020d8735d30f1_CopyEdited" src="https://github.com/user-attachments/assets/d47cca59-490a-406b-9657-16798152a9a4" />

###  After installation , the next step is to connect to the database.

<img width="2545" height="523" alt="AdobeExpressPhotos_e2485e598d374143a0204c0ea205a243_CopyEdited" src="https://github.com/user-attachments/assets/f0ad7051-2909-43d2-a24c-591860d5865a" />

### . CREATING A DATABASE ON INSTANCE CLI

COMMANDS :  CREATE DATABASE project_spirit;

CREATE TABLE IF NOT EXISTS records (
    id INT NOT NULL AUTO_INCREMENT,
    description VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (id)
);


The above command created a database called project_spirit and created a table called records. 

<img width="2545" height="279" alt="AdobeExpressPhotos_03bd20582aba48d5a043ec00b59887c2_CopyEdited" src="https://github.com/user-attachments/assets/219e3b64-71f3-4cf6-a5a5-6ff25808f921" />


<img width="2542" height="824" alt="AdobeExpressPhotos_19de095b0e3a43b6a94f27e7a277cf23_CopyEdited" src="https://github.com/user-attachments/assets/416f5666-999f-493f-aa1b-37d4821a64a8" />

<img width="2545" height="323" alt="AdobeExpressPhotos_b29941171cb54117a26e8034b7e0f49b_CopyEdited" src="https://github.com/user-attachments/assets/96562a67-0a11-4935-a34c-847cbd1d646c" />


### INSTALLING AND CONFIGURING APPLICATION

installing the app requirments : dnf install -y python3-pip

create a directory for the backend Application : mkdir -p /opt/project-spirit/backend

on s3 the backend code is located at :   s3://projectspirit-bucket/PROJECT-SPIRIT-main/PROJECT-SPIRIT-main/backend/

Download files : aws s3 cp s3://projectspirit-bucket/PROJECT-SPIRIT-main/PROJECT-SPIRIT-main/backend/ /opt/project-spirit/backend/ --recursive
 
Create a virtual environment to install dependencies: python3 -m venv /opt/project-spirit/venv

Activate : source /opt/project-spirit/venv/bin/activate..

Install dependencies : pip install -r /opt/project-spirit/backend/requirements.txt


<img width="2544" height="985" alt="AdobeExpressPhotos_411ad5a283cf4fc3b10ec471406d0279_CopyEdited" src="https://github.com/user-attachments/assets/1e6e82c5-7d29-4458-bbf7-cddc75f1c74e" />

<img width="2545" height="978" alt="AdobeExpressPhotos_a4b7310e3abf4938acdd9a2a851c43b9_CopyEdited" src="https://github.com/user-attachments/assets/3cd02533-d5c7-453b-aeb9-8836cc8b1304" />

<img width="2545" height="345" alt="AdobeExpressPhotos_65c147fea3d14e44ada80a56d856f0ac_CopyEdited" src="https://github.com/user-attachments/assets/186d8e62-2d87-40c7-b7f2-9d50ea63c80f" />

COMMANDS 

UPADATED THE database.py with the details from RDS and created a .env file for creds. 

Test the database connection

cd /opt/project-spirit/backend

python -c 'from database import get_db_connection; conn = get_db_connection(); print("Database connection successful"); conn.close()'


python -m py_compile /opt/project-spirit/backend/app.py

pip install gunicorn

gunicorn --version

Start the backend application

cd /opt/project-spirit/backend

gunicorn --workers 2 --bind 0.0.0.0:5000 app:app

curl http://127.0.0.1:5000/health


<img width="2543" height="325" alt="AdobeExpressPhotos_ff4ed99bd3dc493abe34a5cf367ea294_CopyEdited" src="https://github.com/user-attachments/assets/a63df020-9d13-4085-a654-db07d76ea297" />

<img width="2545" height="511" alt="AdobeExpressPhotos_c2828d599dad4fae8ff46cd0216dba8e_CopyEdited" src="https://github.com/user-attachments/assets/ee9884a0-f2da-44a7-8370-c1959a4651a2" />

We'll now create a systemd service so Gunicorn can run independently

Create the service file

nano /etc/systemd/system/project-spirit.service


[Unit]
Description=Project Spirit Flask Backend
After=network.target

[Service]
User=root
WorkingDirectory=/opt/project-spirit/backend
Environment="PATH=/opt/project-spirit/venv/bin"
ExecStart=/opt/project-spirit/venv/bin/gunicorn --workers 2 --bind 0.0.0.0:5000 app:app
Restart=always

[Install]
WantedBy=multi-user.target


Then reload : systemctl daemon-reload

Enable the service : systemctl enable project-spirit

systemctl start project-spirit

systemctl status project-spirit

<img width="2545" height="956" alt="AdobeExpressPhotos_21f9f646425846f28cbae8c4c8c0b986_CopyEdited" src="https://github.com/user-attachments/assets/20774aaa-8f51-4a74-abf0-52621427e5d1" />


### CREATING INTERNAL LOAD BALANCER

Target GROUPS

Target groups are sets of registered servers or instances that receive traffic from a load balancer based on defined rules.

Navigate to EC2 > Target Groups> Create Target Groups> instances > Fill necessary input> next > choose instance > include as pending below> create target group


<img width="2532" height="932" alt="AdobeExpressPhotos_c6243c3f619c46fc875c460c047e6666_CopyEdited" src="https://github.com/user-attachments/assets/0636047e-dc54-4379-a8ac-e690ef03baf5" />

<img width="2544" height="941" alt="AdobeExpressPhotos_76b5744569b24ac398c9ae3936e2ca84_CopyEdited" src="https://github.com/user-attachments/assets/9f564c2b-24c7-4bb1-8cc4-756b638bffb3" />

<img width="2523" height="936" alt="AdobeExpressPhotos_fc036294ec6c41c2baba7c2955d157cb_CopyEdited" src="https://github.com/user-attachments/assets/ddb09a46-5d2b-44d3-a45c-c8dfe09fe735" />

<img width="2526" height="936" alt="AdobeExpressPhotos_b7944577a40843a98c64040fb3ca18b5_CopyEdited" src="https://github.com/user-attachments/assets/714a8318-1019-4c77-8fb6-b6bb3e6b7790" />

<img width="2543" height="1027" alt="AdobeExpressPhotos_b3e07e0e9a0e4c9f8af62d8cc50d69a0_CopyEdited" src="https://github.com/user-attachments/assets/b04f5396-c6ef-4c69-b1a7-89d3ddd7c927" />


### LOAD BALANCER

A load balancer is a network device or service that distributes incoming traffic across multiple servers to ensure reliability, scalability, and optimal performance.

Navigate to EC2> Load Balancers> Create Load Balancer> Create Application Load Balancer > internal (for this project) > Fill in necessary fields

<img width="2536" height="942" alt="AdobeExpressPhotos_84f5341e573e4f74abb61430957d24c6_CopyEdited" src="https://github.com/user-attachments/assets/83c34854-b815-47db-9fe6-8da03309dda6" />

<img width="2529" height="930" alt="AdobeExpressPhotos_6a57be97307e4e118b2e2f8da57893d2_CopyEdited" src="https://github.com/user-attachments/assets/45d0332a-c0db-47f0-b967-827d41344dfd" />

<img width="2528" height="940" alt="AdobeExpressPhotos_dd08cb1e29bc4fda925c41edf0901e7f_CopyEdited" src="https://github.com/user-attachments/assets/c3fe3286-38ae-4f8b-a001-66088bde173d" />



Before moving to the next step which is to create the web-tier, Open the internal ALB's target group and check the backend EC2 health status

<img width="2538" height="930" alt="AdobeExpressPhotos_3aa3e160d4ce495492d68c4e093c9c4e_CopyEdited" src="https://github.com/user-attachments/assets/da47f0e0-d5ee-4512-8be6-a5ed2b73070a" />

This screenshot showed that the cause is a security group rule blocking communication between the internal ALB and  backend EC2.

### .  TROUBLESHOOTING AND FIXING

Check the backend EC2 security group

<img width="2538" height="923" alt="AdobeExpressPhotos_e544964839a54c139a0e8c7a8a03e2e6_CopyEdited" src="https://github.com/user-attachments/assets/0d2597f6-b682-4900-9800-609acf6d2464" />

The screenshot shows that the backend security group is allowing traffic on the wrong port (4000) instead of port 5000 which Gunicorn is listening on , and requests will come from the  internal Load Balancer's security group .

FIX:  Add  new inbound rule with the right port. 

<img width="2524" height="919" alt="AdobeExpressPhotos_c578e76e560e4ff3a7db85b4e107e79c_CopyEdited" src="https://github.com/user-attachments/assets/e0354350-2a88-45ea-9ca1-10675da3c4bd" />


The below screenshot shows that the internal ALB can reach the backend EC2.

<img width="2523" height="937" alt="AdobeExpressPhotos_07ece2f06ece444dae58bab812fcc421_CopyEdited" src="https://github.com/user-attachments/assets/f751edb1-a750-45fe-b692-59ce3d7de4eb" />

### . CREATING WEB TIER

Navigate to EC2 > instances > Launch Instance > Fill the necessary space

<img width="2533" height="933" alt="AdobeExpressPhotos_86c0b9ec656f4e27a416f47aeb923973_CopyEdited" src="https://github.com/user-attachments/assets/559e4623-c107-467b-97fb-f3123d40b292" />

<img width="2542" height="931" alt="AdobeExpressPhotos_6cc8588af52349519c6c7b446892f730_CopyEdited" src="https://github.com/user-attachments/assets/8d46c717-f034-44f9-9f73-36ce2e438879" />


<img width="2545" height="931" alt="AdobeExpressPhotos_e45c82b89ba84085b1a8c0950ebfe7eb_CopyEdited" src="https://github.com/user-attachments/assets/278214c0-6984-4ff2-807d-3f3a12ce9193" />

<img width="2545" height="938" alt="AdobeExpressPhotos_c503dad8ff0841548d41e859ba9c8434_CopyEdited" src="https://github.com/user-attachments/assets/d926c81f-cc3b-4fe5-ad75-33a0ed6576cd" />


<img width="2542" height="938" alt="AdobeExpressPhotos_a8290c07835e42589baad5239beb05b1_CopyEdited" src="https://github.com/user-attachments/assets/3c31667c-1ebb-4079-bbb4-0e323d23b61e" />

<img width="2545" height="908" alt="AdobeExpressPhotos_567e075f8a724f4bbfdd041c3d0c89ea_CopyEdited" src="https://github.com/user-attachments/assets/156b00af-c268-4509-829a-405cdeb5d87c" />


After creating the web Tier instance, the next step is to connect through SSM and run as ec2-user. Then run the following commands.

sudo dnf install -y httpd

sudo systemctl enable --now httpd

<img width="2545" height="976" alt="AdobeExpressPhotos_b6c32475585e43f9a17c7de56f17fe31_CopyEdited" src="https://github.com/user-attachments/assets/ba231f9d-441c-4fe8-8451-250d5367a6cc" />

<img width="2545" height="987" alt="AdobeExpressPhotos_0e3039a0e2294a48ae609ac0259e0062_CopyEdited" src="https://github.com/user-attachments/assets/f63138df-fa86-4af6-b4f9-d6a387c32b15" />


CLI VERSION :aws --version

 S3 bucket access : aws s3 ls s3://projectspirit-bucket/

<img width="1985" height="176" alt="AdobeExpressPhotos_1c2e4f85347d44ca888842a580d549fd_CopyEdited" src="https://github.com/user-attachments/assets/b4baa1a5-a325-4245-8428-613230fcc186" />

inspect bucket content : aws s3 ls s3://projectspirit-bucket/PROJECT-SPIRIT-main/PROJECT-SPIRIT-main/frontend/ --recursive

create destination folder : mkdir -p /var/www/html/css /var/www/html/js

Copy contents to created apache web  directory :  aws s3 cp s3://projectspirit-bucket/PROJECT-SPIRIT-main/PROJECT-SPIRIT-main/frontend/ /var/www/html/ --recursive


Confirm copied contents : ls -R /var/www/html/

<img width="2545" height="506" alt="AdobeExpressPhotos_f1eaf5eb2bba4144ad3bfb0ccb69558f_CopyEdited" src="https://github.com/user-attachments/assets/fb04d634-1de5-4e87-9024-e568e064bb01" />

Testing Apache locally : curl -I http://localhost

<img width="1012" height="307" alt="AdobeExpressPhotos_759eaa4ca4e6478cb56f5312a88dccdc_CopyEdited" src="https://github.com/user-attachments/assets/d1eb59a3-f8c0-4302-8951-210e02155378" />


configure Apache as a reverse proxy

The browser will send requests to the Web Tier, and Apache will forward /api/records to the Internal ALB, which routes them to the Flask backend

1 enable Apache's reverse-proxy modules so it can forward API requests to the backend : 

sudo sed -i 's/^#LoadModule proxy_module/LoadModule proxy_module/' /etc/httpd/conf.modules.d/00-proxy.conf

sudo sed -i 's/^#LoadModule proxy_http_module/LoadModule proxy_http_module/' /etc/httpd/conf.modules.d/00-proxy.conf

grep -E 'LoadModule proxy(_http)?_module' /etc/httpd/conf.modules.d/00-proxy.conf

create Apache's reverse-proxy configuration  

sudo nano /etc/httpd/conf.d/project-spirit-proxy.conf

Paste the code into the file 

ProxyPass /api/ http://internal-PROJECT-APPLICATION-LB-1167768252.eu-north-1.elb.amazonaws.com/api/
ProxyPassReverse /api/ http://internal-PROJECT-APPLICATION-LB-1167768252.eu-north-1.elb.amazonaws.com/api/

This tells Apache to forward /api/ requests to the Internal ALB, preserving the API path.

<img width="2288" height="358" alt="AdobeExpressPhotos_9014d6bfdf634ea89c5666c71a2e8e0c_CopyEdited" src="https://github.com/user-attachments/assets/e6c20df2-abf2-4f1e-9b3b-f75ba4d1d112" />

Validate configuration : sudo apachectl configtest
responds with syntax ok 

Restart Apache : sudo systemctl restart httpd

status check : sudo systemctl status httpd


<img width="1908" height="947" alt="AdobeExpressPhotos_681ee07b17e2430da9e97e775e091b88_CopyEdited" src="https://github.com/user-attachments/assets/d8e76ef0-a6d8-43c1-975b-9463ce0bf8f4" />




















