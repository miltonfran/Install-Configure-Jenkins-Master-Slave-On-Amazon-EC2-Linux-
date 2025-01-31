<h1>Install & Configure Jenkins Master-Slave On Amazon EC2 Linux </h1>

<h2>Description</h2>
This project demonstrates how to set up a Jenkins Master-Slave architecture on AWS EC2 instances running Linux. The setup enables distributed builds and improved scalability for your CI/CD pipeline by delegating build jobs to slave nodes while the master node manages the overall system.
<br />


<h2>Languages and Utilities Used</h2>

<b>

  - Bash/Shell scripting
  
- Jenkins Configuration DSL

-  AWS CLI commands 

<b>

<h2>Environments Used </h2>

</b> - AWS EC2 instances (t2.micro or higher recommended)
- Amazon Linux 2
- Jenkins Master node
- Jenkins Slave node(s)</b>

<h2>Program walk-through:</h2>

<p align="center">
step 1: Launch EC2 Instances

-  into AWS Console and navigate to EC2
- Launch two EC2 instances
- Use Amazon Linux 2 AMI

Configure Security Groups:

- Allow SSH (Port 22)
- Allow Jenkins (Port 8080)
- Allow custom TCP for Jenkins agent connection (Port 50000)

<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738192153/Screenshot_2025-01-28_182026_lkcua7.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738192218/Screenshot_2025-01-28_184438_pxlu8i.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738192773/Screenshot_2025-01-28_184645_rv9wqf.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738192801/Screenshot_2025-01-28_192035_abouur.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738198948/Screenshot_2025-01-28_201142_lqwoqy.png"/>
<br/>
<br/>

Step 2: Install Jenkins on Master Node 
Connect to Master EC2 instance via SSH
- Install Java
- Install jenkins
- Start Jenkins service
- Install Docker

<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738200152/Screenshot_2025-01-28_192229_nn7t6u.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738201067/Screenshot_2025-01-28_192522_m0ctvr.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738201115/Screenshot_2025-01-28_195805_cifylx.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738201182/Screenshot_2025-01-28_200016_woi0s8.png"/>
<img src="srchttps://res.cloudinary.com/dk3bkl3ji/image/upload/v1738201630/Screenshot_2025-01-28_205236_viynne.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738201445/Screenshot_2025-01-28_204734_rqyc08.png"/>
<br />
<br />

Step 3: Initial Jenkins Setup<br/>
- Access Jenkins web interface via browser:
http://[master-public-ip]:8080
- Retrieve initial admin password:
  sudo cat /var/lib/jenkins/secrets/initialAdminPassword

<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738202848/Screenshot_2025-01-28_201650_tocy0z.png"/>
<img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738203450/Screenshot_2025-01-28_201919_i1f9en.png"/>
<br />
<br />

Step 4: Configure Jenkins Slave Node<br/>
- Connect to Slave EC2 instance
- Update system and install Java:

sudo yum update -y
sudo amazon-linux-extras install java-openjdk11 -y
sudo useradd jenkins
sudo mkdir -p /home/jenkins/agent
sudo chown -R jenkins:jenkins /home/jenkins

- Add Slave Node in Jenkins UI
- Navigate to Jenkins Dashboard → Manage Jenkins → Manage Nodes
- Verify Connection
- Check node status in Jenkins dashboard
- Verify agent connection status
- Run a test job to confirm proper operation

 <img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738261918/Screenshot_2025-01-28_201952_k3pcg6.png"/>
 <img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738261954/Screenshot_2025-01-28_203440_aizcbe.png"/>
 <img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738261984/Screenshot_2025-01-28_203659_nbkhpr.png"/>
 <img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738262017/Screenshot_2025-01-28_203751_kbwd5d.png"/>
 <img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738262984/Screenshot_2025-01-29_013525_cdpbns.png"/>
 <img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738263009/Screenshot_2025-01-28_204832_nhukde.png"/>
 <img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738271638/Screenshot_2025-01-29_013604_dtpfjm.png"/>
 <img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738271660/Screenshot_2025-01-29_013739_zntihw.png"/>
 <img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738271708/Screenshot_2025-01-29_013831_rcroti.png"/>
 <img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738283111/Screenshot_2025-01-29_014211_wtmkfy.png"/>
 <img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738283143/Screenshot_2025-01-29_014249_oxxvpn.png"/>
 <img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738283168/Screenshot_2025-01-29_014322_dftcpe.png"/>
 <img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738283204/Screenshot_2025-01-29_014405_vxsljq.png"/>
 <img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738283289/Screenshot_2025-01-29_014505_o9ezn3.png"/>
 <img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738283493/Screenshot_2025-01-29_014559_x68qhv.png"/>
 <img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738283554/Screenshot_2025-01-29_014655_hn36rh.png"/>
 <img src="https://res.cloudinary.com/dk3bkl3ji/image/upload/v1738283580/Screenshot_2025-01-29_014724_h3gxqt.png"/>

<br />
<br />

