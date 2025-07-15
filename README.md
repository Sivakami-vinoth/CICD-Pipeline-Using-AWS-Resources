# CICD-Pipeline-Using-AWS-Resources

**Problem Statement: **

You are assigned to create a software development life cycle for an application your company has created. The company wants you to use AWS for the infrastructure part and AWS Developer tools for the pipeline part. 

**Tasks to be performed: **

1.	Create a website in any language of your choice and push the code into GitHub 
2.	Migrate your GitHub repository into the AWS CodeCommit repository 
3.	Create two CodeDeploy deployments (for the QA stage and the Production stage) with an EC2 deployment group into which you can push the code from the CodeCommit repository 
4.	Using AWS CodePipeline, create a software development life cycle: 
a.	The source is the CodeCommit repository. 
b.	The code will be pushed into the deployment created in CodeDeploy. 
c.	There should be two stages in deployment, the QA stage and the Production stage 
d.	Only when the QA stage is successful, the Production stage should execute. 
5.	Create a third stage where the same website is pushed into an Elastic Beanstalk environment
---------------------------------------------------------------------------------------------------------------------

**Step:1 Create a CodeCommit Repository**

**Login to your AWS manage console**

**Goto-> Services-> Developer Tools-> CodeCommit**

<img width="602" height="389" alt="image" src="https://github.com/user-attachments/assets/236c118e-ff12-40db-8d3f-8aa4064db0f2" />

**Click on Create Repository**

<img width="602" height="186" alt="image" src="https://github.com/user-attachments/assets/f01340fa-629f-410c-9198-21487494dc6d" />

**Enter the Repository name and click on Create**

<img width="565" height="427" alt="image" src="https://github.com/user-attachments/assets/960f8f0f-2b09-4efb-9d0f-eede6ff4481f" />

**CodeCommit Repository created successfully**

<img width="602" height="109" alt="image" src="https://github.com/user-attachments/assets/6553b026-359e-441c-9d2e-bde41e4cb719" />

<img width="602" height="287" alt="image" src="https://github.com/user-attachments/assets/ceaf993a-6786-427f-a5e7-9447348baaf7" />


**Step:2 Create an IAM user with Administrator Acccess**

**Open the IAM services from AWS Management Console**

**Click on Add users**

<img width="602" height="197" alt="image" src="https://github.com/user-attachments/assets/6fa2672e-27df-4716-a9ac-2afb2ffd0c27" />

**Enter the user name and select the option ‘provide user access to the AWS Management Console’. Also Select ‘Iwant to create an IAM user**

**Select Auto-generated password and click Next**

<img width="622" height="252" alt="image" src="https://github.com/user-attachments/assets/3b98e4b1-b052-463b-953b-d7924c2d1b71" />

<img width="602" height="215" alt="image" src="https://github.com/user-attachments/assets/14508246-4bbe-4f9c-8bea-15bd1a10e7a2" />

**Click on Create group and create a user group ‘myusergroup’**

**Select the ‘AdministratorAccess’**

**Finally review and create the user**

<img width="602" height="225" alt="image" src="https://github.com/user-attachments/assets/124e96b8-c1bd-4a50-95fa-1e484d9435ae" />

**Download the password and save it for future use**

<img width="602" height="244" alt="image" src="https://github.com/user-attachments/assets/bb40a00e-2b92-4f7a-a205-ec2f5487dd05" />

**User created successfully**

<img width="602" height="183" alt="image" src="https://github.com/user-attachments/assets/c2282f47-f625-436d-9178-46897724644f" />

**Open the IAM user created and Click on Security credentials**

<img width="602" height="258" alt="image" src="https://github.com/user-attachments/assets/52afcb0e-8065-4708-9337-9eb53bb69ef1" />

**Move to HTTPS Git credentials for AWS CodeCommit and click on Generate credentials**

<img width="602" height="150" alt="image" src="https://github.com/user-attachments/assets/77989c62-0dd7-4d15-8359-4e0e6ea47160" />

**Download the credentials and save it for future use**

<img width="490" height="368" alt="image" src="https://github.com/user-attachments/assets/a7c0cef2-38c3-460b-a21b-770866c12698" />

**Step:3 Create an EC2 Instance**

**Login to AWS Management console using the IAM user created**

**Open the EC2 Dashboard and create an EC2 Instance**

<img width="602" height="203" alt="image" src="https://github.com/user-attachments/assets/c3e2be5f-4de8-464e-8e7d-a0fa6fa4a3c8" />

<img width="602" height="107" alt="image" src="https://github.com/user-attachments/assets/a967648b-b42b-4915-84f9-f9e8c60f4702" />

**Connect to the EC2 Instance and run->sudo apt update**

<img width="602" height="110" alt="image" src="https://github.com/user-attachments/assets/6ecd603a-2405-465b-ae44-323bcee1309c" />

**Step:4 Copy the content from the Github to a local repository**

