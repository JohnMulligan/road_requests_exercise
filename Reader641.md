# Wright Brothers Negatives Collection

![Reader641_1](/assets/Reader641_1.png)

https://www.loc.gov/collections/wright-brothers-negatives

### My Experience with the Collection
----
My familiarity with the Wright brothers drew me to this particular collection[^1]. When I delved into it, I was struck anew by their pioneering spirit and the sheer improbability of their success.

Examining the interfaces, I found each offered distinct value:
- The portal excelled for one-time explorations, ideal for casual browsing without repetitive tasks.
- The browser-based JSON, particularly when formatted, provided a clear understanding of the collection's overall structure.
- Python-based JSON facilitated robust and efficient tasks, like retrieving specific text elements.

While the collection itself held no surprises, it nonetheless served as a valuable reminder of the Wright brothers' remarkable achievements.

### The Library of Congress Collections Portal
----
This portal contains links to all of the available digital collections which can be filtered and sorted.

#### API View
-----
The collections portal when requested via the API is JSON list of collections 

### Specific Collections
------
Specific collections contain links to items within the collection which contain detailed information about the item.

#### API View
----
The specific collection when returned via the API is a JSON list of items within the collection. The items have detailed attributes (name, value pairs).

When viewed from the command line the information about the collection is harder to read via the command line, easier in Firefox and easiest on the website, but for a program the command line/programmatic access of the returned data would be most useful since the JSON can be parsed and relevant information extracted by the program.


### General Notes on Exploring JSON Files in Python
----
The following is some general notes on how one may explore a JSON file in python with only access to the standard library. It is by no means an exhaustive list.

**Understanding JSON Structure in Python**

JSON data is represented in Python as nested collections: primarily as dictionaries, lists, and strings. A full breakdown is shown below[^2]:

| JSON Type | Python Type | Description |
|---|---|---|
| Object | Dictionary | Unordered collection of key-value pairs. Keys are unique strings, and used to access values. |
| Array | List | Ordered collection of elements, allowing duplicates. Elements can be any type. |
| String | String | Textual data enclosed in quotes. |
| Number (int/real) | int/float | Integer or floating-point number. |
| true | True | Boolean value representing truth. |
| false | False | Boolean value representing falsity. |
| null | None | Special value representing nothingness. |


**Exploring a JSON File with Python**

1. **Import the `json` module:**

   ```python
   import json
   ```

2. **Load the JSON data:**

   - **From a file:** Use `json.load()` with the filename:

     ```python
     with open("your_file.json", "r") as f:
         data = json.load(f)
     ```

   - **From a string:** Use `json.loads()` with the string:

     ```python
     json_string = '{"key": "value"}'
     data = json.loads(json_string)
     ```

3. **Explore the data using Python constructs:**

   - **Access dictionary keys:**

   ```python
   data.keys() # Get top level keys
   data["key"] # Get values associated with specific key
   ```
   
   - **Iterate over lists:**

     ```python
     for item in data_list:
         print(item["key_you_want"])  # Replace with your desired key
     ```

     ```python
     for i in range(len(data_list)):
         print(i, data_list[i]["key_you_want"])  # Replace with your desired key
     ```

   - **Check data type:** `type(data_element)`
   - **Perform other Python operations** as needed.


**Key Points:**

- Use `data.keys()` to get top-level keys.
- Check nested structures using `type()` (e.g., `type(data)`) and access elements using keys or indices.
- Adapt the code to your specific JSON structure.
- Use conditional statements and logical operators for more complex exploration.

Remember that this is a general guide, and you might need to adjust it based on your specific JSON file and exploration goals.



[^1]: [Wright Brothers Negatives](https://www.loc.gov/collections/wright-brothers-negatives/about-this-collection/)
[^2]: [json - Encoders and Decoders](https://docs.python.org/3/library/json.html#encoders-and-decoders)
