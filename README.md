# Title
The module generate_fuzzy is a flask application having different function to generate fuzzy names and fuzzy address along with the score of each fuzzy name or address. User can enter maximum count and minimum score to get the desired result.

## Pre-requisite
Python version 3

[requirements](./requiremeny.txt)

## Build 
Command to run the tool 

`python3 generate_fuzzy.py`

## How to execute
It runs in port number:5000
Different routes present

1./score/name/<name>?max_count=&min_score=
In this route name is to be provided along with query parameters max_count(maximum number of fuzzy name) and min_score(minimum score of the fuzzy name).We can set min_score to zero to get all possible fuzzy names.

Example
- /score/name/john?max_count=3&min_score=50

  output : 
  ```
  {
  "john": [
    {
      "fuzzy_word": "jon", 
      "score": 86
    }, 
    {
      "fuzzy_word": "jonn", 
      "score": 75
    }
  ]
}
```
2./score/address/<address>?max_count=&min_score=
This route takes a address and returns all possible fuzzy address along with its score , it takes each word of the address and find fuzzy word and and replace it with the fuzzy word and if not word has a fuzzy word then it appends ',' at different postions.

Example
- /score//address/42 Fairhaven Commons Way?max_count=5&min_score=0 (when fuzzy word is found)

output :

```
{
  "42 Fairhaven Commons Way": [
    {
      "fuzzy_address": "42 Fairhaven Commons waye", 
      "score": 94
    }, 
    {
      "fuzzy_address": "42 Fairhaven Commons wey", 
      "score": 92
    }, 
    {
      "fuzzy_address": "42 Fairhaven Commons wei", 
      "score": 88
    }, 
    {
      "fuzzy_address": "42 Fairhaven Commons weigh", 
      "score": 84
    }
  ]
}
```
- /score//address/777 Brockton Avenue?max_count=5&min_score=0 (when fuzzy word is not found)

output :

```

  "777 Brockton Avenue": [
    {
      "fuzzy_address": "777 , Brockton Avenue", 
      "score": 0
    }, 
    {
      "fuzzy_address": "777 Brockton , Avenue", 
      "score": 0
    }
  ]
}

```
Since only ',' is added the so score will be zero.

