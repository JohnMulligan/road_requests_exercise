# My Interesting Discovery on "America at Work, America at Leisure"

## The Front End
The website has been designed with a simplistic but polished look to grant viewers the ease of navigating through its domain as well as the ease of consuming the data by their handy audio translator.The site utilizes both text, images, and audio to showcase highlights and key items from the collection, allowing for an engaging and educational experience.
Here is a link to the collection of "America at Work, America at Leisure": 
"https://www.loc.gov/collections/america-at-work-and-leisure-1894-to-1915/about-this-collection/"

### JSON Formatting
The "America at Work, America at Leisure: Motion Pictures from 1894 to 1915" Collection is located under "['results'],[24]" in the main collections view. However, navigating the JSON format contrasts sharply with the user-friendly web interface, lacking visual aids and presenting minimal text. This makes finding specific items challenging as users must sift through raw data and numerous textual elements. While the structure becomes clearer with time, interacting with the JSON format seems more suitable for those seeking a deeper understanding of data organization rather than casual exploration.

##### The Request format
Proficiency in utilizing JSON in Python, or any programming language, relies on understanding the requisite commands to accomplish particular objectives. My personal journey with this revealed a blend of frustration and gratification: frustration stemming from the initial learning curve, but satisfaction once mastery was attained, highlighting the efficiency it offers for repetitive tasks to those possessing the requisite skills. I accessed this format using Python Anywhere, and without the assistance and collaboration of my peers, learning how to access a specific collection would have been impossible.
Here is the code used to access this collection:


```Python
import requests
r=requests.get('https://www.loc.gov/collections/?fo=json&at=results')
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
j['results'][24]['aka']
[https://www.loc.gov/collections/america-at-work-and-leisure-1894-to-1915/]



