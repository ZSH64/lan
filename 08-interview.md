**Kr**

It's always problem weith setup with webex I supose!
Godd aftrnoon Avinash, thank you for joing! **It is quite late. It is thursday already**
We've got your cv from Ali, **We've got interested in the number of techniques which you listed in that CV**.
Just as an introduction, I am Kris; I work as a cloud solution in Allianz Ireland!
My job is keeping up to date with the cloud infrastructure for some of the products. Zahra is working with me; she is a DevOps engineer. 
**Both of us combine into the DevOps team** in Allianz Ireland. We started our journey around 3 and half years ago. 
Around two years ago, it is really picked up; 
There are more products that we are currently putting into the cloud. Thus, we need to scale, and we are looking for people who ganna allow us to
scale it up to the next level. we are also looking for some people who have experience with working with other companies because and We've have worked on these projects for quite some time now, so we are isolated from the external world, **so we are looking to have fresh blood** and keep us more experienced.




We do have Azure infrastructure mainly,  we do have also AWS but we don't use it very much, there was an account which we created long time ago for experimentation.
We mostly use Azure. The applications run on The App Service Environment for Windows applications plus .net core applications, which work on K8s clusters.
At the moment, we have 6 clusters, 5 different environments, and the build environment. Those K8s clusters are isolated from each other; they don't talk to each other.
So we want to make sure that we test the applications in isolation from each other.


What else? We use Prometheus and Graffana for monitoring and Elastic Stak for log aggregation. So, we also use ISTIO. We'll talk about it in a minute because I noticed that you used Istio.


Do you have any questions before we move forward? Is there anything of your interest before we move on?

**In**

No, we can proceed

**Kr**

Let me share my screen we can chat about your CV if that's fine.
This is the CV which we got from Oliver James.
So you work for Erikson. 
where are based at the moment? Is it going to be a problem to come to Dublin once in a while?


as such, we are not really Hybrid because we are asked to come to the office once a week. **but nobody's enforcing that**. We can make it work fully remotely if that's works for everyone

we don't see each other in the office. me and zahra, for instance. **We work remotely pretty much all the time**. That's work for us. 
**It is just a matter of setting up** what kind of model works for everyone.

Can you tell me what you did in Erikson? What was your job? What was your duty? How would you describe your role there?

**Avi**
I was responsible as an applications engineer, mainly supporting the microservices team.
Applications **can be considered as a bunch of microservices**.
Spluncer **was mainly used by** the **cloud ops team** to deploy applications to AWS EKS cluster
**My team was responsible for** writing the helm chart for microservice
We **integrated applications with** Postgre DATABASE.

In terms of testing, we were using some load tests. we had to **build a testing pipeline from scratch ourselves** 

The first assignment was actually a product that a number of people came together to build from scratch. There were around 800 people working on this specific product in Athlone itself.

We had integration with Promethouse, Graffana and Istio. All these third-party services where again provided by the Central team, so what we had to do was **integrate them and configure the pipeline**
to deploy them, then **trigger the K6 testing pipeline** to **run the load tests** and **gather the performances and response metrics** from the test.

The testing would be done by Product level teams as well. Multiple teams worked together.

My **main day-to-day job** is mainly to deploy the Postgres DB and Redis cluster to the Open Shift platform and whatever automation is required, which our teams are responsible for doing.
and also writing the functional tests as well to test the integration Database with the other services




**Kr**


Can we start with your previous project? Sorry, **I didn't catch the name**.
So you said that there were services, and applications, right? So how did the release proccess work? **That sounds like pretty much complex**. 
Did you release individual services? or did you move applications on the Entrite products?



**Avi**
We were responsible for only two applications. These applications have multiple microservices plus a database. so, for example, microservice teams **make a commit**
that **would trigger the application pipeline.** So all **that orchestration was done by** Spinnaker

So Spinnaker was the main orchestrator. **The microservices passed the application staging**, which **triggered the product staging pipeline**. After the successful completion of product staging, it deployed into the production cluster. Deployments were on multiple clouds, and multiple customers made their own choices. 
This would deploy to AKS Azure as well.
Mainly AWS and Azure.

**Kr**
I get it. Then you use Helm to deploy the K8s applications, right?

**Avi**
We would have multiple helm charts. **Microservices would have their own helm charts**, which would then be wrapped into an application helm chart.
Then we would have another **product-level helm chart** that would contain a number of applications, so it would be like an umbrella chart called a product chart.
That would **ultimately get deployed into the cluster** that the customer uses.


**Kr**
**How often did you run releases**? How often was it done?


**Avi**
The release would run every night. so every 24 hours.

**Kr**
so **whatever changes were committed,** they would be going through those all the pipeline, right? That's the idea.
Did you use any artifactory like nexus here?
Sorry, **I didn't notice that in your CV**.
What exactly did you keep in your artifacty?

