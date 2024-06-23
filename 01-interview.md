I haven't  seen too much about the job specification or requirements, so I'd like to get an understanding of, say, your requirements and what you are looking  for exactly.




I've been with Allianz since 2020, so I joined around  the peak epidemic. My role was to design and implement the infrastructure in Azure. we can talk about technology choices in a minute. I've been told to **build up the infrastructure** to host the applications, which people from the development move from on-prem infrastructure. They have buckets of Windows base applications in .net core and they rolled a large chunk of it in .net core,
basically  migrated that to host on k8s
My job was to build the individual environments so that we could move them those applications through those environments, make sure they are adhering to their quality, the security standard, to the  regulatory standard, and then we could present them to the actual customers

My first job was **building the k8s clusters** so that we could host the applications; the applications **are written in microservices pattern**, so each single microservice has its own entities working  on it's own container, using its own database and stuff like that

We have five environments at the moment; the largest one is the production one, which is seven nodes, but that's gonna be growing pretty rapidly, parallel to that we use the engine called The App Service Environment(ASE), that's the service from Azure which allows you to run legacy windows applications without need to host your own server, basically your IIS application id started into App Service Enviroment, it needs  its own kind of container, it is not really container because windows doesn't have containers, but its is just emulate the IIS, and it is managed.  it takes of you the security patching and all the operations related to VMs hosting.


I'll share my screen and actually show you what we do. So go to https://quote.allianz.ie/. This is one of our applications, which we host on the K8s.
That is the new application but there are also things like for instance the MyAllianz Applications which is a portal related to the tthe insurance different kind that moved to Azure recently two weeks ago
So Zahra is playing an important part in that, Zahra was hired roughly a month after me. so  we worked together on building the entire infrastructure and building the operational sites around this.
We have loads of DevOps stuff here. This is one of the applications. We have loads of DevOps metrics and Dashboard stuff like that.
We work primerly on Garrafana. There is Promethouse metrics. It is bit noisy at the moment we need to do some cleaning extra.
So Part of the problem at the moment is that we grow so rapidly taht we all need a staff which wasnot necessary to sastain application as we ..
But now we need somebody else to help us with cleaning, extra, so putting some operational oversight, let's put it that way, and helping us.
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
I was able to **come up with some terraform scripts** to do that whole thing automatically. That was one thing that I'm was working on


Can we for one-second focus on that?  what did you mean by rehydration? You mentioned that term a couple of times;

**Interviewee**: There is a companywide compliance standard. There is a lot of operational overhead and time investment, and Terrafrom and Pipeline automated a lot of the processes.




It dose make perfect sence. what were these Windows instances used for? was it a desktop machine?


**Interviewee:** There are Windows server machines used for hosting SASS applications, so the SASS service renders the UI to the end user.


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
**There were some problems I had to overcome**. That's kind of a process that we went through. I wrote some Powershell scripts as well to do some basic system configuration. something that should happen after the service is deployed and installed. setting up firewalls and configs.
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

**Interviewee:** 
Yes, it can do a lot of things to monitor, let's say, proccess level metrics, It can monitor WebAPis ad API response times. 
It can monitor databases. It can do all the basic system level metrics monitoring. You can also do synthetic load testing so like stress testing withn the application, not something
like I'm not using too much detail

However, we had a big issue with significant latency in one of the web APIs, which was preventing a release from occurring. We had non-functional requirements that the API response time should be under 300 milliseconds. So, we were able to do stress testing and see all that within a dashboard in DataDog. By looking at all the different components, we could perform some performance tuning, adjust the IIS settings, run stress tests, and monitor the changes in DataDog.


**K:**  

Does it also have log aggregation? or is it just primarily metrics?

**Interviewee:** 
It can **tail logs** as well. You can see the logs and visualize them within DataDog. There is a **cost associated with** how many logs you are consuming, so you can just tail certain logs.

**K:**  
Have you used any other log aggregation tools? Like Elastic  Stack or Splunk?

