# What it does


The module generate_fuzzy is a flask application having different function to generate fuzzy names and fuzzy address for given value.

Usage
It is used to :
1.Generate json object containing fuzzy name for the name provided.
2.Generate json object with list of fuzzy names with the score for each name.
3.Generate json object containing fuzzy address for the provided address.
4.Generate json object with all possible fuzzy address along with its score.

`python3 generate_fuzzy.py`

Different routes
1./name/<name> : 
example:
route: /name/sara 
output:{ "matches": "sarah" },
       { "matches": "serra" }

- if not matching fuzzy word is found then output will be {"error": "no fuzzy words found"}


2./address/<address>
example:
route: /address/42 Fairhaven Commons Way  
output:{ "matches": "42 Fairhaven Commons waye" }
- If a fuzzy word is found for any of the word then string replaced with fuzzy word is sent.

route: /address/777 Brockton Avenue
output :{ "matches": "777 , Brockton Avenue" }
If no words in the address have fuzzy word the a comma is inserted randomly in between the address.

```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

~~The world is flat.~~

