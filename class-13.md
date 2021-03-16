# [THE PAST, PRESENT & FUTURE OF LOCAL STORAGE FOR WEB APPLICATIONS](https://diveinto.html5doctor.com/storage.html)

## New research reveals surprising truths about why some work groups thrive and others falter.
Persistent local storage is one of the areas where native client applications have held an advantage over web applications. For native applications, the operating system typically provides an abstraction layer for storing and retrieving application-specific data like preferences or runtime state. These values may be stored in the registry, INI files, XML files, or some other place according to platform convention. If your native client application needs local storage beyond key/value pairs, you can embed your own database, invent your own file format, or any number of other solutions.

- Working in teams can produce a wide range of results. It's up to us how we approach the team, and we contribute.
Historically, web applications have had none of these luxuries. Cookies were invented early in the web’s history, and indeed they can be used for persistent local storage of small amounts of data. But they have three potentially dealbreaking downsides:

- In 2015, Google launched Project Aristotle - to study hundreds of Google’s teams and figure out why some stumbled while others soared. 
- Cookies are included with every HTTP request, thereby slowing down your web application by needlessly transmitting the same data over and over
- Cookies are included with every HTTP request, thereby sending data unencrypted over the internet (unless your entire web application is served over SSL)
- Cookies are limited to about 4 KB of data — enough to slow down your application (see above), but not enough to be terribly useful

### Project Aristotle:
What we really want is

  - Reviewing a half-century of academic studies looking at how teams worked.
  - Were the best teams made up of people with similar interests?
  - Did it matter more whether everyone was motivated by the same kinds of rewards? 
  - How often did teammates socialize outside the office? 
  - Did they have the same hobbies? 
  - Were their educational backgrounds similar? 
  - Was it better for all teammates to be outgoing or for all of them to be shy? 
  - They drew diagrams showing which teams had overlapping memberships and which groups had exceeded their departments’ goals. 
  - They studied how long teams stuck together and if gender balance seemed to have an impact on a team’s success.
  - Results were inclusive:
- A lot of storage space
- On the client
- that persists beyond a page refresh
- and isn’t transmitted to the server

    - Some groups that were ranked among Google’s most effective teams, for instance, were composed of friends who socialized outside work. 
    - Others were made up of people who were basically strangers away from the conference room. 
    - Some groups sought strong managers. 
    - Others preferred a less hierarchical structure. 
    - Most confounding of all, two teams might have nearly identical makeups, with overlapping memberships, but radically different levels of effectiveness. 
## A BRIEF HISTORY OF LOCAL STORAGE HACKS BEFORE HTML5

### Group Norms
In the beginning, there was Internet Explorer. which included DHTML Behaviors, and one of these behaviors was called userData.

  - Research was noted by psychologists and sociologists that focused on what are known as ‘‘group norms.’’ 
- userData allows web pages to store up to 64 KB of data per domain, in a hierarchical XML-based structure. (Trusted domains, such as intranet sites, can store 10 times that amount. And hey, 640 KB ought to be enough for anybody.) IE does not present any form of permissions dialog, and there is no allowance for increasing the amount of storage available.

    - Norms are the traditions, behavioral standards and unwritten rules that govern how we function when we gather:  
In 2002, Adobe introduced a feature in Flash 6 that gained the unfortunate and misleading name of “Flash cookies.” Within the Flash environment, the feature is properly known as Local Shared Objects. Briefly, it allows Flash objects to store up to 100 KB of data per domain. Brad Neuberg developed an early prototype of a Flash-to-JavaScript bridge called AMASS (AJAX Massive Storage System), but it was limited by some of Flash’s design quirks.

      - One team may come to a consensus that avoiding disagreement is more valuable than debate 
      - Another team might develop a culture that encourages vigorous arguments and spurns groupthink. 
      - Norms can be unspoken or openly acknowledged, but their influence is often profound. 
      - Team members may behave in certain ways as individuals — they may chafe against authority or prefer working independently — but when they gather, the group’s norms typically override individual proclivities and encourage deference to the team.
By 2006, with the advent of ExternalInterface in Flash 8, accessing LSOs from JavaScript became an order of magnitude easier and faster. Brad rewrote AMASS and integrated it into the popular Dojo Toolkit under the moniker dojox.storage. Flash gives each domain 100 KB of storage “for free.” Beyond that, it prompts the user for each order of magnitude increase in data storage (1 Mb, 10 Mb, and so on).

  - Project Aristotle’s researchers began searching through the data they had collected, looking for norms. They looked for instances when team members described a particular behavior as an ‘‘unwritten rule’’ or when they explained certain things as part of the ‘‘team’s culture.’’ 
