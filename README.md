# rcloud.params
Notebook parameters for RCloud

This RCloud package allows notebook variables to be exposed as parameters,
both through query parameters and through UI elements.

Say that we want a variable `x` to be read from a query parameter or defaulted to 1.

Simply load the library, set the variable, and call `param` on it, and then call `submit`
to generate the submit button:

```{r}
library(rcloud.params)
x <- 1
numericInput(x)
submit()
```

rcloud.params will generate a labelled text input for the variable, display the default value,
and display a submit button and wait for it to be clicked.

If a value is specified as a query parameter, it will populate the variable instead of the
default value.

If there is no default, the text input will be empty and must be filled in before the submit
will be successful:

```{r}
library(rcloud.params)
textInput(y)
submit()
```

The variable will created during `submit`. A non-defaulted value can also be specified as
`NA` or assigned using the widget.

```{r}
library(rcloud.params)
textInput(y, value = "Hello World")
submit()
```

Multiple variables can be assigned using one submit() either by individually listing
or using the paramDiv() function to diaply with inline html

```{r}
library(rcloud.params)
library(htmltools)

paramDiv(h1("Start"), 
    textInput(x), 
    numericInput(y), 
    dateInput(theDate), 
    h1("End"), 
    byRow = TRUE
    )
submit()
```

