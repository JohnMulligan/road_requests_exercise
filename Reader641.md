# Wright Brothers Negatives Collection

![Reader641_1](/assets/Reader641_1.png)

[Wright Brothers Negatives Collection](https://www.loc.gov/collections/wright-brothers-negatives)

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

j_struct['results'][0]['aka']
j['results'][0]['aka']
