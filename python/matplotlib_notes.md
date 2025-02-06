# Matplotlib

<aside>
💡

Learn from: [Grid Lines](https://www.w3schools.com/python/matplotlib_grid.asp#:~:text=Specify%20Which%20Grid%20Lines%20to%20Display)

</aside>

## Plotting

```python
import matplotlib.pyplot as plt
import numpy as np

xpoints = np.array([0, 6])
ypoints = np.array([0, 250])

plt.plot(xpoints, ypoints)
plt.show()
# Draws a line from point to point
```

### Plotting without line

```python
xpoints = np.array([0, 6])
ypoints = np.array([0, 250])

plt.plot(xpoints, ypoints, **'o'**)
plt.show()
```

### Multiple points

```python
xpoints = np.array([1, 2, 6, 8])
ypoints = np.array([3, 8, 1, 10])

plt.plot(xpoints, ypoints)
plt.show()
```

### Default X-points
- Default values are 0, 1, 2, 3…

```python
ypoints = np.array([3, 8, 1, 10])

plt.plot(ypoints)
plt.show()
```

## Markers
- Emphasize points

```python
ypoints = np.array([3, 8, 1, 10])

plt.plot(ypoints, marker = **'o'**)
```

`*` : Start

### Other markers


| 'o' | Circle |
| --- | --- |
| '*' | Star |
| '.' | Point |
| ',' | Pixel |
| 'x' | X |
| 'X' | X (filled) |
| '+' | Plus |
| 'P' | Plus (filled) |
| 's' | Square |
| 'D' | Diamond |
| 'd' | Diamond (thin) |
| 'p' | Pentagon |
| 'H' | Hexagon |
| 'h' | Hexagon |
| 'v' | Triangle Down |
| '^' | Triangle Up |
| '<' | Triangle Left |
| '>' | Triangle Right |
| '1' | Tri Down |
| '2' | Tri Up |
| '3' | Tri Left |
| '4' | Tri Right |
| '|' | Vline |
| '_' | Hline |
### Customize marker

```python
plt.plot(ypoints, marker = 'o', ms = 20, mec = 'r', mfc = 'g')
```

`ms` : Marker size

`mec` : Marker edge color

`mfc` : Marker face color

- Hexadecimal
    
    ```python
    plt.plot(ypoints, marker = 'o', ms = 20, mec = '#4CAF50', mfc = '#4CAF50')
    ```
    
- Supported color names: [W3Schools](https://www.w3schools.com/colors/colors_names.asp)
### Format strings

`marker|line|color`

```python
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([3, 8, 1, 10])

plt.plot(ypoints, 'o:r')
plt.show()
```

- Remove `:` for no line
- Lines
    
    
    | '-' | Solid line |
    | --- | --- |
    | ':' | Dotted line |
    | '--' | Dashed line |
    | '-.' | Dashed/dotted line |
- Colors
    
    
    | 'r' | Red |
    | --- | --- |
    | 'g' | Green |
    | 'b' | Blue |
    | 'c' | Cyan |
    | 'm' | Magenta |
    | 'y' | Yellow |
    | 'k' | Black |
    | 'w' | White |
## Line
### Line styles
- Use keyword argument `linestyle` or `ls`
    
    ```python
    plt.plot(ypoints, linestyle = 'dotted') # or just ':'
    ```
    

| 'solid' (default) | '-' |
| --- | --- |
| 'dotted' | ':' |
| 'dashed' | '--' |
| 'dashdot' | '-.' |
| 'None' | '' or ' ' |
### Line color
- Use `color` or `c`

```python
plt.plot(ypoints, color = 'r')
```

- Hexadecimal or HTML names also possible
### Line width
- Use `linewidth` or `lw`

```python
plt.plot(ypoints, linewidth = '20.5')
```

### Multiple lines

```python
y1 = np.array([3, 8, 1, 10])
y2 = np.array([6, 7, 2, 11])

plt.plot(y1)
plt.plot(y2)

plt.show()
```

- Add both x and y values
    
    ```python
    x1 = np.array([0, 1, 2, 3])
    y1 = np.array([3, 8, 1, 10])
    x2 = np.array([0, 1, 2, 3])
    y2 = np.array([6, 2, 7, 11])
    
    plt.plot(x1, y1, x2, y2)
    ```
    
    or
    
    ```python
    plt.plot(x1, y1)
    plt.plot(x2, y2)
    ```
    
## Labels

```python
x = np.array([80, 85, 90, 95, 100, 105, 110, 115, 120, 125])
y = np.array([240, 250, 260, 270, 280, 290, 300, 310, 320, 330])

plt.plot(x, y)

plt.xlabel('Average Pulse') # Label for x-axis
plt.ylabel('Calorie burnage') # Label for y-axis

plt.show()
```

### Title

```python
plt.title('Sports Watch Data') # Title of the graph
```

Position

```python
plt.title('Sports Watch Data', **loc='left'**)
```

### Font

```python
font1 = {'family':'serif', 'color':'blue', 'size':20}
font2 = {'family':'serif','color':'darkred','size':15}

plt.title('Sports Watch Data', **fontdict=font1**) 
plt.xlabel('Average Pulse', **fontdict=font2**)
```

## Grid lines

```python
plt.plot(x, y)

plt.grid()

plt.show()
```
