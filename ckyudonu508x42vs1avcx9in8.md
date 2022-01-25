## Bus Factor in Software Engineering


# 1. Introduction
Imagine that John Doe works on a project along with 7-10 folks. John started 
working on this project from the beginning and therefore knows a lot more than everyone else in the project.

These leads to some problems such as:
1. John is the go-to person for each detail that the team needs. John has a lot of responsibility and workload on his shoulders, making his progress sometimes slow.
2. Whenever John falls sick and goes on unplanned leave, he is bugged by his team to keep things moving forward in the project.
3. The organisation finds it hard to replace John and has therefore retained him twice in the past year by raising his compensation twice.

> In short, the project has a single point of failure -> John Doe


# 2. What is Bus Factor?

As per Wikipedia, The bus factor is a measurement of the risk resulting from information and capabilities not 
being shared among team members, derived from the phrase "in case they get hit by a bus". 
It is also known as the bread truck scenario, bus problem, beer truck scenario, lottery factor, truck factor, 
bus/truck number, or lorry factor.

In simple words, what is the probability of the project failing if John Doe gets hit by a bus and is not able to return to work? 
> Higher the bus factor higher the risk of failure. 


# 3. Reducing/Preventing the Bus Factor in Software Development

## 3.1 Documenting
Creating and maintaining documentation can take a good amount of effort from all 
the stakeholders. But in the long run, it is worth documenting. Documenting includes Product Requirement
Documents(PRDs), High & Low-level design documents, changelogs, READMEs, complete ticket descriptions on ticketing tools, 
Root Cause Analysis documents in case of production fires, etc

## 3.2 Code Reviews 
If done effectively, code reviews can act as an excellent tool to reduce the bus 
factor, given that everyone in the team gets a chance to review the code. 
The Engineering manager/team lead should make sure that there are relative code 
review guidelines set up as per the team so that it is effective enough.

## 3.3 Meetings
Yes, I know meetings sometimes slow us down and hinder our productivity. Also, some meetings can 
just be replaced by an email. But, meetings (especially if you are working remotely) can actively reduce the 
bus factor if done correctly. Meetings like standup, sprint planning/grooming, design discussions, 
sprint retros etc bring everyone together as a team. Imagine you reading a minute of meeting document vs
actually brainstorming in the meeting. **Meetings do not replace the documentation. Instead, the
documentation complements the meeting process.**

## 3.4 Team Process
More team processes can improve the knowledge distribution in the team like:
- Pair programming
- Office hours
- On-call rotations
- Engineering demos 
- Knowledge sharing sessions


## 3.5 Positive Work culture
A positive culture means employees are happy in the organisation and a better work environment is created. 
Following techniques can be applied to improve the work culture and reduce the bus factor:

### 3.5.1 Mandatory Paid Annual Vacation 
Most of the organisations provide paid leave to their employees. The organisations should also encourage
people to use these leaves and go on a vacation(for a week at least). This will enable other employees to take
care of work in the absence of an employee. 


### 3.5.2 Short Notice/Termination Period
A short notice period means, the organisation making sure that there is less dependency on an employee. 



# Conclusion
The first step is to talk about Bus factor in your team, even if you are a junior member in
the team. Maybe, some of the above methods like meetings, code reviews, documenting etc.
are already being used in your organisation for sharing knowledge. You can consider optimising those methods to reduce/prevent 
the bus factor in your team. For eg, you can consider including the junior members of your
team in meetings and code reviews. The members with a centralized knowledge can work on
spreading their knowledge in the team so that they can spend their time and energy on 
something new for the team. 

What do you think of Bus factor in your team? Do you have more methods to prevent high bus
factor? Feel free to give your feedback!