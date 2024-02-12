# Introduction


## Solo Exercise
https://www.loc.gov/collections/african-american-photographs-1900-paris-exposition?fo=json&at=results

**1. The JSON format**
   -  The data is structured hierarchically, with key-value pairs defining various aspects of each item. This hierarchical structure allows the encapsulation of related information within each container, allowing clarity and organization of the data.
  
   - Arrays are used effectively to handle cases where there are multiple values associated with a single attribute. For instance, the "subject_headings"  key contains an array of five strings, each representing a different subject related to the item. These subjects include specific topics such as the *Tuskegee Normal and Industrial Institute*, *African American Education in Alabama*, *Students in Alabama Tuskegee*, *Classrooms in Alabama Tuskegee*, and the state of *Alabama* itself.
     
   - The dataset showcases the use of complex objects to encapsulate detailed information about each item. For instance, the "item" key contains nested attributes such as "call_number", "control_number", and "created", which offer insights into the bibliographic and archival aspects of the items.
     
- This view allows you to know more about the data such as creation date, location, format, and associated subjects.

 The JSON view presents the data in a structured format, with keys and values providing information about various attributes of the collections and items. This structured representation allows for easy navigation and understanding of the data. This is view is not for an average person. It doesn't allow for that seamless flow that you would get from a webpage and you have dive in deeper to get access to the information. Although, it is easy to follow it is not ideal to look at.
  
  ------
  
**2.The Webpage view**

**Header:**
   - at the top left side of the page there is the logo of the Library of Congress which is a clickable link to the home page.
   - a search bar at the top right with a dropdown menu (to help filter through a particular collection)
   - navigation menu

**Body:** 
- Page title (e.g. African American Photographs Assembled for 1900 Paris Exposition)
- Three hyperlink headings one that displays the collection items, about the collection, and articles and essays
- filter to sort the collections by (title, date, etc...)
- view option to change how the content is displayed to the user
- each collection is displayed in a container that displays a photo of item, the format of the item, the title/ name of item, a breif description, date, and contributor about that particular item
- side bar panel with additional filter links to other parts of the collection to refine the search results (e.g. you can filter to items dated from 1900 to 1999)
- page numbers and page count (results: 1-25 of 557)
- an option to change how many items are displayed on the page at a time 

**Footer:** 
- reasources, contact information, social media links and copyright logo
  
The interactive element makes it easy the average user to navigate through the content. It is visually appealing and helps with easy engagement of the web pages. Hyperlinks and embedded media elements allows for seamless navigation to different parts of the webpages and other datasets. Its user-centric design and interactive features make it a easy for people seeking to extract data from complex datasets. The use for this view delivers a user-centric design with an interactive feature for displaying the content.

-----

**3. The command-line view**

With this view keys are enclosed in quotes and followed by a colon, and values can be of various data types, such as strings, booleans, lists, or nested dictionaries. The structured metadata accompanying each item allows for comprehensive documentation and retrieval of information.  The ability to retrieve data using Python's requests library and parse it with `json.loads()` makes the collections easily accessible for manipulation and analysis within Python environments. The data retrieval process shows that API integration with external APIs is possible. Possible use could be the use of the Library of Congress collections API for future development on similar projects. 




------

## Taking a peek at the dataset

i. **Public-facing webpages** (Library of Congress collections portal)
   
 a.
   **Header:**
   - at the top left side of the page there is the logo of the Library of Congress which is a clickable link to the home page.
   - a search bar at the top right with a dropdown menu (to help filter through a particular collection)
   - navigation menu

**Body:** 
- Page title (e.g. Digital Collections)
- carousel slider with the collection's featured content
- filter to sort the collections by (title, date, etc...)
- view option to change the how the content is displayed to the user
- each collection is displayed in a container that displays the collection name, title, a brief description, and how many items are in that collection
- side bar panel with additional filter links to other parts of the collection to refine the search results
- page numbers
- an option to change how many items are displayed on the page at a time 

**Footer:** 
- resources, contact information, social media links and copyright logo

  ------

ii. **A specific collection**

a.  **Header:**
   - at the top left side of the page there is the logo of the Library of Congress which is a clickable link to the home page.
   - a search bar at the top right with a dropdown menu (to help filter through a particular collection)
   - navigation menu

**Body:** 
- Page title (e.g. 10th-16th Century Liturgical Chants)
- Two hyperlink headings one that displays the collection items and the other tells you about the collection 
- filter to sort the collections by (title, date, etc...)
- view option to change the how the content is displayed to the user
- each collection is displayed in a container that displays the format of the item, the title/ name of item, a breif description, date, contributor, and reasources to view more about that particular item
- side bar panel with additional filter links to other parts of the collection to refine the search results (e.g. you can filter to items dated from 1400 to 1499)
- page numbers
- an option to change how many items are displayed on the page at a time 

**Footer:** 
- reasources, contact information, social media links and copy right logo
------

2. **API -- same thing in a different format! Just add ?fo=json&at=results**

i. - ?fo=json&at=results returns the page content stored in an array called results
- they're 40 objects (0-39) in this array with nested objects and key-value pairs
    - an example of these array is description: [_] when expanded shows 0: array that contains a string shown in the body of the about this collection page
- keys represents different aspects of the collection
- expanding 0: {...} shows there are a list of objects and key value pairs where each object represents a specific attribute or item of the collection and its corresponding value shows the associated data ( e.g count: 55)
- the full URL is given to where a photo is located is shown in this view, whereas in the normal webpage view the photo is shown
- the full URL for the location of a photo is shown in this view, which is unlike the webpage where the photo is displayed
- the use of boolean values are shown, an example of this is "access_restricted: false" it shows you what is accessible to the public 
- timestamps of when the data was last edited
- the data is presented hierarchically, where each object represents an individual item from the collection.
- Within these objects, key-value pairs describe various attributes of the collection items.  
   
ii.
- they're 25 objects (0-24) in this array with nested objects and key value pairs
- the layout format is identical to the above mentioned with minor changes such as less objects 
-----