**Avi**
The heml packages and also our Docker images.


**Kr**
Did you have their own ortifactory, or did you have a managed instance?

**Kr**

What did you use Redis for?



**Avi**
Redis is the catching service for cloud-run products. As a team, we are only responsible for the data sources, so **we are expected to deliver** all **data-related services like Postgres **and Redis.
Even **Redis is used as a message base**.



**Kr**
Interesting. Why is it like that? AWS has very interesting tools, even KAFKA, AMMQ or other services. Why did you use Redis? That does not sound right, really.

 
**Avi**
When I said cloud run, **it's more on the networking side of the mobile networks**. So We would **package all the helm charts and the docker images into a package** and these  packages are 
actually **delivered to the customer**, so customers would install them into their networks.
So this is the **standalone deployment** as you say

So, it is completely microservice architecture. **They get the package which has everything in it**.


**Kr**
By customer you mean other company? So they would get the entire package. I see!
There is one **interesting point here**: "Containerize and Deploy Redis and Postgres on EKS cluster" **Why did you put Postgres on k8s**?


**Avi**
The Eroksomn's **use cases were pretty straightforward**. every application would have **its own individual data store layer**.
There is no product level or one single instance. so **every product application uses its own data store**.

There is a central team that actually does this containerization of Postgress, so we at Erikson have this policy of using it. **Any specific third-party services will be containerise**d. We can just pick that up and modify and configure it according to the needs of the application.


**Kr**

**I get that**, but you are on AWS, and AWS has its own managed Postgres. **why did you go with the containerised version**?
We see that as the way in Allianz. some people make that stupid decision. I was just curious; **I would never put a database on the k8s cluster**. Because there are a number of issues we had with the persistence volume, for instance, right?

So, How did you manage persistence volume, going to that point?
Did you use persistence volume in Postgres?

**Avi**
It is written by the Postgres team. so that wasn't me.

**Kr**
How did you configure microservices to integrate into Istio Service Mesh?

**Avi**
So, first of all, these are configuration-specific for the Pod template. One usage is specific cert need to comiunicate with teh IStio part.
When you said Istio, it is MTLS. so we are to **configure a microservice to use MTLS**, to use certificates to login into other services

**Kr**
**Istio does it automatically,** you don't have to do anything here.
When you install Istio, **it creates a sidecar** that is **assigned to the individual services**. **Istio orchestrates the certificate issue** and **mutual authentication**.
I'm just curious. What exactly did you do here? Why would you customize something if Istio does it for you automatically?


**Avi**

 We **were adding annotation** for the microservice to **become part of the Istio mesh**.

**Kr**

Do you mean it enables?
**Why did you use Istio?** what exactly did you use Istio for? Why is it important in this case?


**Avi**

We use Istio for secure communications between services, it provides MTLS.  and also for autorisations.
It was **based on the customer's needs**. I think a **zero-trust framework** was **one of the requirements to deliver**

**Kr**

Do you remember the **networking plugin in k8s** you used?

But Calico has some security features implemented already, so Calico, for instance, has some features which I**stio already has around the security comiunications**.
Did you try to use Calico for that? Do you know why I used the Istio, or was it just a customer requirement?

**Avi**

It was an architect's decision and based on customer needs. we are not involved in.

**Kr**

What is your opinion on microservice? why do we use that pattern?
When is the best to use microservice? and when it is not the best idea.
**What kind of value do we get from microservices?**


**Kr**

How large was the cluster? how many nodes did you have there?
How many master nodes?
From a networking perspective, I  have 20 nodes, and I have a service installed on node number 15. I'm a customer. I'm **coming from the Internet** and I want to call 
that exactlly service on that node 15, how do I do that?

So, The individual applications **can be shifted and run between different nodes**; that is part of the problem probably.So how the **k8s allows you to target those individual** applications **regardless of where they are installed**
You have an application on node 15, then you restart it, and all of a sudden, it lands on node 6. How do the K8s help me reach the proper node?

**Avi**

Traffic flows to Service objects, so the request hits the load balancer. Once it passes a load balancer, then it hits the service object. then the service object would have a map of where to send the request with respect to


**Kr**

Let's move back for a second because you said that the load balancer hit the service object; **how does the load balancer know what to hit exactly**?

**Kr**

How would you explain the difference between k8s and Docker? what is the key difference between the k8s and docker? What is the relationship between k8s and docker?


**Avi**

Docker is containerisation technology but the k8s is container orchestrator. That's the major difference.


**Kr**

**What does the orchestration actually mean** in this context?


**Kr**

I noticed you use "Image Scanning Tools," but I didn't get that; what are those?


**Avi**

They would scan Docker images for **vulnerabilities and security constants**. These could come from the OS layer or from the application itself.
They could generate vulnerability CV reposts.

**Kr**