**Open the Github account and copy the HTTPS url**

<img width="602" height="279" alt="image" src="https://github.com/user-attachments/assets/5823d35c-7c15-46ff-9fd0-b0e9d26e61fe" />

**Run the command ->git clone –mirror https://github.com/Sivakami-vinoth/aws-devops-pipeline-project.git aws-devops (will copy the contents from github to the local repo aws-devops)**

<img width="602" height="89" alt="image" src="https://github.com/user-attachments/assets/63a408b9-ed86-433f-b773-038c33aa3921" />

<img width="602" height="64" alt="image" src="https://github.com/user-attachments/assets/f6ef5dea-3913-405b-bbe3-80d2f383de98" />

**Step:5 Push the contents to the CodeCommit Repository**

**Open the CodeCommit and open the repository created**

**Copy the https url of the repository**

<img width="602" height="255" alt="image" src="https://github.com/user-attachments/assets/b0220381-a98a-46e7-9494-22303fbc3943" />

**Run Commans-> git push https://git-codecommit.us-east-1.amazonaws.com/v1/repos/my-repo**

**Enter the AWS CodeCommit username and password genereted while creating the IAM user**

<img width="602" height="133" alt="image" src="https://github.com/user-attachments/assets/75ce0f30-dd3b-4f75-8a98-c3bb7d00e76d" />

**Step:6 Check for the Github repository contents in the CodeCommit Repository**

<img width="602" height="140" alt="image" src="https://github.com/user-attachments/assets/770c00f7-f8fa-4912-b929-3054d41ecff0" />

<img width="602" height="245" alt="image" src="https://github.com/user-attachments/assets/3b6e8c69-9060-401d-9c37-94ac2af8aeb5" />

**Successfully imported the Github Repository contents to the CodeCommit Repository**

**Step:7 Create an IAM role with permissions policies**

**AmazonEC2RoleforAWSCodeDeploy**

**AmazonSSMManagedInstanceCore**

<img width="602" height="242" alt="image" src="https://github.com/user-attachments/assets/89c5de1c-3c9b-455f-a30c-76b00df3b082" />

<img width="602" height="317" alt="image" src="https://github.com/user-attachments/assets/98a178c8-bd51-43bd-b618-bcb6bd612b6b" />

<img width="602" height="215" alt="image" src="https://github.com/user-attachments/assets/d6ceb51b-1985-4cea-a2fa-adbcf580940d" />

<img width="602" height="328" alt="image" src="https://github.com/user-attachments/assets/5fc48704-b8e8-48f5-b8ec-ba02691ee2bc" />

<img width="602" height="170" alt="image" src="https://github.com/user-attachments/assets/2459e0c5-c603-4b62-b959-68300594433e" />

<img width="602" height="175" alt="image" src="https://github.com/user-attachments/assets/73f2c24e-7a31-47ad-abb8-7bfe82e86700" />

**Step:8 Create an EC2 Instance with the IAM Role Created to deploy the application**

<img width="602" height="292" alt="image" src="https://github.com/user-attachments/assets/fdcfb0bd-5029-4b7a-b2b8-7c329272d70b" />

<img width="602" height="267" alt="image" src="https://github.com/user-attachments/assets/4dd3feb3-0b0b-46c8-9a3b-40ba0701101f" />

**Step:9 Connect to the EC2 Instance and run the following commands**

<pre>
sudo apt update
sudo apt install ruby
sudo apt install wget -y
cd /home/ubuntu
wget https://aws-codedeploy-us-east-2.s3.us-east-2.amazonaws.com/latest/install
sudo chmod +x. /install
sudo chmod +x ./install
sudo ./install auto
sudo service codedeploy-agent status
</pre>


<img width="602" height="182" alt="image" src="https://github.com/user-attachments/assets/ffa5969f-c697-46cd-baf1-6f30edaf5e3d" />

**Step:10 Create a CodeDeploy Application with the compute platform as EC2**

<img width="602" height="215" alt="image" src="https://github.com/user-attachments/assets/7e07caee-64c0-4826-adb8-329659629a31" />

<img width="602" height="402" alt="image" src="https://github.com/user-attachments/assets/651a9ae8-1547-4b57-b542-063e0235105a" />

<img width="602" height="213" alt="image" src="https://github.com/user-attachments/assets/582220e4-469e-4a78-9089-1892b0f61d24" />

**Step:11 Select the deployment group with the created EC2 Instances**

<img width="602" height="124" alt="image" src="https://github.com/user-attachments/assets/a01d1b0a-98d6-4dde-bf21-2e7d27a04edc" />

<img width="602" height="318" alt="image" src="https://github.com/user-attachments/assets/77b1db09-72ba-44eb-8662-5be95f7b784f" />

<img width="602" height="210" alt="image" src="https://github.com/user-attachments/assets/8051c0d8-7c67-489c-852c-b1d248ac9d32" />