**Interviewee:** 
I use Splunk pretty heavily in Allianz.

**K:**  
Have you created any Dashboard in Splunk?


**K:**  
So Calico is one of the plugins for k8s? do you use any other?

**Interviewee:** 
No, Calico was the only one that I was looking at when I was there.

**K:** 
Did they ask you to use Calico? or did you just choose it on your own?


**Interviewee:** 
No, That decision was made

**K:** 
That was running the network across all three environments? that was like a central plugin for your networks

**K:** 
What about Istio in k8s? Have you heard about Istio?


**Interviewee:** 
I've heard about Istio, but I haven't had too much exposure to it.


**K:** 
You have some experience with SQL Server as well. I'm asking because we do a lot on managed SQL instances. What kind of experience do you have with SQL Server?

**K:** 
Have you done the release management of the SQL database schema? When you release applications, you sometimes need to update the schema in sql server.
Have you done anything like that?


**Interviewee:** 
I would have had at some stage, but some of those production systems were done **alongside developers** who were developing applications and **done through the releases**.

**K:** 
Out of curiosity, what software did Allianz use for the releases? what kind of toolset did you use?
when you say you did software releases on various OS like Linux, unix and Windows how they worked excatly?




**Interviewee:** 
The tools we used for software releases was ServiceNow. The team would raise a Change Management Request, go through CAB, and then work **in tandem with** developers to release whatever changes they had into Production. There was a wide landscape of software for those trading systems; we oversaw several of them, including everything from Portfolio Management Systems to Analytic Systems.

We had a good management process in place, and everything was often documented in terms of the sequential steps to follow for those releases.




**K:** 
Your job was just to do hands-on releases on whatever software was required to be released, right?

**K:** 
**We are approaching 45 minutes at the moment**. I want to use the last 15 minutes to answer any of your questions. Do you have any? Can I help you with undrestadning the role better? Or is there anything you'd like to learn from this call?



**Interviewee:** 
Yes, I do have a question. Could you tell me what you like about working on the project you're currently involved in?


**K:** 
I don't really feel like I'm working at a big company.Allianz Ireland had **a lot of independence for a very long time**, but this started changing recently. We used to work for Allianz Ireland, but we were moved to Allianz Technology **a year ago**. Basically, they took all the IT staff and moved them to a central organization. 

Even then, we have a lot of independence in our technology choices. For instance, I was asking you about Calico, and you mentioned that someone else made that decision for you, or that you're working with tools chosen by someone else. In our case, we are pretty much choosing our technology stack ourselves.


So it was up to us to create the infrastructure, **aside from choosing the cloud provider** because that **decision was made** for us. We didn't have any say in choosing Azure as opposed to AWS.

Aside from that, it is completely up to us to **choose our own toolset** and the Linux flavor to run those servers and ensure their security. We work with various players from the security and operations sides, but again, we own the entire stack.

We built it from scratch, which is why I like working here—I have full ownership of the entire stack where we run those applications.

Having said that, we work very closely with the software engineering team. They are very smart guys and **came up with the model of migrating a monolithic application into a microservice one**. Because we are a small organization, we don't talk to each other using ServiceNow. While we need to fit the ServiceNow ticket, **we are on very short communication lines**. If there is any problem, you can ping one another directly.

There's nothing like waiting half an hour until someone picks up a critical ticket. If there's a critical error, we can address it immediately.
So, the fact that we are a small team and work very closely together makes it a very good workplace, in my opinion.


Again having that sence of ownership gives you alot of pride actully. As I said, it givesm me pride. I dont knwo Zahra's think but, so the fact that we build that from scrach


It is very hard to find finantial company which is very hevealy regulated and wich alwayse gives you degreed of freedom

I understand how that kind of policy works, but Allianz is not like that. They are really well-regulated. At the moment, we are working with PWC on auditing some aspects of IT operations, so I need to provide them with a lot of boring reports, documentation, and stuff like that. Obviously, we are not a wild kind of company; we are still under the law.