What is the name of the tool?
Oh, okay, I didn't get that name. I know Qualys.
**Qualys is integrated with the artifactory?** How does it work?


**Avi**

Qualys is integrated into the pipeline.

**Kr**

What did you use Ansible for?


**Avi**

This was from my previous Job. We had a platform for specifically to get IMID. There are several customers like mostly from the auto industry using this platform for **IDM services**.
We had multiple services deployed. we had an **Apigee API gate way.**
We use Ansible to deploy **the Apigee cluster** on to environments.
**When we say Apigee cluster, it is a full stack from the load balancer to the database**

**Kr**

So you had self-hosted Apigee on your own infrastructure.


**Avi**


No, Apigee was hosted on AWS. Now you can use **Apigee in GCP as a service**. it is a good product. but in our case it is hosted in AWS as an on-prem cluster.
They have the option of deploying on promises, so we deployed it on AWS as we already have a service running the back-end **IDM services**.



**Kr**

Quick question on the **theory side**. Let's say I want to **build my public-facing Application**, so basically, **it has to go to the Internet**.
I have **a product consisting of multiple microservices**. They are run on the K8s cluster in the back end. How would you **open the K8s cluster for those applications to the public internet**, regardless of the cloud infrastructure? You can pick up your own stack if you want so that it is secured and the data can not be broken into.
Basically, it is a fully working 21st-century product. which is secured to the customer, which is fast and efficient

The only requirement I have is that the application has to be run on k8s. It has to be accessible from the internet. How would you that?

**Avi**

If it is an **internet-facing application** , The **front-facing layer** would be a load balancer. The request would hit the load balancer. Before, we would require DNS names to be registered.
Also, **requires enabling SSL and TLS for communication**.

We could choose to **offload TLS on the load balancer** itself or in the application layer.


**Kr**


What is the role of the load balancer here? Why do we need a load balancer?
If I go to your previous example, you're cluster has 20 nodes the **load balancer would be targeting each** single of those nodes


**Avi**

We would operate a NodePort service, and then they would be mapped to a DNS name that **would be internal to our Infrastructure**. Request hits the worker node.
CORE DNS would come into play and redirect to a specific service name. The service would forward requests to specific pods based on mapping from Kue-proxy.
Then finally reach the Pod itself

**Kr**

**What kind of Loadbalancer strategy would you pick up for a load balancer** here?
Have you worked with Revers Proxies? What is Reverse Proxy? what is the difference between a load balancer and a reverse proxy?

**Avi**

The Revers Proxy should not do Load balancing. It is just a front for the application that we want to hide. We had Jenkis server, which was behind the Nginx, which is a proxy.


**Kr**

**Have you ever worked with web application firewalls?** Like WAF?
How about any tools related to **DDOS security**?


**Avi**

**With respect to security**, I have some experience securing applications, mainly from the CI/CD front. 
We had a third-party library tool scanning called **Black Duck** so it would scan the application itself before containerizing it.
It would fail the pipeline if there were vulnerabilities; the pipeline will not move forward until you fix that. Apart from that, 
We set TLS communication between our Jenkins servers and worker nodes.



**Kr**

You've also mentioned you have some experience with Redhat. **What did you do exactly in the Redhat**?

**Avi**

I worked for a team that maintained Redhat services. We were provisioning new hosts as requested, way back in 2016.

**Kr**
How did you provision that?
Did you  need it to  do some configuration manually on that server?



**Avi**
Once the server is provisioned, we used to do network configurations and also patch the server.


**Kr**
Can you write a script in Bach?
What tools do you use to **check the amount of free disk space on the server**?



**Kr**
What did you use Graffana for?


**Avi**

We use Graffabna to visualize the cluster health and pod metrics.
Kibanna is a UI tolls to which wehere logs


**Kr**
Did you be on your ELK, or did you use the existing one?



**Avi**
This was mainly the exciting one. **The ELK stack was also containerised**.


**Kr**
We are approaching 45 minutes now. As I said, we are going to leave the last 15 minutes for your question. Is there anything you would like to know more about? Would you like to learn more about the role or about the company?

**Kr**
That's Zahra and me. We are mainly in Azure except for the AKS; we use our own K8s cluster, which is hosted on an Azure VM. We don't use AKS.

**Avi**
So you are expecting some new work that are coming in; that's why you are recruiting, is it?

**Kr**
It is a mix of; at the moment, we are adding more applications which are being migrated from legacy infrastructure, from premises. That is VMware as well
they want to decommission the VMWare and move completely to the Azure mainly. That's loads of applications.
We had almost 80 Virtual machines and almost 200 different databases. The infrastructure is quite sizable.we have a lot of automation, but in the end, it is just me and Zahra working on and supporting that. plus there is ongoing support work with the development teams and helping product teams. So it is mixed of staff. basically we need someone to help with that.


**Avi**
