In 2007, Google launched Gears, an open source browser plugin aimed at providing additional capabilities in browsers. Gears provides an API to an embedded SQL database based on SQLite. After obtaining permission from the user once, Gears can store unlimited amounts of data per domain in SQL database tables.

    - Some groups said that teammates interrupted one another constantly and that team leaders reinforced that behavior by interrupting others themselves. 
    - On other teams, leaders enforced conversational order, and when someone cut off a teammate, group members would politely ask everyone to wait his or her turn. 
    - Some teams celebrated birthdays and began each meeting with informal chitchat about weekend plans. 
    - Other groups got right to business and discouraged gossip. - There were teams that contained outsize personalities who hewed to their group’s sedate norms, and others in which introverts came out of their shells as soon as meetings began.
    - But which Norms matter most?
In the meantime, Brad Neuberg and others continued to hack away on dojox.storage to provide a unified interface to all these different plugins and APIs. By 2009, dojox.storage could auto-detect (and provide a unified interface on top of) Adobe Flash, Gears, Adobe AIR, and an early prototype of HTML5 storage that was only implemented in older versions of Firefox.

      -Was it better to let everyone speak as much as they wanted, or should strong leaders end meandering debates
      - Was it more effective for people to openly disagree with one another, or should conflicts be played down? 
As you survey these solutions, a pattern emerges: all of them are either specific to a single browser, or reliant on a third-party plugin. Despite heroic efforts to paper over the differences (in dojox.storage), they all expose radically different interfaces, have different storage limitations, and present different user experiences. So this is the problem that HTML5 set out to solve: to provide a standardized API, implemented natively and consistently in multiple browsers, without having to rely on third-party plugins.

### Carnegie Mellon, M.I.T. and Union College Test Case
## INTRODUCING HTML5 STORAGE

- Researchers wanted to know if there is a collective I. Q. that emerges within a team that is distinct from the smarts of any single member.
### HTML5 Storage

- To accomplish this, the researchers recruited 699 people, divided them into small groups and gave each a series of assignments that required different kinds of cooperation. 
A way for web pages to store named key/value pairs locally, within the client web browser. Like cookies, this data persists even after you navigate away from the web site, close your browser tab, exit your browser, or what have you. Unlike cookies, this data is never transmitted to the remote web server (unless you go out of your way to send it manually).

  - One assignment, for instance, asked participants to brainstorm possible uses for a brick. 
**All Browsers support HTML5** 

    - Some teams came up with dozens of clever uses 
    - Others kept describing the same ideas in different words. 
**You can use [Modernizr](https://diveinto.html5doctor.com/detect.html#modernizr) to detect support for HTML5 Storage.**

  - Another had the groups plan a shopping trip and gave each teammate a different list of groceries. The only way to maximize the group’s score was for each person to sacrifice an item they really wanted for something the team needed. 
## USING HTML5 STORAGE

    - Some groups easily divvied up the buying 
    - Others couldn’t fill their shopping carts because no one was willing to compromise.
HTML5 Storage is based on named key/value pairs. You store data based on a named key, then you can retrieve that data with the same key. The named key is a string. The data can be any type supported by JavaScript, including strings, Booleans, integers, or floats. However, the data is actually stored as a string. If you are storing and retrieving anything other than strings, you will need to use functions like parseInt() or parseFloat() to coerce your retrieved data into the expected JavaScript datatype.

- What interested the researchers most, however, was that teams that did well on one assignment usually did well on all the others. Conversely, teams that failed at one thing seemed to fail at everything. The researchers eventually concluded that what distinguished the ‘‘good’’ teams from the dysfunctional groups was how teammates treated one another. The right norms, in other words, could raise a group’s collective intelligence, whereas the wrong norms could hobble a team, even if, individually, all the members were exceptionally bright. But what was confusing was that not all the good teams appeared to behave in the same ways.
## TRACKING CHANGES TO THE HTML5 STORAGE AREA

- As the researchers studied the groups, however, they noticed two behaviors that all the good teams generally shared. 
If you want to keep track programmatically of when the storage area changes, you can trap the storage event. The storage event is fired on the window object whenever setItem(), removeItem(), or clear() is called and actually changes something. For example, if you set an item to its existing value or call clear() when there are no named keys, the storage event will not fire, because nothing actually changed in the storage area.

