Lists are probably the most intuitive and simplest of all data structures but they are limited by being only indexable by a sequence of integers. Take the following example, in which bananas is the 0th item in the fruits list and apples are the 1st.

```
In [1]: fruits = ['bananas', 'apples']

In [2]: fruits[0], fruits[1]
Out[2]: ('bananas', 'apples')
```

It is possible to create a _nested list_, a list of lists, in Python, which may be useful when creating a grocery list. 

```
In [3]: fruits = ['bananas', 'apples']

In [4]: grains = ['bread']

In [5]: vegetables = ['broccoli', 'spinach']

In [6]: grocery_list = [fruits, grains, vegetables]; grocery_list
Out[6]: [['bananas', 'apples'], ['bread'], ['broccoli', 'spinach']]
```  

My fruits are now accesible by taking the 0th element of grocery list, grains the first, and vegetables the second. But this is unideal. What if I want to keep the information that broccoli and spinch are vegetables? To view my vegetables in this format, I would have to remember that vegetables were added as the last element in the nested list.  

Dictionaries solve this limitation by allowing indexing not only by integer but by any immutable type, which Python calls _keys_. Dictionaries should be thought of as a set of associated _key-value pairs_. A dictionary can be created with curly brackets, `{ }`, and indexed with hard brackets, `[ ]`. We can thus recreate our grocery list a dictionary to quickly access our needed grains,

```
In [7]: grocery_list = {'fruits': fruits, 'grains': grains, 'vegetables': vegetables} 

In [7]: grocery_list
Out[7]:
{'fruits': ['bananas', 'apples'],
 'grains': ['bread'],
 'vegetables': ['broccoli', 'spinach']}
```

Index values can be listed with `.keys()` and contents can be listed with `.values()`. 
```
In [8]: grocery_list.keys()
Out[8]: dict_keys(['fruits', 'grains', 'vegetables'])

In [9]: grocery_list.values()
Out[9]: dict_values([['bananas', 'apples'], ['bread'], ['broccoli', 'spinach']])
```

Like lists, dictionaries also support the ability to be nested for more complicated data structures. When would you need to create such a complicated data structure? Perhaps to catalog the color palettes of our generation's best director's movies? 

Let's make a nested dictionary of [Wes Anderson color palettes](http://www.anothermag.com/art-photography/3586/wes-andersons-colour-palettes). The following is a dictionary of colors of shots from [Moonrise Kingdom](https://www.rottentomatoes.com/m/moonrise_kingdom/) and [The Grand Budapest Hotel](https://www.rottentomatoes.com/m/the_grand_budapest_hotel),

```
In [10]: moonrise = {
   ...:     'blue': (122, 142, 135),
   ...:     'orange': (193, 125, 63),
   ...:     'white': (204, 196, 148),
   ...:     'black': (41, 33, 31)
   ...: }

In [11]: budapest = {
    ...:     'pink': (229, 161, 196),
    ...:     'purple': (198, 206, 246),
    ...:     'brown': (215, 164, 154),
    ...:     'blue': (115, 149, 210)
    ...: }
```

We'll then combine it into one larger dictionary, 

```
In [12]: wesanderson = {
    ...:     'moonrise-kingdom': moonrise,
    ...:     'budapest-hotel': budapest
    ...: }

In [13]: wesanderson
Out[13]:
{'budapest-hotel': {'blue': (115, 149, 210),
  'brown': (215, 164, 154),
  'pink': (229, 161, 196),
  'purple': (198, 206, 246)},
 'moonrise-kingdom': {'black': (41, 33, 31),
  'blue': (122, 142, 135),
  'orange': (193, 125, 63),
  'white': (204, 196, 148)}}

In [14]: wesanderson.keys()
Out[14]: dict_keys(['moonrise-kingdom', 'budapest-hotel'])

In [15]: wesanderson.values()
Out[15]: dict_values([{'blue': (122, 142, 135), 'orange': (193, 125, 63), 'white': (204, 196, 148), 
'black': (41, 33, 31)}, {'pink': (229, 161, 196), 'purple': (198, 206, 246), 'brown': (215, 164, 154), 
'blue': (115, 149, 210)}])

In [16]: wesanderson['budapest-hotel']
Out[16]:
{'blue': (115, 149, 210),
 'brown': (215, 164, 154),
 'pink': (229, 161, 196),
 'purple': (198, 206, 246)}
```

This dictionary can be constructed all at once and configured for use with [Matplotlib](https://matplotlib.org), 
```
moonrise = {'blue': (122, 142, 135), 'orange': (193, 125, 63), 'white': (204, 196, 148), 'black': (41, 33, 31)}
budapest = {'pink': (229, 161, 196), 'purple': (198, 206, 246), 'brown': (215, 164, 154), 'blue': (115, 149, 210)}

for color in moonrise.keys():
    r, g, b = moonrise[color]
    moonrise[color] = (r / 255., g / 255., b / 255.)
    
for color in budapest.keys():
    r, g, b = budapest[color]
    budapest[color] = (r / 255., g / 255., b / 255.)
    
wesanderson = {'moonrise-kingdom': moonrise, 'budapest-hotel': budapest}
```

Read more from the [official documentation](https://docs.python.org/3/tutorial/datastructures.html#dictionaries).

Bonus: The build-in application [Digital Color Meter](https://support.apple.com/guide/digital-color-meter/welcome/mac) on Apple computers lets you get RGB value for any color on your screen!
