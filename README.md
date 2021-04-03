# lysis_curve.py

This function generates automated lysis curves (OD curves) for bacteriophage research via plotly.
It can also split a spaghetti lineplot into up to 9 subplots.

# lysis_curve_pub.py

This variant generates automated OD curves with modifications with a more professional (less Plotly) styling more suitable for publication. Dynamic interaction with the plots is sometimes buggy due to an issue on Plotly's end.

### Running in Jupyter

First, make sure your x-axis (time) data is your **zeroth (first) column** (this script always plots the first column in the csv file as the x-axis). Next, make sure you save your data in the .csv file format. Finally, navigate to the directory containing your .csv file in Jupyter.
```python
import os
os.chdir('your_path_here')
```
Next, import the lysis_curve.py file or just copy/paste it into a jupyter cell and execute.
#### Generate basic plot
This basic plot is good for cases where you do not wish to visually group your data
```python
lysis_curve('yourcsvfile.csv')
```
#### Generate plot with subplots
Use the argument ```subplots=True``` to split your data into subplots.


#### Generate plot with grouping
This argument is useful if you wish to visually group your data by color. 
It automatically sets each line in each group the same color, 
but assigns them different markers.
*Does not work with subplots.*
Pass the argument to `group` as a list of strings, with each column in a group separated by vertical bars.
```python
lysis_curve('yourcsvfile.csv', group=['1', '2|3', '4|5', '6|7|8'])
```

#### Generate plot with custom title
Use the argument ```title='Your Custom Title Here'```
By default, the title will be taken from your csv file name - thus 'yourcsvfile' if 'yourcsvfile.csv' is passed.

#### Generate plot with annotations
Use the argument ```annotations=True``` and follow the prompts.

#### Pass custom colors
```python
lysis_curve('yourcsvfile.csv', colors=['red', 'blue', 'blah'])
```

#### Save as .png
Set the argument ```png=True``` and the function will generate a .png file of the graph in your current directory.

#### Save as .svg
Set the argument ```svg=True``` and the function will generate a .svg file of the graph in your current directory.
Requires Kaleido or Orca

### Save .png, .svg and legendless .svg
```save=True```
Saves three versions of the graph: (1) a .png version with a legend (2) a .svg version with a legend (3) a .svg version without a legend and square dimensions

### Dependencies

* Python 3.5+
* Pandas ```pip install pandas```
* Plotly ```pip install plotly```
* Requests ```pip install requests```
* Kaleido ```pip install kaleido``` (Kaleido is recommended over Orca according to Plotly)