<img width="602" height="247" alt="image" src="https://github.com/user-attachments/assets/9d4a4704-871b-468e-99ee-136e133f4e7a" />

<img width="602" height="264" alt="image" src="https://github.com/user-attachments/assets/98e5b6e4-77a0-4c28-9bbd-01ea712796da" />

<img width="602" height="294" alt="image" src="https://github.com/user-attachments/assets/ed71c0bc-1516-4409-8fa7-7a76b52a68f9" />

<img width="602" height="317" alt="image" src="https://github.com/user-attachments/assets/f31f4640-03a8-4817-b514-557e45de636f" />

<img width="602" height="371" alt="image" src="https://github.com/user-attachments/assets/ff9442fd-ad21-4fd1-b8c5-a3407eb2dd3f" />

<img width="602" height="159" alt="image" src="https://github.com/user-attachments/assets/7f216fd7-2741-40b7-8eae-ad6b781320f4" />

<img width="602" height="191" alt="image" src="https://github.com/user-attachments/assets/62243de4-db7a-4831-9538-2b56991d33e4" />

<img width="602" height="413" alt="image" src="https://github.com/user-attachments/assets/2bd44467-cb36-4d3a-ac94-9c54f44657b9" />

<img width="602" height="242" alt="image" src="https://github.com/user-attachments/assets/e462054d-711b-4385-8ed8-a4aa77ce9fee" />

<img width="602" height="384" alt="image" src="https://github.com/user-attachments/assets/4f3ddc94-c439-4c24-8f02-032121158a89" />

<img width="602" height="282" alt="image" src="https://github.com/user-attachments/assets/3ee454a5-4e0a-437c-918c-ec21c4453258" />

**Step:12 Create a pipeline using CodePipeline**

<img width="602" height="157" alt="image" src="https://github.com/user-attachments/assets/21894f02-612d-4bde-ab7d-cd52a674181d" />

<img width="602" height="451" alt="image" src="https://github.com/user-attachments/assets/6b802613-4008-4586-a72b-cebde6404568" />

<img width="602" height="470" alt="image" src="https://github.com/user-attachments/assets/75e89595-3da2-4b11-b6d0-ab3154067087" />

<img width="602" height="203" alt="image" src="https://github.com/user-attachments/assets/c3996d48-2d51-4c38-86f5-fc67550843ff" />

<img width="602" height="361" alt="image" src="https://github.com/user-attachments/assets/dafbec07-f199-4241-88b4-689b8a8e6b55" />

<img width="602" height="468" alt="image" src="https://github.com/user-attachments/assets/a18b9c06-803a-4732-ad03-ed1ed08fda04" />

<img width="602" height="481" alt="image" src="https://github.com/user-attachments/assets/56543a1b-7491-4a73-89e1-8e14186c32ce" />

<img width="602" height="276" alt="image" src="https://github.com/user-attachments/assets/f0bafb08-d158-44ae-b0ae-06c320c254ba" />

<img width="602" height="351" alt="image" src="https://github.com/user-attachments/assets/a12d2adf-9c86-4972-a4c9-f5c3e1d2f92a" />

<img width="602" height="258" alt="image" src="https://github.com/user-attachments/assets/1b371af3-d9ad-4849-8340-6318a82cb4d0" />

<img width="602" height="421" alt="image" src="https://github.com/user-attachments/assets/25dda692-82f7-4425-a417-c028c313ebe7" />

<img width="602" height="140" alt="image" src="https://github.com/user-attachments/assets/6f247da0-de4a-4707-8d13-3286ce03cdf2" />

<img width="602" height="408" alt="image" src="https://github.com/user-attachments/assets/40f4431a-3cff-4f71-950a-52ffc30322b2" />

<img width="602" height="273" alt="image" src="https://github.com/user-attachments/assets/74bb3adc-7d7a-4fee-945d-a5dc0abfe832" />

<img width="602" height="297" alt="image" src="https://github.com/user-attachments/assets/ebc5ca07-ec4a-4857-a4ef-80eeadc3794b" />

<img width="602" height="456" alt="image" src="https://github.com/user-attachments/assets/04cc7364-163d-4e95-a167-a198464349db" />

<img width="602" height="205" alt="image" src="https://github.com/user-attachments/assets/825278c8-9d0c-49ca-893f-df0b3ac13895" />

<img width="602" height="315" alt="image" src="https://github.com/user-attachments/assets/0f6e2d2e-61aa-416e-a53c-ed1afa6e09ca" />

<img width="602" height="176" alt="image" src="https://github.com/user-attachments/assets/6a8cdbc1-8cdb-40ef-9035-e50a4b93ddd8" />

<img width="602" height="132" alt="image" src="https://github.com/user-attachments/assets/f4cc996e-a169-411d-8e87-acb90f38484e" />

<img width="602" height="317" alt="image" src="https://github.com/user-attachments/assets/006fbce5-6523-4cef-aa8d-4867d4c07503" />












































































