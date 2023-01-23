# I HOSTED A WEB APPLICATION ON AWS USING LIFT AND SHIFT STRATEGY

The "lift and shift" strategy, also known as "rehosting," is a method of migrating an existing on-premises application to the cloud, without making any significant changes to the application architecture or code. The goal of lift and shift is to move the application with minimal disruption and to take advantage of the scalability, availability, and cost benefits of the cloud.

- **So I will guide you on the steps to help you in this project**

## HOST A WEB APPLICATION ON AWS USING LIFT & SHIFT STRATEGY


In the first project we setup a multi-tier web application stack locally.
In this project we will host and run the application on AWS cloud for production using **Lift & shift Strategy**

- Learn how to run application workload on AWS using life & shift strategy


**AWS Services used**

- EC2 instances will be used for Tomcat, RabbitMQ, Mmecached, Mysql

- Elastic load balancer - Nginx LB replacement

- Autoscaling

- S3/EFS storage

- Route 53

- AWS Certificate Manager


### Objective

- We want a flexible infracture

- No upfront payment

- Iaac - automation

- Modernise our infractruture effectively


We will be shifting our stack in the previous project

Once we have our workload in AWS running, our architecture will look like this:

Users will access our website using a url and that url will be pointed to an endpoint, this entry which will be mentioned in GoDaddy DNS or any other domain registrar you may have, the app will use the endpoint to connect to loadbalancer by using HTTPS. The Certificate for HTTPS encryptIon will be mentioned in AWS ACMS. Users will access Loadbalancer endpoint. LB will be in a security group and we will only allow HTTPS traffic and the App Loadbalancer will route request to tomcat instances. Apache tomcat service will be running on some set of Ec2 instances and will be managed by autoscaling group.
These instances capacity will be scaled out or scaled in. The EC2 instances where tomcat is running will be a separate security group and only allow traffic only from Loadbalancer on port 8080.
You know our app sits on tomcat instance and our app need backend servers such as Mysql, Memcached, RabbitMQ. The backend server IP address will be mentioned in route53 private DNS zone. So tomcat instances will access the backedend servers with the name which will be mentioned in route53 private DNS...this backend EC2 instances which are running RabbitMQ, Mysql, Memcached will be in a separated security group.


#### Flow of execution

- Login to AWS account

- Create key pairs

- create security group

- Launch instances with user data (bash scripts)

- Update IP to name mapping in route53

- Build application from source code

- Upload to s3 bucket

- from S3 bucket download artifact to Tomcat EC2 instance

- Setup ELB with HTTPS (Cert from amazon certificate manager)

- Map ELB endpoint to website name in Godaddy DNS and 

- Verify

- Build autoscaling group for Tomcat instances


##### Detailed execution steps will be added Soon!

