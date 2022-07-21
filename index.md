<html><head>
    <title>Bokeh Example</title>
    <meta charset="iso-8859-1">
    <link rel="icon" type="image/x-icon" href="./favicon.png">
    <script type="text/javascript" src="https://cdn.bokeh.org/bokeh/release/bokeh-2.4.2.js"></script>
    <script type="text/javascript" src="https://cdn.bokeh.org/bokeh/release/bokeh-gl-2.4.2.min.js"></script>
    <script type="text/javascript" src="https://cdn.bokeh.org/bokeh/release/bokeh-widgets-2.4.2.min.js"></script>
    <script type="text/javascript" src="https://cdn.bokeh.org/bokeh/release/bokeh-tables-2.4.2.min.js"></script>
    <script type="text/javascript" src="https://cdn.bokeh.org/bokeh/release/bokeh-mathjax-2.4.2.min.js"></script>

    <script type="text/javascript">
        Bokeh.set_log_level("info");
    </script>
    <link rel="stylesheet" href="https://pyscript.net/alpha/pyscript.css" />
    <script defer src="https://pyscript.net/alpha/pyscript.js"></script>
    </head>
    
        <py-env>
- bokeh
        </py-env>
        <h1>Bokeh Example</h1>

    <body>
<header style = "height: 100px; width: 100%; background-color: #607D8B;" >
<h1 style=" color: #fff; text-align: center; padding-top: 25px; font-size: 30px;" > Header Section </h1>
</header>
<nav style = "background-color: #607d8b9c;" >
<ul>
<li> <a href = "#"> Navigation Link1 </a> </li>
<li> <a href = "#"> Navigation Link2 </a> </li>
<li> <a href = "#"> Navigation Link3 </a> </li>
</ul>
</nav>
<div class = "main">
<section>
<h2> Section Part </h2>
<div id="chart"></div>
<p> Some Text </p>
</section>
<article>
<h2> </h2>
<p> Some Detailed Text </p>
</article>
<aside>
<h2> Sidebar Part </h2>
<p>  </p>
</aside>
</div>
<details>
<summary> </summary>
<p></p>
</details>
<footer style = " height: 100px; background-color:#607D8B; width: 100%; text-align: center;">
<h3 style = " color: #fff; text-align: center; padding-top: 10px; font-size: 30px; " >Footer Section</h3>
<p></p>
</footer>



    <py-script>

import json 
import pyodide 
from js import Bokeh, console, JSON
from bokeh.embed import json_item
from bokeh.io import output_file, show
from bokeh.layouts import gridplot
from bokeh.plotting import figure

<!-- output_file("layout_grid.html") -->

x = list(range(100))
y0 = x
y1 = [190 - i for i in x]
y2 = [abs(i - 500) for i in x]

# create three plots
s1 = figure(background_fill_color="#fafafa")
s1.circle(x, y0, size=12, alpha=0.8, color="#53777a")

s2 = figure(background_fill_color="#fafafa")
s2.triangle(x, y1, size=12, alpha=0.8, color="#c02942")

s3 = figure(background_fill_color="#fafafa")
s3.square(x, y2, size=12, alpha=0.8, color="#d95b43")

# make a grid
grid = gridplot([[s1, s2], [None, s3]], width=600, height=900)

p_json = json.dumps(json_item(grid, "chart"))
Bokeh.embed.embed_item(JSON.parse(p_json))


    </py-script>

</body>
</html>
