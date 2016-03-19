---
title       : Cars MPG Predictors Presentation
subtitle    : 
author      : Neveen Mohamed
job         : BI Analysis and Data Science specialist
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [shiny,bootstrap,interactive,htmlwidgets]       # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---
## Presentation Content

This presentation goes over the shiny project delivered in this class. The project uses 
mtcars data and allows an interactive selection of predictors from the dataset to relate with the MPG.

The presentation illustrates the use of interactive R code as follows:
*  ui.R uses check boxs to allow selecting from the indicator list.
*  The input selection is passed in the application to the server.R where is processes it.
*  A message is displayed if no predictors were passed to the server.
*  The output chart is displayed showing the relation between MPG and the predictors.


--- .class #id &interactive

## Selecting the predictors
The project uses a group of check boxes to allow the user to select the predictor(s) that need to be researched. 

Here is what the selections look like:

<!--html_preserve--><div id="params" class="form-group shiny-input-checkboxgroup shiny-input-container">
<label class="control-label" for="params">Parameters</label>
<div class="shiny-options-group">
<div class="checkbox">
<label>
<input type="checkbox" name="params" value="disp"/>
<span>disp Displacement (cu.in.)</span>
</label>
</div>
<div class="checkbox">
<label>
<input type="checkbox" name="params" value="hp"/>
<span>hp   Horse Power</span>
</label>
</div>
<div class="checkbox">
<label>
<input type="checkbox" name="params" value="drat"/>
<span>drat Rear axle ratio</span>
</label>
</div>
<div class="checkbox">
<label>
<input type="checkbox" name="params" value="wt"/>
<span>wt   Weight (lb/1000)</span>
</label>
</div>
<div class="checkbox">
<label>
<input type="checkbox" name="params" value="qsec"/>
<span>qsec 1/4 mile time</span>
</label>
</div>
<div class="checkbox">
<label>
<input type="checkbox" name="params" value="vs"/>
<span>vs   V/S</span>
</label>
</div>
<div class="checkbox">
<label>
<input type="checkbox" name="params" value="am"/>
<span>am   Transmission (0 = automatic, 1 = manual)</span>
</label>
</div>
<div class="checkbox">
<label>
<input type="checkbox" name="params" value="carb"/>
<span>carb Number of carburetors</span>
</label>
</div>
<div class="checkbox">
<label>
<input type="checkbox" name="params" value="gear"/>
<span>gear Number of forward gears</span>
</label>
</div>
</div>
</div><!--/html_preserve-->

--- .class #id 
### Input Validation and Output MPG versus predictors chart


The input from the selectors is sent to server.R which process the selections and displays a chart showing the relation between MPG and the selected predictor(s). googleVis package is used to construct the chart.
If no variables were selected a message is displayed in the output informing the user to make a selection.  

[1] "Check at least one parameter."
<!-- ScatterChart generated in R 3.1.2 by googleVis 0.5.10 package -->
<!-- Fri Mar 18 23:19:09 2016 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataScatterChartID251059e65908 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 21,
160,
110,
3.9,
2.62,
16.46,
0,
1,
4,
4 
],
[
 21,
160,
110,
3.9,
2.875,
17.02,
0,
1,
4,
4 
],
[
 22.8,
108,
93,
3.85,
2.32,
18.61,
1,
1,
1,
4 
],
[
 21.4,
258,
110,
3.08,
3.215,
19.44,
1,
0,
1,
3 
],
[
 18.7,
360,
175,
3.15,
3.44,
17.02,
0,
0,
2,
3 
],
[
 18.1,
225,
105,
2.76,
3.46,
20.22,
1,
0,
1,
3 
],
[
 14.3,
360,
245,
3.21,
3.57,
15.84,
0,
0,
4,
3 
],
[
 24.4,
146.7,
62,
3.69,
3.19,
20,
1,
0,
2,
4 
],
[
 22.8,
140.8,
95,
3.92,
3.15,
22.9,
1,
0,
2,
4 
],
[
 19.2,
167.6,
123,
3.92,
3.44,
18.3,
1,
0,
4,
4 
],
[
 17.8,
167.6,
123,
3.92,
3.44,
18.9,
1,
0,
4,
4 
],
[
 16.4,
275.8,
180,
3.07,
4.07,
17.4,
0,
0,
3,
3 
],
[
 17.3,
275.8,
180,
3.07,
3.73,
17.6,
0,
0,
3,
3 
],
[
 15.2,
275.8,
180,
3.07,
3.78,
18,
0,
0,
3,
3 
],
[
 10.4,
472,
205,
2.93,
5.25,
17.98,
0,
0,
4,
3 
],
[
 10.4,
460,
215,
3,
5.424,
17.82,
0,
0,
4,
3 
],
[
 14.7,
440,
230,
3.23,
5.345,
17.42,
0,
0,
4,
3 
],
[
 32.4,
78.7,
66,
4.08,
2.2,
19.47,
1,
1,
1,
4 
],
[
 30.4,
75.7,
52,
4.93,
1.615,
18.52,
1,
1,
2,
4 
],
[
 33.9,
71.1,
65,
4.22,
1.835,
19.9,
1,
1,
1,
4 
],
[
 21.5,
120.1,
97,
3.7,
2.465,
20.01,
1,
0,
1,
3 
],
[
 15.5,
318,
150,
2.76,
3.52,
16.87,
0,
0,
2,
3 
],
[
 15.2,
304,
150,
3.15,
3.435,
17.3,
0,
0,
2,
3 
],
[
 13.3,
350,
245,
3.73,
3.84,
15.41,
0,
0,
4,
3 
],
[
 19.2,
400,
175,
3.08,
3.845,
17.05,
0,
0,
2,
3 
],
[
 27.3,
79,
66,
4.08,
1.935,
18.9,
1,
1,
1,
4 
],
[
 26,
120.3,
91,
4.43,
2.14,
16.7,
0,
1,
2,
5 
],
[
 30.4,
95.1,
113,
3.77,
1.513,
16.9,
1,
1,
2,
5 
],
[
 15.8,
351,
264,
4.22,
3.17,
14.5,
0,
1,
4,
5 
],
[
 19.7,
145,
175,
3.62,
2.77,
15.5,
0,
1,
6,
5 
],
[
 15,
301,
335,
3.54,
3.57,
14.6,
0,
1,
8,
5 
],
[
 21.4,
121,
109,
4.11,
2.78,
18.6,
1,
1,
2,
4 
] 
];
data.addColumn('number','mpg');
data.addColumn('number','disp');
data.addColumn('number','hp');
data.addColumn('number','drat');
data.addColumn('number','wt');
data.addColumn('number','qsec');
data.addColumn('number','vs');
data.addColumn('number','am');
data.addColumn('number','carb');
data.addColumn('number','gear');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartScatterChartID251059e65908() {
var data = gvisDataScatterChartID251059e65908();
var options = {};
options["allowHtml"] = true;
options["width"] =    600;
options["height"] =    400;
options["trendlines"] = {0: { type: 'exponential'}};

    var chart = new google.visualization.ScatterChart(
    document.getElementById('ScatterChartID251059e65908')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartScatterChartID251059e65908);
})();
function displayChartScatterChartID251059e65908() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartScatterChartID251059e65908"></script>
 
<!-- divChart -->
  
<div id="ScatterChartID251059e65908" 
  style="width: 600; height: 400;">
</div>





