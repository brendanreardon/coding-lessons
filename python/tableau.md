[Matplotlib](https://matplotlib.org) is a plotting library for Python, known for its ability to produce publication quality figures but not so much for its default color schemes. [Tableau](https://www.tableau.com/), on the other hand, is known for both its beauty and steep fees. Wouldn't it be great to have the best of both worlds? 

You can! By DIYing your own figures and specifying your own colors. Let's use matplotlib with [Tableau10](https://www.tableau.com/about/blog/2016/7/colors-upgrade-tableau-10-56782). 

Matplotlib's color argument can interpret colors in [five different ways](https://matplotlib.org/gallery/color/color_demo.html#sphx-glr-gallery-color-color-demo-py) and for this demo we will pass colors as R,G,B tuples. 

The hex color's listed on Tableau's website for [Tableau10](https://www.tableau.com/about/blog/2016/7/colors-upgrade-tableau-10-56782) were converted to RBG values and then put into a list in Python. Try the following in a Jupyter notebook to define a list of R,G,B tuples for Tableau10 and then plot a scatter plot, 
```python
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline

tableau10 = [(78, 121, 167), (242, 142, 43), (225, 87, 89),
             (118, 183, 178), (89, 161, 79), (237, 201, 72),
             (176, 122, 161), (225, 157, 167), (156, 117, 95),
             (186, 176, 172)]

for i in range(len(tableau10)):
    r, g, b = tableau10[i]
    tableau10[i] = (r / 255., g / 255., b / 255.)

plt.scatter(np.random.rand(10), np.random.rand(10), color=tableau10[0])
plt.scatter(np.random.rand(10), np.random.rand(10), color=tableau10[1])
plt.scatter(np.random.rand(10), np.random.rand(10), color=tableau10[2])
plt.show()
```

We can also make this more intuitive by using a [dictionary](https://docs.python.org/3/tutorial/datastructures.html#dictionaries) to label R,G,B values by their color,
```python
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline

tableau10 = {
    'blue': (78, 121, 167), 'orange': (242, 142, 43), 'red': (225, 87, 89),
    'cyan': (118, 183, 178), 'green': (89, 161, 79), 'yellow': (237, 201, 72),
    'purple': (176, 122, 161), 'pink': (225, 157, 167), 'brown': (156, 117, 95),
    'grey': (186, 176, 172)}

for color in tableau10.keys():
    r, g, b = tableau10[color]
    tableau10[color] = (r / 255., g / 255., b / 255.)

plt.scatter(np.random.rand(10), np.random.rand(10), color=tableau10['blue'])
plt.scatter(np.random.rand(10), np.random.rand(10), color=tableau10['orange'])
plt.scatter(np.random.rand(10), np.random.rand(10), color=tableau10['red'])
plt.show()
```

Note: This is not as needed as much these days because [matplotlib v2.0.0](https://matplotlib.org/users/dflt_style_changes.html) updated their default styles to use the color10 palette used by Vega and d3, which Tableau developed. None the less, this is still useful to see how you can use custom color palettes with matplotlib.

Read more from the [official matplotlib documentation](https://matplotlib.org/index.html) and their [official tutorials](https://matplotlib.org/tutorials/index.html).

