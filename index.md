---
title       : EnAHRgie Projekt
subtitle    : EA European Academy
author      : Elham Rahmani
job         : Researcher
logo        : logoENA.png
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : solarized_light      # {tomorrow}     # 
widgets     : [mathjax, quiz, bootstrap, shiny, interactive]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
assets      : {assets: ../../assets}
ext_widgets : {rCharts: [libraries/nvd3]}
--- 

## Read-And-Delete

1. Edit YAML front matter
2. Write using R Markdown
3. Use an empty line followed by three dashes to separate slides!

---  

## Slide 2

publish_github(user = "EArahmani", repo = "git push git@github.com:EArahmani/ER-repo.git gh-pages")
https://elhamrahmani.shinyapps.io/Analyseraster_model2/

<iframe src = 'https://elhamrahmani.shinyapps.io/Analyseraster_model2/' height='600px'></iframe>

--- 

## Slide 3

<iframe src = 'file:///H:/RShiny/EnAHRgie/Hist_Wind/Wind.html' height='600px' width='1000x'></iframe>

--- 

## Interactive Chart


<div id = 'chart1' class = 'rChart nvd3'></div>
<script type='text/javascript'>
 $(document).ready(function(){
      drawchart1()
    });
    function drawchart1(){  
      var opts = {
 "dom": "chart1",
"width":    800,
"height":    400,
"x": "Hair",
"y": "Freq",
"group": "Eye",
"type": "multiBarChart",
"id": "chart1" 
},
        data = [
 {
 "Hair": "Black",
"Eye": "Brown",
"Sex": "Male",
"Freq":             32 
},
{
 "Hair": "Brown",
"Eye": "Brown",
"Sex": "Male",
"Freq":             53 
},
{
 "Hair": "Red",
"Eye": "Brown",
"Sex": "Male",
"Freq":             10 
},
{
 "Hair": "Blond",
"Eye": "Brown",
"Sex": "Male",
"Freq":              3 
},
{
 "Hair": "Black",
"Eye": "Blue",
"Sex": "Male",
"Freq":             11 
},
{
 "Hair": "Brown",
"Eye": "Blue",
"Sex": "Male",
"Freq":             50 
},
{
 "Hair": "Red",
"Eye": "Blue",
"Sex": "Male",
"Freq":             10 
},
{
 "Hair": "Blond",
"Eye": "Blue",
"Sex": "Male",
"Freq":             30 
},
{
 "Hair": "Black",
"Eye": "Hazel",
"Sex": "Male",
"Freq":             10 
},
{
 "Hair": "Brown",
"Eye": "Hazel",
"Sex": "Male",
"Freq":             25 
},
{
 "Hair": "Red",
"Eye": "Hazel",
"Sex": "Male",
"Freq":              7 
},
{
 "Hair": "Blond",
"Eye": "Hazel",
"Sex": "Male",
"Freq":              5 
},
{
 "Hair": "Black",
"Eye": "Green",
"Sex": "Male",
"Freq":              3 
},
{
 "Hair": "Brown",
"Eye": "Green",
"Sex": "Male",
"Freq":             15 
},
{
 "Hair": "Red",
"Eye": "Green",
"Sex": "Male",
"Freq":              7 
},
{
 "Hair": "Blond",
"Eye": "Green",
"Sex": "Male",
"Freq":              8 
} 
]
  
      if(!(opts.type==="pieChart" || opts.type==="sparklinePlus" || opts.type==="bulletChart")) {
        var data = d3.nest()
          .key(function(d){
            //return opts.group === undefined ? 'main' : d[opts.group]
            //instead of main would think a better default is opts.x
            return opts.group === undefined ? opts.y : d[opts.group];
          })
          .entries(data);
      }
      
      if (opts.disabled != undefined){
        data.map(function(d, i){
          d.disabled = opts.disabled[i]
        })
      }
      
      nv.addGraph(function() {
        var chart = nv.models[opts.type]()
          .width(opts.width)
          .height(opts.height)
          
        if (opts.type != "bulletChart"){
          chart
            .x(function(d) { return d[opts.x] })
            .y(function(d) { return d[opts.y] })
        }
          
         
        
          
        

        
        
        
      
       d3.select("#" + opts.id)
        .append('svg')
        .datum(data)
        .transition().duration(500)
        .call(chart);

       nv.utils.windowResize(chart.update);
       return chart;
      });
    };
</script>

---&interactive 

## Interactive Chart with Shiny Controls


```r
slidifyUI(
  sidebarPanel(
    selectInput('sex', 'Choose Sex', c('Male', 'Female')),
    selectInput('type', 'Choose Type',
     c('multiBarChart','multiBarHorizontalChart')           
   )
  ),
  mainPanel(
    tags$div(id = 'nvd3plot', class='shiny-html-output nvd3 rCharts')
  )
)
```

```
## <div class="row-fluid">
##   <div class="col-sm-4">
##     <form class="well">
##       <div class="form-group shiny-input-container">
##         <label class="control-label" for="sex">Choose Sex</label>
##         <div>
##           <select id="sex"><option value="Male" selected>Male</option>
## <option value="Female">Female</option></select>
##           <script type="application/json" data-for="sex" data-nonempty="">{}</script>
##         </div>
##       </div>
##       <div class="form-group shiny-input-container">
##         <label class="control-label" for="type">Choose Type</label>
##         <div>
##           <select id="type"><option value="multiBarChart" selected>multiBarChart</option>
## <option value="multiBarHorizontalChart">multiBarHorizontalChart</option></select>
##           <script type="application/json" data-for="type" data-nonempty="">{}</script>
##         </div>
##       </div>
##     </form>
##   </div>
##   <div class="col-sm-8">
##     <div id="nvd3plot" class="shiny-html-output nvd3 rCharts"></div>
##   </div>
## </div>
```

---

