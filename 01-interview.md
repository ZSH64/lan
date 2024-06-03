I have seen too much about the job specification or requirements, so I'd like to get an understanding of, say, your requirements and what you are looking  for exactly.




I've been with Allianz since 2020, so I joined around  the peak epidemic. My role was to design and implement the infrastructure in Azure. we can talk about technology choices in a minute. I've been told to build up the infrastructure to host the applications, which people from the development move from on-prem infrastructure. They have buckets of Windows base applications in .net core and they rolled a large chunk of it in .net core,
basically  migrated that to host on k8s
My job was to build the individual environments so that we could move them those applications through those environments, make sure they are adhering to their quality, the security standard, to the  regulatory standard, and then we could present them to the actual customers

My first job was building the k8s clusters so that we could host the applications; the applications are written in microservices pattern, so each single microservice has its own entities working  on it's own container, using its own database and stuff like that

We have five environments at the moment; the largest one is the production one, which is seven nodes, but that's gonna be growing pretty rapidly, parallel to that we use the engine called The App Service Environment(ASE), that's the service from Azure which allows you to run legacy windows applications without need to host your own server, basically your IIS application id started into App Service Enviroment, it needs  its own kind of container, it is not really container because windows doesn't have containers, but its is just emulate the IIS, and it is managed.  it takes of you the security patching and all the operations related to VMs hosting.


I'll share my screen and actually show you what we do. So go to https://quote.allianz.ie/. This is one of our applications, which we host on the K8s.
That is the new application but there are also things like for instance the MyAllianz Applications which is a portal related to the tthe insurance different kind that moved to Azure recently two weeks ago
So Zahra is playing an important part in that, Zahra was hired roughly a month after me. so  we worked together on building the entire infrastructure and building the operational sites around this.
We have loads of DevOps stuff here. This is one of the applications. We have loads of DevOps metrics and Dashboard stuff like that.
We work primerly on Garrafana. There is Promethouse metrics. It is bit noisy at the moment we need to do some cleaning extra.
So Part of the problem at the moment is that we grow so rapidly taht we all need a staff which wasnot necessary to sastain application as we ..
But now we need to somebody else to help us with cleaning, extera, so putting some operational oversight lets put  it that way, and hepling us.
It is not about building anything from scratch; it is more about sustaining what we have at the moment and helping us sustain this entire ship. if that makes sence.

**Interviewee**: Understood, yes.

There are a few tools which we've been told to start using, so Dynatrace would be one of them. So there is design authority which asked us to do certain stuff. 
 That's on the table as well, we are in azure as I told you but at some stage,  we may be told to move to AWS. so thats internal policy
 So we're looking for somebody who has a mix of experience. I can see you have some azure experience as well
 Sorry for my rambling. There is so much stuff to cover, and I just don't want to take your time. but if you have any questions, then let me know

**Interviewee**: Absolutely, thank you for the overviews. It is definitely interesting what you are working on. As you mentioned, I think maybe a bit of maturing operation, and then those non-functional requirements, let's say reliability, security, maybe some. I'm not sure what your expectations are around, let's say rehydration on that.
I've done a lot of work around CI/CD pipelines and automated deployments, provisioning  Infrastructures recalled through  Terraform as well. That was quite interesting


Let's go through that step by step.Obviously, we have CI/CD pipelines. That's not a concern. We have over a hundred databases and the same number of micro services. There is no manual work we could perform here. It has to be done automatically. But then the question is where we go from heres.
  - can we do something more or can we do something to help our engineer to perform even more better at their job.

Let's talk about your experience. So what did you do in your recent job?

**Interviewee**: In terms of my experience there. I was a cloud and DevOps engineer there. So what I was working on was the deployment of SAAS-based applications for the fund investment team, so they had calculations that they needed to run. There was instances of SASS-based application running on-premises  and running people's local machines. So what I was in charge of doing was bringing that to a cloud-based offering and consolidating some of the licences around the firm so that we could use just one centralized platform. So I pretty much work on everything there from creating these terraform, pipelines and Jenkins. We had an interesting problem whereby every 60 days we have to(I'm not sure if you have the same issue) rehydrate windows image that we are running on every 60 days for compliance reasons. and what that meant is that basically terminate the EC2 that we are running on and essentially do the complete install onto another EC2 and obviouslly manually, thats alot of operayional.
I was able to come up with some terraform scripts to do that whole thing automatically. That was one thing that I'm was working on


Can we for one-second focus on that?  what did you mean by rehydration? You mentioned that term a couple of times;

**Interviewee**: There is a companywide compliance standard. There is a lot of operational overhead and time investment, and Terrafrom and Pipeline automated a lot of the processes.




It dose make perfect sence. what were these Windows instances used for? was it a desktop machine?


**Interviewee:** There are Windows server machines used for hosting SASS applications, so the SASS service renders the UI to the ned user.


