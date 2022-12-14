GitHub repository on DEOHS GitHub account 

[https://github.com/deohs/HDW](https://github.com/deohs/HDW)

Cleaning practices

- R Markdown script
- Version control done through Git utilizing GitHub
- Naming conventions
    - functions: camel case (myFunctionWorks)
    - original RedCap variables: lowercase with “_” between words (my_variable)
    - new variables: lowercase with “_” between words (my_variable)
        - new logical variable: end in “01” (my_variable_01)
        - new categorical/factor variable: end in “fac” (my_variable_fact)
- Keep old variable in dataset and write over them with clean data if doing minor cleaning
    - minor cleaning includes:
        - changing missing to NA or the equivalent for dates
        - correctly spelling a value
        - making a categorical variable into an ordered factor variable
- Missing values
    - change all missing to NA (mostly should have been done in first cleaning script)
- Labeling- done through RedCap code, but Spanish needs to be removed
- Documentation
    - **original variable name**
    - **new variable(s) name(s)**, if any
    - any **important cleaning steps**
        - which values were changed to NA
        - which missing values were able to be filled
        - if the class of the variable was changed
    - any **values outside of an expected range** (ex: weight is 12) and what was done with them, typically these can be changed to NA unless there are variables around it that can be used to gather this variable
    - if there is an **unusual amount of missingness** after the variable is cleaned (the variables from the different forms are coalesced) make a note of this to disucss
    - **variable class**
- Example of how documentation should look for variables
    - Variables: allergies, allergies_v2, allergies_v3
    - Cleaning: convert to a factor and labeled with English only (using RedCap code)
    - Class: factor
- Update the data dictionary
    - add your initials to the data dictionary in the row that you cleaned
    - clean the variable’s data dictionary line
        - remove Spanish
        - remove unnecessary text (ex: <font>)
    - add new variables to the second sheet in the file

Resources for data cleaning and coding in R

1. [R for applied epidemiology and public health | The Epidemiologist R Handbook (epirhandbook.com)](https://epirhandbook.com/en/)
2. [Welcome | R for Data Science (had.co.nz)](https://r4ds.had.co.nz/index.html)
3. [The R Markdown Cheat Sheet - RStudio](https://www.rstudio.com/blog/the-r-markdown-cheat-sheet/)
4. RMarkdown [rmarkdown.pdf](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4041daa4-1094-4e19-9925-23f14fb92305/rmarkdown.pdf) 
