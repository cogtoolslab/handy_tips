# Interview Tips

*Tips for interviews, mostly for research internship positions. Written by Felix after an interview with [AI2](http://prior.allenai.org)*

*thanks to (among others): Ronen and Cameron*

## Coding interviews
* ask questions
* an interviewer will often (but not always) stay in the room with you
* start with pseudocode/general structure (and check that it makes sense)
* keep talking to the interviewer and make clear your thought process
    * practice talking out loud while coding in preparation
* keep in mind potential limitations, extensions and how you might address them
* be prepared to be asked questions about your code & design, for example:
    * why choose this loss over another loss function?
    * what is a potential bias of this sampling procedure?
    * how could this be optimized?
* the aim to convince the interviewers that you can think through problems and solve them in real world settings in a team, not some raw coding ability

### How to prepare?
* consider the work that you'll be doing, the interview will likely aim for checking that you'll be quick to get up to speed with the work and the frameworks they use
    * for AI2, the coding problem was using a sim2real framework to create a dataset and to train a simple model on the dataset
* for research, they want to see general competency in thinking through problems and writing code, but nothing too fancy/technical. You probably won't get algorithm/data structure riddles in a research interview
* one way of preparing general Python skills is doing [leetcode problems](https://leetcode.com/problemset/all/)
* the coding interview is likely just a filter: you have to be good enough, but it's not sufficient by itself

## Research interviews
* will likely include a section on your research experience
* and a section on what you're interested—have a project pitch prepared
    * think of something that can be done in three months and be written up as a publication
    * the incentives of the researchers who will take you on and most likely make hiring decisions are to publish
* you'll likely have a lot of room to steer the conversation

### How to prepare?
* if you know who will be interviewing you, read their papers and find overlap with your work/interests
    * come up open-ended questions on their work (you can always ask how one study generalizes)
* prepare a project pitch for a potential project
* have prepared a 3 sentence summary of your research interests

## Industry interviews
* unlike research-specific roles, these may focus more on analytic skillsets since you're more likely to be working with real company data for an applied project
* See if the company/team has a blog; companies like [Microsoft experimentation](https://www.microsoft.com/en-us/research/group/experimentation-platform-exp/) , [Stitchfix](https://multithreaded.stitchfix.com/blog/), Apple, etc. often publish about their methods and recent projects.   
    * If the team doens't have a blog, check out other companies where they do, or even better, look up team members on LinkedIn and check their past companies/roles for content
* interviews will likely consist of 3 main parts: technical/content screen, coding, and behavioral (sometimes with more/less rounds)
    * Following an application, there is sometimes a first screen with HR which is not technical and just about the role and gauging interest, then you may get a take-home coding/data challenge or start with a technical screen
    * Coding tests are *rarely* technically difficult

### How to prepare?
* if you know who will be interviewing you, read their papers and find overlap with your work/interests -- even in industry, a lot of managers and senior members have past research experience
    * unlike research roles, you're unlikely to have to discuss the work directly, but mentioning their topics in passing is a great way to score points
* Master one language for analysis (either R or Python) -- don't fret about learning both, very few teams will test coding in more than one language
* Learn SQL, it's ubiquitous in industry and very easy to pick up
    * check out [stratascratch](https://stratascratch.com) -- even the free version has updated sql questions from major companies
* For datascience/analytics roles, focusing on dataframes (aggregation, filtering, etc.), string manipulation (reverse a string, find matches, etc.), loops and functions, and core libararies can be more important than classical leetcode style software engineering problems

## How to get an interview?
Most interviews come through interactions with researchers in the company/institution who give you a referra (ie. give your name to the HR department, telling them to invite you for an interview), not through applying through the normal channels (you might need to apply anyway, but it's not sufficient by itself).
Don't spend a lot of time trawling job boards—networking is the most important part of the process.
Rather,
* ask around in your network who has done interviews
* talk to people and ask them about recommendations for places/people at places that do relevant work
* identify people in institutions that do work that you're interested in
    * is there a connection in network that can refer you?

After you've identified a few people (wj), you can ask them about their experiences and recommendations.
If you have someone to set up a meeting with that person, great. If not, write them a cold email (scary, I know) that describes who you are, what you're interested in, mentions that you're exploring "internship opportunities" and asks for a chat with that person about their research and (if applicable) their experiences doing an internship. Tailor these to the recipient, of course.

Here's an example of one I sent:
>Hello Yonathan,\
>I'm a third year PhD student in cognitive science, working with Judy Fan and Marcelo Mattar at UCSD. 
>My work is on planning and physical reasoning, especially how to develop autonomous agents that interact with the physical world as robustly as humans do. 
>In my research on planning, I focus on classical planning algorithms and modern extensions as applied to reasoning in rich, physical environments. 
>
>I am currently exploring research internship opportunities in this research area for next summer. 
>I thought you'd be a great person to reach out to given your extensive experiences working on planning both in academia and at MSR (especially your work on tree search!) I'd love to learn more about potential internship opportunities at MSR. Would you be available for a brief chat sometime in the next few weeks? 
>
>Best,\
>Felix Binder

You can send these emails by Judy or other folks in the lab for a "sniff test".

From these chats, try to get:
* procedural knowledge (*"hey this is my current approach—this is how I've approached it so far. I go on peoples website, see where they worked, go that's cool and that's how I become aware of recruiting organizations. I know that there are sometimes ads/listing, but I've heard that cold applications is not a good strategy. Has that been your experience? How have you identified opportuinites and secured offers?"*)
* Your experience working in places (*"Did you have a good experience working there? Working with them?"*)
* New contacts (*"Would they be okay with me reaching out to them?","Do you think an introduction would be more effective?", share CV, "Do you think they would be available to talk research opporunitites?", "Are there papaers/ other research outcomes I can take a look to see ifits a great fit, and if so, can I reach out to you again to see if you can create a connection/pass on CV (based on knowing what make me a good fit for that infomation)*")

Come prepared and be clear about what you want to get out of the conversation—this'll make the other person feel good about the conversation, since they helped you.


## Resources
* [Guide for Google Interviews](https://docs.google.com/presentation/d/1_6c6eu1oaDcJeKGcu43wtal8OeFNL6xMmmoSiDt9l5A/edit#slide=id.g3b1a8a6735_157_56)

