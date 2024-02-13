_This document is looking at a specific collection on the library of congress_

 

# Pale Blue Dot and Other Pixels

## Standard View Html

 

This is a look into the world of 'down and dirty' data, essentially data in the wild.

In this case, our example is taken from the [Library of Congress](https://www.loc.gov). 

In the world of design, some research has claimed,

> [A] schematic display of textual information improves perceptions of information quality. When a picture of the product appears together with textual information, users remember more information and consider it easier to remember if that information appears schematically. However, without a product picture, users allocate more resources to process paragraph information and therefore recall more information and perceive it as easier to recall.[^1]

In the case of the Library of Congress, I tend to agree; here, it feels like the common phrase "a picture is worth a thousand words" more than applies; Yet I can't say how many of those words I remember.

The first thing you notice when arriving on the website is the curated images in the Featured Content on the main page that immediately invite you to start [exploring](https://xkcd.com/214) by delving into some topic. If you resist the urge, your eyes are then drawn further down to the list of Digital Collections.

You notice that for each collection, the layout is in the form of

- A relevant picture
- Category (in this case, it’s just 'collection')
- Title
- Short summary
- Meta data (number of items in the collection)

Personally, the images were what caught my eye first, before anything else. Yet I felt overwhelmed by the amount of choices[^2]. Thankfully, prominently on the left-hand side was a way to filter these choices into something much more manageable.

So how did I filter?

I recently watched a [YouTube video](https://youtu.be/fG8SwAFQFuU?si=Eg1Ozdhur4K3w0aj), from someone I follow, and the responses he got surprised me, curated though they may be. I had assumed a bit of what he said was common knowledge, which really reveals some of my biases and preconceptions about common knowledge. I also don't have a leg to stand on; ask me about the names of anywhere in Barbados more than a mile from my home, and I _guarantee_ I don't know them.

What's my point here, and how does this connect to the Library of Congress?

Well, ideas about the universe are fresh in my mind, so I filtered by Science and Technology and then immediately stopped at the collection entitled [*Finding Our Place in the Cosmos: From Galileo to Sagan and Beyond*](https://www.loc.gov/collections/finding-our-place-in-the-cosmos-with-carl-sagan/about-this-collection/) which really clicked with me.

The collection describes itself with the following words:

> A thematic collection exploring changing models of the universe through time, ideas of life on other words and Carl Sagan’s place in the tradition of science. It features manuscripts, rare books, celestial atlases, newspaper articles, sheet music and movie posters.


I dove in through its Featured Content starting with the childhood movies.

My general thoughts on the collection itself were that it was more than interesting.

- [The silent movie](https://www.loc.gov/item/cosmos000112) confused me since I really should have read the description where the word silent would have saved me a lot of confusion, but then I started to wonder just how voyeuristic this truly was to see what the parents had captured as their own personal and intimate moments with their family (that and it being again, silent) made me move on quickly.
- [the draft for a pale blue dot](https://www.loc.gov/resource/mss85590.042/?sp=4&st=image) was another interesting note. I'm more familiar with the image of the same name and even the [video.](https://youtu.be/GO5FwsblpT8?si=3E8d97qBzsg49Fd-)

 

So, what were my thoughts on the experience itself?

- This feels quite organic; it’s easy to simply click on what I'm interested in and engage, rather by watching or reading and moving on as I wish.
- Having the digital articles to interact with was easy and intuitive as well, although it was at times much too easy to ignore the contextual information.
- Distractions abound; sometimes it was more desirable to click on related content on each thing rather than stay on task and explore that single collection.
- A systematic exploration was not convenient; I know I didn't go through all the material, and with a point-and-click interface, it's hard to engage in such a repetitive manner. Drilling in on a specific topic is much easier than trying to capture any form of overview of the data.


Personally, as a user, this is the best way to go about it, unless you're trying to summarise or gain any other form of insight about the group.


 
# The Matrix Red Pill Blue Pill
## JSON in the Browser

The idea that there's something behind what we see has always existed in our society's consciousness; this especially shows itself in our media. The same collection I've been examining considered what life may exist on the Moon[^3] or on Mars[^4]. Movies have also shown this, for instance in 'They Live'[^5], yet the move that stands out to me is the Matrix[^6]. It showed that the world's front end has a back end, and only through the right 'pill' did our hero really get to see the messiness behind it.

JSON is a similar backend for this website. One definition is the following:

>JavaScript Object Notation (JSON) is a standard text-based format for representing structured data based on JavaScript object syntax. It is commonly used for transmitting data in web applications (e.g., sending some data from the server to the client so it can be displayed on a web page, or vice versa).[^7]

When I explore the JSON for this collection via the browser, it's a completely different experience. Gone are the pictures and carefully tailored UX, what's left is just text and brackets—lots and lots of brackets.

What were my experiences here?

- Exploration feels like a great reduction in ease of use and comprehension as you're overloaded with information.
- Accessing any particular digital object itself becomes difficult; you now have to find the appropriate href and follow that link.
- The overall structure for how the information is laid out is now somewhat clearer.
   - Collapsing all the brackets that have no objects in them helped me view how everything was connected and stored.
- 'Hidden' details can be found in the JSON, be it in its structure itself or simply not loaded in the HTML.

Personally, except for understanding the structure of the data, I don't see why one would interact with JSON in this manner.


# Golem Perverse Incentive
## JSON with Python

 
1. Programs can be great, as they perfectly follow instructions.
2. Programs can be horrid, as they perfectly follow instructions.

As you get exactly what you (or other programmers) put in, you can be sure that it will account for only what it was made to account for.

JSON in Python is convenient… when you know the commands to help you reach your concrete goal. Python (and any other programming language) is like a [golem](https://en.wikipedia.org/wiki/Golem) so it's neither benevolent nor malevolent, but it sure can feel so when trying to get it to do what you want.

 
What was my experience here?

- Honestly? Frustrating, but that's on me. I simply got caught up in trying to get something done that I hadn't learned how to do.
- Once it works, it works well.
- I can easily imagine anyone with the prerequisite programming language would find this to be the superior choice, especially in the situation of repetitive tasks.


See below for the code used.
```python

 

### Import Packages
import requests
import json

### Connect to the Website

r = requests.get('https://www.loc.gov/collections/finding-our-place-in-the-cosmos-with-carl-sagan/?fo=json&at=results')
r.status_code # Check the status code of the connection

# r.json() # We can access the json directly this way without loading json
# r.headers['Content-Type']

### Get JSON
j=json.loads(r.text)
print(json.dumps(j, sort_keys=True, indent=2)) # Print JSON with some formatting

print(j.keys()) # Print the keys of the json object.

### Analyse JSON

# Function to get the structure of JSON, where 'VALUE' is the first time data is seen and '...' is a repeat

# This function is NOT a testament to any skill of coding on my part (there is none), but rather just a testament to stubbornness and googling
def explore_json_structure(data, seen_values=None):
    """

    Recursively explores the structure of a JSON-like object (dictionary or list).

    Args:
        data: The JSON-like object to explore.
        seen_values: Set to track seen values (optional).

    Returns:
        A representation of the structure (e.g., nested dictionaries or lists).
    """
    if seen_values is None:
        seen_values = set()
    if isinstance(data, dict):
        if len(data) == 1:
            key, value = next(iter(data.items()))
            return {key: explore_json_structure(value, seen_values)}
        else:
            return {key: explore_json_structure(value, seen_values) for key, value in data.items()}
    elif isinstance(data, list):
        if len(data) > 1:
            return [explore_json_structure(data[0], seen_values)]
        else:
            return [explore_json_structure(item, seen_values) for item in data]
    else:
        if data not in seen_values:
            seen_values.add(data)
            return "VALUE"
        else:
            return "..."







j_struct = explore_json_structure(j)
print(json.dumps(j_struct, sort_keys=True, indent=2))

# We can use j_struct to drill down to whatever we wish to see and simply replace it with j to get the actual data.
# Personally, I find it a little easier, so the console is not as 'busy'.

j_struct['results'][0]['aka']
# ['VALUE']

j['results'][0]['aka']
#['http://lccn.loc.gov/00522095',
# 'http://www.loc.gov/item/00522095/',
# 'https://hdl.loc.gov/loc.rbc/Vollbehr.22905',
# 'http://www.loc.gov/resource/Vollbehr.22905/',
# 'http://www.loc.gov/resource/rbc0001.2012vollb22095/']
```

## Command-line View

### Interesting Aspects
- **Control**: The command-line view provides powerful control over computer systems. It's efficient and scriptable.

### Difficulties
- **Learning Curve**: Command-line interfaces have a steep learning curve. They are not as intuitive as graphical interfaces.


# References

[^1]: [Effects of visual and textual information in online product presentations: looking for the best combination in website design](https://doi.org/10.1057/ejis.2010.42)
[^2]: [Why More Choices Don't Make You Happy](https://youtu.be/hTRBAjYGjsI?si=j5_6CM-_KMQ7reqF)
[^3]: [Peoples & Creatures of the Moon](https://www.loc.gov/collections/finding-our-place-in-the-cosmos-with-carl-sagan/articles-and-essays/life-on-other-worlds/peoples-and-creatures-of-the-moon/)
[^4]: [Envisioning Martian Civilizations](https://www.loc.gov/collections/finding-our-place-in-the-cosmos-with-carl-sagan/articles-and-essays/life-on-other-worlds/envisioning-martian-civilizations/)
[^5]: [They Live (1988)](https://www.imdb.com/title/tt0096256/)
[^6]: [The Matrix (1999)](https://www.imdb.com/title/tt0133093/)
[^7]: [Working with JSON](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/JSON)
