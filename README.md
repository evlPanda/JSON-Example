# JSON-Example
Example of populating complex data type from JSON in PeopleCode

Credit to https://www.cedarhillsgroup.com/knowledge-base/kbarticles/JSON-parsing-using-peopleTools/ for the example.

Example JSON:

```
[
  {
    "name": "Meowsy",
    "species" : "cat",
    "canBark": false,
    "foods": {
      "likes": ["tuna", "catnip"],
      "dislikes": ["ham", "zucchini"]
    }
  },
  {
    "name": "Barky",
    "species" : "dog",
    "canBark": true,
    "foods": {
      "likes": ["bones", "carrots"],
      "dislikes": ["tuna"]
    }
  },
  {
    "name": "Purrpaws",
    "species" : "cat",
    "canBark": false,
    "foods": {
      "likes": ["mice"],
      "dislikes": ["cookies"]
    }
  }
]
```

The example code populates an Array of ```Animal```:

```
class Animal
   property string name;
   property string species;
   property boolean canBark;
   property string likesFoods;
   property string dislikesFoods;
end-class;

class Animals extends Array
   method Animals(&jsonString_ As string);
   method getByName(&name_ As string) Returns JSON_EXAMPLE:Animal;
```

example use:

```
Local JSON_EXAMPLE:Animals &Animals;
Local string &exampleJSON = GetHTMLText(HTML.EXAMPLE_JSON);
&Animals = create JSON_EXAMPLE:Animals(&exampleJSON);
```

See more examples in unit test.
