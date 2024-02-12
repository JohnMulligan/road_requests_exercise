# Food and Foodways Web Archive 

https://www.loc.gov/collections/food-and-foodways-web-archive/

## Normal Webpage View

* There are options to filter the type of collection items seen and how these items are displayed (i.e. in a list or gallery etc.)

* Each collection item displayed has a brief description and title which makes it easy for the web user to identify a specific item.
* Each collection item displayed has a brief description, contibutor and title which makes it easy for the web user to identify a specific item.

* There's an about section which allows the web user to get a gist of what the collection contains.

* Each collection item has a very user friendly page showing the item (captures), meta data (title etc.), rights and citation information. 

> This webpage allows for seamless navigation through its content. The homepage is well organized, has helpful menu options, and has an intuitive layout that helps users easily access different sections. The navigation bar at the top provides direct links to specific collections, allowing efficient exploration of the collection. The use of a search bar further enhances user convenience for those looking for specific information within the collection. Overall, the website's view aids in a user-friendly experience through easy navigation and accessibility to the content in the collections.
## JSON Format

https://www.loc.gov/collections/food-and-foodways-web-archive/?fo=json&at=results

* The colelction data is displayed as easily readable key value pairs.

> Adding `?fo=json&at=results` to the end of the URL, as shown above, tells the server to return the contents in an array called "results" in JSON format. The "results" array consists of 24 elements, each representing a different aspect of the collection. This view provides detailed information about each collection item that may not be displayed in the web page view (i.e., timestamp information, contributor details, and access coditions.)
>  This array begins at 0: {...} to 24: {...}, representing one collection item in each array. Each item contains detailed information about a specific webpage or organization. For example, 0: {...}  contains information about Center for Science in the Public Interest (CSPI), while 1: {...} contains information about the Institute for Food and Development Policy (Food First).
> This structure allows for organised and detailed data representation for multiple items within the web collection. In essence, to view more items in the collection, one must expand the arrays and deep dive into each, expanding on the information shown in the key-value pairs to gain a better insight on this collection. 

## Command Line View

* The request object allows you view information outside of the collection data and content, like the request status (whether it was successful or not), the response time elapsed, the encoding used etc.
  * The response time could be tested to see how quickly the interface provides the requested data.

* The request object also provides the raw collection data, as a blob of text. It's not as easy on the eyes like the JSON format or webpage view.

> To access the command line view of the webpage, the user must use the `requests` library in Python to get the information from the webpage. Before you can view the data from the webpage, a GET request is sent: `import requests; 
r = requests.get('https://www.loc.gov/collections/food-and-foodways-web-archive/?fo=json&at=results')`, check the status code for connection `r.status_code`, then load the JSON data: `import json
j = json.loads(r.text)`.  `j['results']` will display all the contents of the collection together with their key-value pairs. However, if a user wants to do a more refined search to narrow the amount of data being returned, create a variable to store the contents of your results array: `data = j['results']`, which is now a list of the content, and you can now extract data from this list. For example, `for i in range(len(data)):  
  print(i, data[i]["title"])` gives you the title of every item in the collection. Having a side by side view of the webpage allows for easy navigation when drilling into the contents of the command line.
