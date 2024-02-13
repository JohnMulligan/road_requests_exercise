# Wright Brothers Negatives Collection

![Reader641_1](/assets/Reader641_1.png)

[Wright Brothers Negatives Collection](https://www.loc.gov/collections/wright-brothers-negatives)

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
The Wright Brothers Negatives collection at the Library of Congress features an extensive selection of photographs documenting the early experiments and achievements in aviation by the Wright brothers. This collection provides a unique visual record of the Wright brothers' development of the airplane, their flights, and their experimentation from 1897 to 1928. It includes both glass negatives and photographic prints, offering a rare glimpse into the pioneering efforts that led to the first successful powered flights. This collection is a valuable resource for researchers, historians, and enthusiasts interested in the history of aviation and the remarkable contributions of the Wright brothers. For more detailed exploration, you can visit the collection on the Library of Congress website.

- Historical photographs documenting early aviation experiments.
- Visual records of the Wright Brothers' flight tests and aircraft.
- A mix of glass negatives and prints spanning from 1897 to 1928.
- Insightful glimpses into the innovation process of the Wright Brothers.

#### API View
-----
Exploring the collection in JSON format significantly differs from its web interface, lacking visual elements and relying on a text-heavy layout. This approach overwhelms with details, complicating the search for specific information amidst text and links. While it clarifies the data's structure, making it easier to understand its organization, engaging with JSON primarily benefits those aiming for an in-depth analysis of the data framework, as opposed to casual browsing. The specific collection when returned via the API is a JSON list of items within the collection. The items have detailed attributes (name, value pairs).When viewed from the command line the information about the collection is harder to read via the command line, easier in Firefox and easiest on the website, but for a program the command line/programmatic access of the returned data would be most useful since the JSON can be parsed and relevant information extracted by the program.

#### Request View
----
Software follows provided instructions precisely, leading to outcomes that can be either very efficient or problematic, based on how accurate those instructions are. Working with JSON in Python, or any language, requires knowledge of specific commands for targeted results. My journey through this was a blend of initial frustration due to the steep learning curve and eventual satisfaction upon gaining proficiency, highlighting the method's effectiveness for repetitive tasks, given the right expertise.

See the code used to access this collection below:

```phython
import requests
r=requests.get('https://www.loc.gov/collections/wright-brothers-negatives/?fo=json&at=results')
r.status_code
import json
j=json.loads(r.text)
print(json.dumps(j,indent=2))
print(j.keys())

def explore_json_structure(data, seen_values=None):
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
