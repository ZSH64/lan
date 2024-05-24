I have seen much around job specification or requirements, so I'd like to get an undrestanding from lets say your requirments and what you are lookimg for exactly.




I've been with Allianz since 2020, so I joined arount the peak epidemic. My role was to design and implement the infrastructure in Azure. we can talk about technology choices in a minute. I£ve been told to build up teh infrastructure 
to host the applications which are currently people from the development move from on-prem infrastrucure. we have backet of windows base applications in .net and they re-wrote large chunk of it in .net core,
basiclly the are migrated that to host on k8s
My job was build the individual environments so that we can move them those applications through those environments, make sure they are adhering to the quality, to the the security standard, to teh regulatory standard, then we could present them, to actual customers

My first job was building the k8s clusters so that we could host the applications, the applications are written in microservices pattern, so its own entities, its works on its own container, using its own database and stuff like that

We have five enviroments at the moment, the largest one is production one, that's seven nodes but that's gonna be growing pretty rapidly, apart to that we use the engine called The App Service Environment(ASE)
