# Meeting 1 Notes

## brainstormed ideas:
1. Continue on the market perception wave
2. make a way to get a unbiased news source 
3. make a d&d bot that generates scenarios 
4. Game guide for some complicated games
5. context for sports while its live

#### it looks like were going with number 2

## rough working plan:
1. we have to narrow down on authoratative sources of public information and public sentiment
2. Setup a cheap rag system we can test on to see if the information can be used by some model to then give us fairly good answers 
3. test and iterate on the rag until it can do something of use even with a reduced paramater count such as 7bil, which even we could run 
4. figure out how we deliver to consumers. do they clone our code and use the local service? do we try to run it somewhere and provide the service for others? 
5. execute

## general notes:

### definite necessities (what we need to confirm saturday):
1. Need acess to all mainstream news sources. We stream articles in on demand and keep a cache with lru policy. The user can then search for topics favoring more recent news to understand the points mentioned. Caveat: what can we realistically scrape for free here?

2. Model doctrine: does not add any of its own opinions. It should synthesize relevant docs and present back to the reader, little input from itself, and perhaps should have a handcoded tool that it can use to identify which document source has given it something and where that information can be found. (link to the page probably ) basically its imperative that the model does not hallucinate and that its easily verified if it does. 

### future considerations (most of these we dont even have to think about yet):
1. How is the service provided, self host or central provider. ()
2. model pipeline
3. optimizing for our specific problem. Output should be basically deterministic, you cant really ask the main producer a

## Specific first steps for saturday: 
1. get the basic thing running on both of our systems.

2. Do a test run with handpicked links, get a feel for how expensive this is in terms of compute and how we can do better than what we have by base

3. Think about what the model pipeline will look like: (note the data stuff and scraping plan depend on how we provide the service)
* what does the user tell us? do we update a table of trending topics? does user describe a topic and we go find it?
* how do we handle malicious user input, they shouldnt be able to get our service to do anything but what we claim to provide
* what kinds of models do we need? (eg. main producer, condenser, interpreter models)
* what sorts of databases do we maintain?
* How do we preprocess information before it goes in the database? 
* is there any way we can make the scraping better?  

4. decide on if we need to limit scope further. Do we need a story that is opinion to be included in this? how do we discriminate? 

5. Think about if its worth including alternative sources, possibly even try our hand at getting social media sentiment, although this could be hard to do 

# Importantly: 

what we are not doing is making something that will answer your questions about news. The end goal is to have this do objective fact summary and perhaps some commentary on the retrieved sources and information about their diferences in terms of news ouput. We favor getting exact and accurate information, and perhaps some quotes. If the model ever does happen to hallucinate, it needs to be easily identified. 

