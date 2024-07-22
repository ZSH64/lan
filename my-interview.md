Good afternoon, and thank you for joining us today!

My name is Zahra, and I’m a DevOps Engineer at Allianz Ireland. My primary role involves maintaining our cloud infrastructure and implementing CI/CD processes. I work closely with our cloud solution architect, and together, we form the core of the DevOps team here at Allianz Ireland.

We began our journey about three and a half years ago. Since then, we have collaboratively built the entire infrastructure and the operational sites surrounding it. Our main platform is Azure. We run Windows applications on the App Service Environment and .NET Core applications on Kubernetes clusters. Currently, we manage six custom-built Kubernetes clusters, which are isolated from one another to ensure robust security and performance.

In terms of DevOps practices, we have a comprehensive setup including various metrics and dashboards that help us monitor and manage our infrastructure effectively. Our team is responsible for overseeing these clusters and providing support to other teams.

As our applications continue to expand, we are looking to grow our team. We’re seeking a DevOps professional who is keen on automation, has a solid understanding of cloud technology, and is adept at maintaining operational standards. This role isn’t about building from scratch but rather about enhancing and sustaining our existing infrastructure.

Do you have any questions before we proceed?

------------------




**CI/CD:**
- Can you tell us what you are doing in your current job? What is your duty? How would you describe your role there?
- How often did you run releases? How often was it done?
- Could you describe a build and deployment pipeline you've created in any system?
- Can you describe an example of something that you automated? I know you've given those suggestions of the ideas of what you've been working on, but just something that you've greatly automated that saved the business time?

  
**artifactory**
- Did you use any **artifactory** like nexus here?
 - What exactly did you keep in the artifacty?
**Microservice**
 -What is your opinion on microservice? When is the best to use microservice? and when it is not the best idea. What kind of value do we get from microservices?


**K8S:**
- you have experience in managing or deploying applications in Kubernetes environment.
- Did you manage k8s admin part?
 - how many clusters did you have?
 - How large was the cluster? how many nodes did you have there?
- What advantages do you see in using K8s in general?
- Do you see any workload that you'd never put in K8s for some reason? If I told you we have a cluster of VMs and want to cut costs by moving them all to K8s, is there any use case you consider not suitable for K8s?Do you see any workload that you'd never put in K8s for some reason?
- Can you explain how you would perform a rolling update or rollback in Kubernetes?

**K8S:**

Quick question on the theory side. Let's say I want to build my public-facing Application, so basically, it has to go to the Internet. I have a product consisting of multiple microservices. They are run on the K8s cluster in the back end. How would you open the K8s cluster for those applications to the public internet, regardless of the cloud infrastructure? You can pick up your own stack if you want so that it is secured and the data can not be broken into. Basically, it is a fully working 21st-century product. which is secured to the customer, which is fast and efficient

The only requirement I have is that the application has to be run on k8s. It has to be accessible from the internet. How would you that?

- What kind of Loadbalancer strategy would you pick up for a load balancer here? Have you worked with Revers Proxies? What is Reverse Proxy? what is the difference between a load balancer and a reverse proxy?

**Istio**
 - What about **Istio** in k8s? Have you heard about Istio?
- How did you configure microservices to integrate into Istio Service Mesh?
- Why did you use Istio? what exactly did you use Istio for? Why is it important in this case?

- how did you manage persistent volumes up to that point? Did you use persistent volumes in Postgres?

**ReversProxy:**

- Have you worked with Revers Proxies? What is Reverse Proxy? what is the difference between a load balancer and a reverse proxy?
**Ansible**
- What did you use Ansible for?

**SQL**
- wht kind of database you use?
- What kind of experience do you have with SQL Server?
- Have you completed the release management of the **SQL database schema**? When you release applications, you sometimes need to update the schema in sql server.Have you done anything like that?

**Redhat**
- You also mentioned you have some experience with Redhat. What did you do exactly in the Redhat?

**Terraform:**
- where did you use Terraform?
- How did you manage the state in the Terraform script?
- Terraform has some problems with storing secrets; basically, it stores the secret in open text. How did you work around that? This includes passwords, certificates, and any other sensitive data.

**Automation Tools**
- did you have some windows between where you kept the old server and you need to bring the new service? **how was that process orchestrated?** how did you do that?
- How much of the entire journey was automated?
- Aside from Terraform, do you have any hands-on experience with other similar tools that allow you to manage VMs, provision them, or perform some kind of automation on those VMs?


**logging and Monitoring:**
- Have you used any log aggregators?
- What did you use Graffana for?
-  did you manage the promethouse from admin side?
- Have you created any dashboard in.
- Did you have any **alerting infrastructure** here as well? did you use any thenologies to send alerts when somethings went wrong?
  - what if the disk run low or CPU was overextended?
- How do you monitor and ensure the performance and health of your cloud infrastructure in a DevOps environment


- How you protect your selve form the upgrade going wrong, how did you rolleback?
- What are the potential challenges you might face when implementing Continuous Deployment?? and how did you go about overcoming it
What would you say are mandatory steps in Continuse integration

WHat security considratiion do you consider when you building a system? what doose key security considration?what is the pricnisples you apply?

next question ganna be like a role-playing scnario. So I gonna give you a problem and just see what your next step would be and how you think through a problem essentially. so the problem is that there is a devops engeenr in your team and sick, but when you run terraform, there is a whole bunch of infrastructure changes that are going to happen like delete other changes. how would you go around and solve the problem? what would be the first command you'd run? or the way you'd approach that problem?
