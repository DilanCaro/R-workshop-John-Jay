# Part IV: Interactive Dashboards with Shiny (30 minutes) {-}
## Introduction to Shiny for building web-based data dashboards {-}

Shiny is an R package that makes it easy to build interactive web applications (apps) straight from R. It allows you to turn analyses into interactive web applications without requiring HTML, CSS, or JavaScript knowledge.


```r
# Load the Shiny package
#install.packages("shiny")
library(shiny)
```

The basic structure of a Shiny app involves two main parts:

1. A user interface (UI) script, which controls the layout and appearance of the app.
2. A server script, which contains the instructions to build and rebuild the app based on user input.


## Creating a simple Shiny app {-}

*UI Component:* The UI has a sliderInput for selecting the mpg range and a tableOutput to display the filtered data.

*Server Logic:* The reactive function creates a reactive subset of mtcars based on the selected mpg range. The renderTable function then renders this filtered data as a table in the main panel.

*Running the App:* As with any Shiny app, shinyApp(ui = ui, server = server) runs the app.


```r

# Example: A simple Shiny app for displaying a plot

# Define UI
ui <- fluidPage(
  titlePanel("Simple Shiny App"),
  sidebarLayout(
    sidebarPanel(
      sliderInput("num", "Number of bins:", 
                  min = 1, max = 50, value = 30)
    ),
    mainPanel(
       plotOutput("distPlot")
    )
  )
)

# Define server logic
server <- function(input, output) {
  output$distPlot <- renderPlot({
    x <- faithful$eruptions
    bins <- seq(min(x), max(x), length.out = input$num + 1)
    hist(x, breaks = bins, col = 'darkgray', border = 'white')
  })
}

# Run the application 
shinyApp(ui = ui, server = server)
```


```{=html}
<div style="width: 100% ; height: 400px ; text-align: center; box-sizing: border-box; -moz-box-sizing: border-box; -webkit-box-sizing: border-box;" class="muted well">Shiny applications not supported in static R Markdown documents</div>
```



```r

# Define UI
ui <- fluidPage(
  titlePanel("Data Filtering App"),
  sidebarLayout(
    sidebarPanel(
      sliderInput("mpgRange", "Miles per Gallon (mpg):",
                  min = min(mtcars$mpg), max = max(mtcars$mpg),
                  value = c(min(mtcars$mpg), max(mtcars$mpg))
      )
    ),
    mainPanel(
      tableOutput("filteredData")
    )
  )
)

# Define server logic
server <- function(input, output) {
  filteredData <- reactive({
    mtcars[mtcars$mpg >= input$mpgRange[1] & mtcars$mpg <= input$mpgRange[2], ]
  })

  output$filteredData <- renderTable({
    filteredData()
  })
}

# Run the application 
shinyApp(ui = ui, server = server)
```


```{=html}
<div style="width: 100% ; height: 400px ; text-align: center; box-sizing: border-box; -moz-box-sizing: border-box; -webkit-box-sizing: border-box;" class="muted well">Shiny applications not supported in static R Markdown documents</div>
```


*Exercise*:

1. Modify the example Shiny app to include a dataset of your choice and create a different type of plot.

2. Add additional input options, like checkboxes or dropdown menus, to manipulate the plot.