Did you consider using any other managed services?

**Interviewee:** That's how was done basically when I came in. so we have kind of self-managed EC2 envirmont


Who did you report to? Was it some kind of architecture group? was it a DevOps group? or Operational group?

**Interviewee:**  We had a chapter lead like a team lead. We deliver services for different business unit. 

There was no way of moving that to Linux. So, even putting aside the policies that they have at the moment, would you consider moving it to Linux ? or there is no option moving that?

**Interviewee:** I believe, from technical documentation that SASS providers provided, that their recommendation was to use Windows on EC2 instances. so that is **standalone server**.

**K:** 
You keep calling that SASS, but you hosted that on your owns, so It is not really SASS, is it?

**Interviewee:** it was an external vendor who ran this.



**K:** You need to roll out the new images.  windows is known for being a pain when it comes to creating new instances, It takes ages.
did you have some windows between where you kept the old server and you need to bring the new service? how was that process orchestrated? how did you do that?
when you bring up a new server, how did you orchestrate that entire process? so keeping the application live and you need to bring a new instance of the server and you need to flip traffic to a new one. so how did that process work on detail on the technology side?





**Interviewee:**  That was a very interesting problem to solve. They had to follow the sequential process to **make sure that everything happened in order** so it had to happen when the business was not using it. that involved stopping the servers and creating a new instance, then going into repointing the new instance EC2 with a new IP. then pointing the CNAME record to teh IP of the new instance. that wat a been proces. That was an old token that was associated with the old machine. that had to be regenerated and placed
The password had to be encrypted.
There were some problems I had to overcome. That's kind of a process that we went through. I wrote some Powershell scripts as well to do some basic system configuration. something that should happen after the service is deployed and installed. setting up firewalls and configs.
Then, of course, terminating the old server when it is no longer used to save cost because some of the Azure instances are quite expensive.
 

**K:** 
How much of that was automated? You mentioned Terraform, but Terraform handles a very narrow set of tasks. So, how much of the entire journey,from **kicking off this process** to **decommissioning the old servers** was automated?

**Interviewee:**
I would say probably 90% was automated. It was quite efficient. One challenge I had with automation was certificates.
We use a Certificate Manager called Venafy to get our PEM files, and a translation of that creates a PPK file. **There is a bit of a manual process around running SSL binding** and then merging that within mmc, and some manual processes around setting up the system settings for the first time. 
So that was one of the manual processes that aren't completely automated.
But that was relatively efficient. There is a good operational document around that. It is a documented and repeatable process. All the heavy lifting was automated.


**K:** 
Aside from this project, where did you use Terraform?


**Interviewee:**
so, It was the first place that I ecncounterd Terraform. it was a relatively new technology to me at the time.
I've been aware of other infrastructure provisioning tools like cloud information, but I wouldn't have used some of them.
That was my first exposure to it. It is pretty easy to pick up when you use it.
 
**K:** 
When you use Terraform, It needs to save state to a file or some other location. How did you manage the state in terraform scripts?

**Interviewee:**
We had the teraform scripts located in Git for storage of those p 

**K:** 
Terraform has some problems with storing secrets; basically, it stores the secret in open text. How did you work around that? This includes passwords, certificates, and any other sensitive data.


**K:** 
Once you have a server, you flip the traffic to the new stack. How did you know the new stack is working correctly? if there is feature parity between the old one and the new one.



**Interviewee:**
In terms of how I figured out that it was working correctly, it was reachable by a web browser. And if the pinging of that URL returns the right IP of the new instances, it could be a valid test that it is pointing to the rights server

**K:** 
But you said some certificates needed to be generated, so **there is a set of tasks need to be performed**  , and then you need to check if those certificates work correctly. 
everything is working together. so aside from doing the basic smoke test, do you have the motoring at the top of the stack?

**Interviewee:**
Yes, we had monitoring in place. We used DataDog for monitoring. I set up a monitoring view that covered all environments, from development to production. This was broken down into system-level metrics like RAM, CPU utilization, and the Mongo database, which became crucial as we onboarded more people.

I also set up monitors to detect any excessive CPU, RAM, or storage utilization and send notifications accordingly. Additionally, we monitored time availability and the API to ensure everything was running smoothly.

**K:** 
How did you send notifications?

**Interviewee:**
We were able to integrate ServiceNow with DataDog. For example, if there was a **threshold breach of 80% in any system-level metrics**, an email notification would be sent. If the **breach exceeded 90%**, DataDog would create an incident ticket for production support. They would then look to **triage the issue**, and if they couldn't resolve it, we would step in to address it at the third-level development stage.

**K:** 
Did you play any role in L1 or L2 support? Would those tickets be assigned to you?

