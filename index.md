---
title       : Cars MPG Predictors Presentation
subtitle    : 
author      : Neveen Mohamed
job         : Analysis and Data person
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


1. Overview of the shiny project
2. Overview of ui.R code
3. Overview of server.R code
4. Overview of output

--- .class #id &interactive

## Interactive R code
The project uses a select input to allow the user to select the predictor that needs to be researched. 

<div class="row-fluid">
  <div class="container-fluid">
    <div class="row">
      <div class="col-sm-12">
        <h1>Cars MPG Predictors</h1>
      </div>
    </div>
    <div class="row">
      <div class="col-sm-4">
        <form class="well">
          <div class="form-group shiny-input-container">
            <label class="control-label" for="carsParamID">Select Cars Param:</label>
            <div>
              <select id="carsParamID"><option value="hp" selected>Horse Power</option>
<option value="cyl">Cylinders</option>
<option value="gear">Gears</option></select>
              <script type="application/json" data-for="carsParamID" data-nonempty="">{}</script>
            </div>
          </div>
        </form>
      </div>
      <div class="col-sm-8"></div>
    </div>
  </div>
</div>

--- .class #id 
## ui.R code

The slidify App has two functions ui.R which is listed below:


```r
library(shiny)

shinyUI(pageWithSidebar(
    headerPanel("Cars MPG Predictors"),
    sidebarPanel(
         selectInput("carsParamID","Select Cars Param:",
                      c(
                        "Horse Power" = "hp",
                        "Cylinders" = "cyl",
                        "Gears" = "gear")),
         submitButton("Update Graph")
        ),
    mainPanel(
        plotOutput('newPlot')
        )
    ))
```

--- .class #id 
## server.R code

and server.R which is listed below:


```r
data(mtcars)
library("ggplot2")
```

```
## Warning: package 'ggplot2' was built under R version 3.1.3
```

```r
shinyServer(
    function(input , output){
        df <- data.frame(mpg=mtcars$mpg
                         ,cyl=as.factor(mtcars$cyl)
                         ,hp=mtcars$hp
                         ,gear=mtcars$gear
                         )
        p1 <- ggplot(df)+geom_point(aes(x=get(input$carsParamID),y=mpg)) 
        output$newPlot<-renderPlot(p1)
    }
    )
```



