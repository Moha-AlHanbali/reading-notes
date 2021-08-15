[Home](README.md)

<br>

# REST

<br>

## Readings from [What Google Learned From Its Quest to Build the Perfect Team](https://www.nytimes.com/2016/02/28/magazine/what-google-learned-from-its-quest-to-build-the-perfect-team.html)

<br>

### New research reveals surprising truths about why some work groups thrive and others falter.


<br>

#### Quotes From The Article

<br>

> In Silicon Valley, software engineers are encouraged to work together, in part because studies show that groups tend to innovate faster, see mistakes more quickly and find better solutions to problems.

>  Studies also show that people working in teams tend to achieve better results and report higher job satisfaction.

> No matter how researchers arranged the data, though, it was almost impossible to find patterns — or any evidence that the composition of a team made any difference.

> Team members may behave in certain ways as individuals — they may chafe against authority or prefer working independently — but when they gather, the group’s norms typically override individual proclivities and encourage deference to the team.

> Understanding and influencing group norms were the keys to improving Google’s teams. 

> What distinguished the ‘‘good’’ teams from the dysfunctional groups was how teammates treated one another. The right norms, in other words, could raise a group’s collective intelligence, whereas the wrong norms could hobble a team, even if, individually, all the members were exceptionally bright.

> Second, the good teams all had high ‘‘average social sensitivity’’ — a fancy way of saying they were skilled at intuiting how others felt based on their tone of voice, their expressions and other nonverbal cues.

> In other words, if you are given a choice between the serious-minded Team A or the free-flowing Team B, you should probably opt for Team B. Team A may be filled with smart people, all optimized for peak individual efficiency.

> Within psychology, researchers sometimes colloquially refer to traits like ‘‘conversational turn-taking’’ and ‘‘average social sensitivity’’ as aspects of what’s known as psychological safety.

>  There were other behaviors that seemed important as well — like making sure teams had clear goals and creating a culture of dependability.

> The behaviors that create psychological safety — conversational turn-taking and empathy — are part of the same unwritten rules we often turn to, as individuals, when we need to establish a bond. And those human bonds matter as much at work as anywhere else. In fact, they sometimes matter more.

<br>

#### The Gist

<br>

- Having a team of competent people is surely important to have a successful team, but what matters more is that poeple who work together get to know each other, respect each other and their work.

- Teammates ought to set `guidelines` for their work and interactions, not supposedly strict, but enough to organize discussions and work sessions.

- Understanding and organization tend to increase team productivity more than individual skills.

<br>

## Conclusion of Readings from [conversation-about-rest](https://gist.github.com/brookr/5977550)

<br>

- Who is Roy Fielding?
    - A man who has helped write the first web servers, that sent documents across the internet, and then he did a ton of research explaining why the web works the way it does.

- Why don’t the techniques that we use today work well when we need to be able to talk to all of the machines in the world?
    - Most of the techniques developers later used to get computers to talk to each other just needed to talk to a small group of machines.

- What is the HTTP protocol that Fielding and his friends created?
    - `Hypertext Transfer Protocol`, this protocol is all about applying verbs to nouns(URLs). For instance, when you go to a web page, the browser does an HTTP GET on the URL you typed in and back comes a web page.

- What does a `GET` do?
    - Systems would retrieve information from each other using a simple `HTTP GET`.
    
- What does a `POST` do?
    - If one system needs to add something to another system, it would use an `HTTP` verb of `POST`. 

- What does `PUT` do?
    - If a system wants to replace something in another system, it uses an `HTTP` verb of `PUT`.

- What does `PATCH` do?
    - If a system wants to do a partial update, it'll use `PATCH`.

<br>

- Geocoding API
    - Did you get your API key?
        - Yes.

- Weather Bit API
    - Did you get your API key?
        - Yes.

- Yelp API Docs
    - Did you get your API key?
        - Yes.

- The Movie DB API Docs
    - Did you get your API key?
            - Yes.