But on the IT side, as long as we play within the rules and don't leak customer data, we are left alone. We can do what we want. That's a very good aspect

Plus, we have a flexible working environment. As I said, we work mostly remotely and only need to come to the office once a week. Other companies are different; I know JPMorgan has a three-day-a-week office policy, and some companies force people to come to the office full-time. It is not like that here.


I hope I answered your questions.So sence of Ownership plus flexible work enviroments

**Interviewee:** 
I completly agree, Lot of company that I worked for as the same . It very locjkked down, you dont get make a lot of decisions regarding tecnologoes stuff and everything standrazied, sounds really intresting 

**K:** 
Have you worked in an environment where you needed to build something from scratch and choose the best possible technology? Or have you been given tasks, like building servers from scratch? Do you have any experience in an environment like that? It doesn't have to be regulatory, just any relevant experience?





**Interviewee:** 
Alot of stuff that I worked on would have been myself like full autonomy over what I do, I developed websites and applications in the past. Wherby I got full atanomy over what I've done. What framework I'm ganna use, what architecure tio use

There are some example which not neccery be documeneted on here. I guss with fidelity that applicatiins planed out and deployed and deliverd for team, that would probably closest thing that I could mentioen

**K:** 
Any other questions?

**Interviewee:** 
No, that's all the questions I have for now. Appreciate you answering those.



So, we'll be in touch with Ellen by the end of this week. I need to talk to my boss, he is in Munich at the moment, once he comes back, we'll talk to him
We'll let you know before the end of the week if that's fine


**K:** 
What do you think?
What he was saying was that they had one gigantic k8s cluster with multiple name spaces; they want to keep the cost in check basically on those.
This is a problem with contractors we have because they usually have no saying in how the IT is built, they come and do stuff
He said that they generated some reports in sql server, he doesn't sound like somebody who did a lot of releases

**We are exceptions** in many ways because we handle running applications end-to-end, including solving incidents. When I joined Allianz, I asked Olex about this. I asked where the production support was in this case. He said that there is no one. So, we do everything end-to-end, which is quite unusual in a company of this size.
 
So he said he does his part; he has a very ****narrow point of view.** However, somebody else in India most likely handles all the incidents. This is where ServiceNow comes into play.

Last night, we had an issue where we were supposedly under attack from some hackers. We noticed a **very heavy load** around 6 PM. We had to stop one of the applications in ASE because it was **being hammered continuously**. It's back up now. We are working with Dave at the moment to figure out if we should raise it with security. In my opinion, we should.

But mypoint is, usually this kind of work would be done by somebody else, that wouldn't be me or you. We are just building stuff. Mostly that should be done by somebody else in some other organization

He has a very narrow field, but as you noticed, he worked for the company for a short time. He usually comes to help the company temporarily. He is not a person who takes ownership of anything, really, which is worrying to some degree because we have three more guys, and I expect we are going to get something senior from them. 
Let's just see. I didn't like him for this role. I'm not going to give him negative feedback yet until we speak with the other guys.



 
The problem with contractors is that they are paid per day, so he would get around 550 Euros per day for working for us. That doesn't mean he gets all that money; it goes to the agency that hires him, and they get some percentage of it. Essentially, he has **no incentive to improve things**. He wants to work as long as possible and milk us for that money. That's going to be a problem with contractors. It's a good point to focus them on the skills we need and tell them exactly what we expect from them.


I get that his feedback is negative. It’s similar to mine, but let's just wait before we send feedback to others, okay?
As I said, it's up to you. You can join the interview. Sometimes I ramble a lot. You can join and listen; it’s up to you.

It doesn't matter. If you have questions, just step in. So what I do is at the end, I leave 15 minutes for questions. If you don't join in many sections, you can practice joining the last section, which is when they ask questions. You can answer some of the questions or ask them follow-up questions. 
But you are a certified engineer, you have experience with Kubernetes, and you build stuff on your own. There is no reason why you wouldn't ask those questions.
Think about this. I'll leave it to you, okay?