**Interviewee:**
I was setting up the cloud platform for the first time, so I provided more hands-on support than typical engineers would. In the early days, yes, I handled L1 and L2 issues. I also established a good support model with production support. **I documented the most common recurring issues** and the regular use of the application for users.

I set up meetings with production support to train them on handling these issues, such as login problems or system issues. This training allowed them to **take over** some of the L1 and L2 support tasks. We implemented a solid support model, with ServiceNow incident tickets being sent to their team. They would troubleshoot the issues, and if they couldn't resolve them, the issues were escalated to us.

**K:** 
Let's do a quick thing about the Kubernetes and Docker. So what kind of work did you do for them in A company?




**Interviewee:**
One problem we had was that there were a lot of **people who had free rein** to set up namespaces within the k8s platform. The problem that we were having was that **we couldn't attribute what team or people created those namespaces** and as a consequence, we had all t he resource utilization that was a bit wasteful
So, I developed a utility that **taps into** the API to translate the email address that created the namespace and try to **attribute the person** who created the namespace to the team's business unit. and I was able to create an automated notification to the team who owns these namespaces and then have **automatic deletion of** those namespaces if they were not being utilized or being actioned by users; they were cleaning them up. 
 
The other part was a kind of advisory for new tenants coming onboard to the system. So lots of providers like to host their applications to k8s and I was acting as a kind  of a **dviser for people**. how to setup their applications


The second part of my role was around ingesting a company into the IT landscape within Allianz. so I would have been doing some bio worker around that like opening network path kind of stuff

**K:**  
So that k8s cluster sounds like (to me at least), there is one cluster, and the individual team would get their own namespace to play with. Is that the accurate description?


**Interviewee:**
They could create their namespace within the k8s. **Rancher** is an Interface by which they could do that. 


**K:**  
 How large was the cluster in terms of number of servers?



**Interviewee:** 
It was pretty signifiicant I do know the exact number of servers.
They had a pretty interesting problem, actually. where by people were working on labs because there is in a semi-conductor industry, and the resources they use always seem to double
 so they needed a clever way to manage cost



**K:**  
So, what is the correlation between K8s and cost management? Do they think that by having an application run on K8s, they are going to save money? I don't understand the correlation between cost and k8s.



**Interviewee:** 
The idea was for the team to do more with less. I don't know the business driver behind it.

**K:**  
Was there any idea of splitting the cluster to multiple and give the teams their own cluster? it's supposed to be a gemous one?



**Interviewee:** 
All team had their own namespaces. we got an understanding of what technology they were using




**K:**  
You mentioned AWS and Azure; where was the k8s running, actually?

**Interviewee:** 
I belive they run the cluster on all three envrioments Azure, AWS and GKE

**K:**  
How did you deal with cases, did you have any saying that a team abusing that cluster like consuming too much memory and cpu or anything like that?

**Interviewee:** 
There was When people like hitting the APIs too much, I believe there was a cost associated with API call.I know that there was some sort of controls putting place we had Splung to monitor like our team were hitting certain APIs

I wasn't personally involved in it. **I was developing a utility to sniff out dormant namespaces** that people weren't using and automatically delete them. I created the utility with Python to do that automatically.

**K:**  
Have you provisioned your own K8s server or K8s cluster, even aside from all your work experience? Did you do that for your own purposes as exercises? Did you try to create the K8s cluster on a server or on your local machine?


**Interviewee:** 
Personally, I haven't.



**K:**  
What advantage do you see in using  k8s in general?

**Interviewee:** 
The idea is to do more with less. I see it as a good way to keep costs in check and ensure smooth operations in the firm.


**K:**  
Do you see any workload that you'd never put in the k8s for some reason?
If I told you we have a cluster of VMs and want to cut costs by moving them all to K8s, is there any use case that you consider not suitable for K8s?

**Interviewee:** 

No, Nothing that I can think of.

**K:**  
 Do you have any hands-on experience with managing Linux? or operating Linux VMs?

**Interviewee:** 
Predominantly, Windows really. I know I would have done releases in previous banking roles in Linux, but it would have been predominantly Windows. 

**K:**  
Aside from Terafform, Do you have any hands-on experience with other similar tools that allow you to manage VMs, provision them, or perform some kind of automation on those VMs?
So, Ansible, Cheif, you mention cloud information, right?

**Interviewee:** 

Yes, Ansible, I would have experienced it. So one thing we had was minimum security based lines for some of the servers that all the servers that they are runing and so
these minimum security-based lines are interposed by wide policy.
In order to retrieve and report on that information, we had Ansible scripts running to pull that information and report it back to create a consolidated dashboard. That was probably one example of using Ansible.


**K:**  
Any experience with Promethouse, Graffana.
So, DataDog was one of the tools. Aside from DataDog, did you use any other similar tools? I believe DataDog is for collecting and presenting metrics. It's a comprehensive data management tool.



