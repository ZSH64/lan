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

Lets tallking about your experience.



