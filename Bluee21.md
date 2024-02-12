# Introduction


## Solo Exercise
https://www.loc.gov/collections/african-american-photographs-1900-paris-exposition?fo=json&at=results

**1. The JSON format**
   -  The data is structured hierarchically, with key-value pairs defining various aspects of each item. This hierarchical structure allows the encapsulation of related information within each container, allowing clarity and organization of the data.
  
   - Arrays are used effectively to handle cases where there are multiple values associated with a single attribute. For instance, the "subject_headings"  key contains an array of five strings, each representing a different subject related to the item. These subjects include specific topics such as the Tuskegee Normal and Industrial Institute, African American education in Alabama, students in Tuskegee, classrooms in Tuskegee, and the state of Alabama itself.
     
   - The dataset showcases the use of complex objects to encapsulate detailed information about each item. For instance, the "item" key contains nested attributes such as "call_number", "control_number", and "created", which offer insights into the bibliographic and archival aspects of the items.
     
- This view allows you to know more about the data such as creation date, location, format, and associated subjects.

 The JSON view presents the data in a structured format, with keys and values providing information about various attributes of the collections and items. This structured representation allows for easy navigation and understanding of the data. This is view is not for an average person. It doesn't allow for that seamless flow that you would get from a webpage and you have drive in deeper to get access to the information. Although, it is easy to follow it is not ideal to look at.
  
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
- view option to change the how the content is displayed to the user
- each collection is displayed in a container that displays a photo of item, the format of the item, the title/ name of item, a breif description, date, and contributor about that particular item
- side bar panel with additional filter links to other parts of the collection to refine the search results (e.g. you can filter to items dated from 1900 to 1999)
- page numbers and page count (results: 1-25 of 557)
- an option to change how many items are displayed on the page at a time 

**Footer:** 
- reasources, contact information, social media links and copy right logo
  
The interactive element makes it easy the average user to navigate through the content. It is visually appealing and helps with easy engagement of the web pages. Hyperlinks and embeded media elements allows for seamless navigation to different parts of the webpages and other datasets. Its user-centric design and interactive features make it a easy for people seeking to extract data from complex datasets. The use for this view is deliver a user-centric design with an interactive feature for displaying the content.

-----

**3. The command-line view**

With this view keys are enclosed in quotes and followed by a colon, and values can be of various data types, such as strings, booleans, lists, or nested dictionaries. The structured metadata accompanying each item allows for comprehensive documentation and retrieval of information.  The ability to retrieve data using Python's requests library and parse it with `json.loads()` makes the collections easily accessible for manipulation and analysis within Python environments. The data retrieval process shows that API integration with external APIs is possible. Possible use could be the use of the Library of Congress collections API for future development on similar projects. 



