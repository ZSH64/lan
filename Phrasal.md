- That was a mandatory thing that needed to be done
- Did you consider using any other managed services?
- did you have some windows between where you kept the old server and you need to bring the new service? **how was that process orchestrated?** how did you do that?
  So, to keep the application live, you need to **bring a new instance** of the server and **flip traffic to a new one**. So, how did that process work in detail on the technology side?
- There were some problems I had to overcome
- I **wrote** some **Powershell script**
- **terminating the old server** when it is **no longer used** to save cost
- You need to **roll out** the new **windows images**.
- **Terraform** handles a very **narrow set of tasks**
- How much of that was automated? You mentioned Terraform, but Terraform handles a very narrow set of tasks. So, how much of the entire journey,from **kicking off this process** to **decommissioning the old servers** was automated?
- I got to the stage where I had ...
- There is a bit of a manual process around running SSL binding
-  There is a good operational document around that
-  so, Terraform is a relatively new technology to me.
-  That was my first exposure to Terraform.
-  It is pretty easy to pick up when you use Terrafom
-  Once you have a server, you flip the traffic to the new stack. How did you know the new stack is working correctly? if there is **feature parity** between the old one and the new one.
-  so **there is a set of tasks need to be performed**there is a set of tasks need to be performed
-  do you have the motoring at the top of the stack?
-   so initially, in the early days, yes, I was handling those L1 and L2 issues.
-   I documented the most **common recurring issues**
-   So what is the **correlation** between k8s and cost management?
-  The idea was for the team to **do more with less**. I don't know the **business driver** behind it.
-  we **got an understanding of** what technology they were using
-  How did you handle situations where a team **overused the cluster** resources, such as excessive memory and CPU consumption?
-  I was not personally involved in it.
-  I was developing a utility to **sniff out** **dormant** namespaces
-  Have you provisioned your own K8s server or K8s cluster, even **aside from all your work experience**?
-  Did you do that for **your own purposes as exercises**?
-  What **advantages do you** see in using K8s in general?
-  The idea is to do more with less. I see it as a good way to **keep costs in check** and ensure smooth operations in the firm.
-  Do you see any workload that you'd never put in K8s for some reason? If I told you we have a cluster of VMs and want to **cut the costs by** moving them all to K8s, is there any use case you consider **not suitable** for K8s?
-  No, Nothing that I can think of
- Do you have any hands-on experience with managing Linux or operating Linux VM?
- **Predominantly**, Windows really. I know I would have done releases in previous banking roles in Linux, but **it would have been predominantly** Windows.
- In order to **retrieve data** and **report on** that information, we had Ansible scripts running **to pull that information** and **report it back** to create a **consolidated dashboard**. That was probably one example of using Ansible.
- **Aside from** DataDog, did you use any other similar tools? **I believe** DataDog is for **collecting and presenting metrics**. It's a **comprehensive data management tool**.
- You can also **do synthetic load testing**, **similar to stress testing** within the application, without going into too much detail.
- We had **non-functional requirements** that the API **response time should be** under 300 milliseconds,So, we were able to do **stress testing**
- Does DataDog have log aggregation? or are they primarily metrics?
- DataDog can **tail logs** as well. You can see the logs and **visualize** them within DataDog.There is a **cost associated with** how many logs you are consuming, so you can just tail certain logs.
- I used Splunk **pretty heavily** at Allianz.
- Calico is central plugin for your network
- I've heard about Istio but haven't had much **exposure to** it.
- We do a lot on managed sql
- Have you done the release management of the SQL database schema? When you release applications, you sometimes need to update the schema in sql server.
- The team would **raise** a **Change Management Request** in ServiceNow, **go through CAB**, and then we work **in tandem with** developers to release whatever changes they had into Production
- We had a good management **process in place**, and everything was often documented regarding the **sequential steps** to follow for those releases.
- Your job was just to do **hands-on releases** on whatever software was required to be released, right?
  - deploying the application manually
- We are **approaching** 45 minutes  at the moment.
- we have a lot of independence in our technology choices
- So it was up to us to create the infrastructure, aside from choosing the cloud provider, because that decision was made for us. We didn't have any say in choosing **Azure as opposed to AWS**.
- We built it from scratch, which is why I like working here—I have full ownership of the entire stack.
  



  
